<script>
  import { getContext, onDestroy } from "svelte";
  import { CellJSON, SuperField } from "@poirazis/supercomponents-shared";

  const { styleable, Provider, builderStore } = getContext("sdk");
  const component = getContext("component");
  const allContext = getContext("context");

  const formContext = getContext("form");
  const formStepContext = getContext("form-step");
  const groupLabelPosition = getContext("field-group");
  const labelWidth = getContext("field-group-label-width");
  const groupColumns = getContext("field-group-columns");
  const groupDisabled = getContext("field-group-disabled");
  const formApi = formContext?.formApi;

  export let field = "Super Text JSON";
  export let label;
  export let span = 6;
  export let placeholder;
  export let defaultValue;
  export let template;
  export let disabled;
  export let readonly;
  export let validation;
  export let invisible = false;
  export let helpText;
  export let align;
  export let controlType;

  export let onChange;
  export let debounced;
  export let debounceDelay;
  export let autofocus;

  export let icon;

  export let role = "formInput";
  export let labelPosition = "fieldGroup";
  export let showDirty;

  let formField;
  let formStep;
  let fieldState;
  let fieldApi;
  let fieldSchema;
  let value = defaultValue;

  $: formStep = formStepContext ? $formStepContext || 1 : 1;
  $: labelPos =
    groupLabelPosition && labelPosition == "fieldGroup"
      ? groupLabelPosition
      : labelPosition;

  $: formField = formApi?.registerField(
    field,
    "string",
    defaultValue,
    disabled,
    readonly,
    validation,
    formStep
  );

  $: unsubscribe = formField?.subscribe((value) => {
    fieldState = value?.fieldState;
    fieldApi = value?.fieldApi;
    fieldSchema = value?.fieldSchema;
  });

  $: value = fieldState?.value ? fieldState.value : defaultValue;
  $: error = fieldState?.error;

  $: cellOptions = {
    placeholder: placeholder || field,
    defaultValue,
    disabled: disabled || groupDisabled || fieldState?.disabled,
    template,
    readonly: readonly || fieldState?.readonly,
    icon,
    debounce: debounced ? debounceDelay : false,
    align,
    error: fieldState?.error,
    role,
    showDirty,
    multiline: controlType == "multiline",
  };

  $: $component.styles = {
    ...$component.styles,
    normal: {
      ...$component.styles.normal,
      display:
        invisible && !$builderStore.inBuilder
          ? "none"
          : $component.styles.normal.display,
      opacity: invisible && $builderStore.inBuilder ? 0.6 : 1,
      "grid-column": groupColumns ? `span ${span}` : "span 1",
    },
  };

  const handleChange = async (newValue) => {
    value = newValue;
    fieldApi?.setValue(newValue);
    await onChange?.({ value: newValue });
  };

  onDestroy(() => {
    fieldApi?.deregister();
    unsubscribe?.();
  });
</script>

<!-- svelte-ignore a11y-click-events-have-key-events -->
<!-- svelte-ignore a11y-no-noninteractive-tabindex -->
<!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
<!-- svelte-ignore a11y-no-static-element-interactions -->
<div use:styleable={$component.styles}>
  <Provider data={{ value }} />
  <SuperField {labelPos} {labelWidth} {field} {label} {error} {helpText}>
    <CellJSON
      {cellOptions}
      {value}
      {fieldSchema}
      {autofocus}
      on:change={(e) => handleChange(e.detail)}
    />
  </SuperField>
</div>
