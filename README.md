# Super Field - JSON

A specialized JSON input component for Budibase applications with syntax validation, formatting options, and flexible input modes.

## 🚀 Features

### JSON Input

- **JSON Field Type**: Dedicated JSON field with type validation
- **Syntax Validation**: Automatic JSON format validation
- **Flexible Input**: Single line or multi-line textarea modes
- **Default Values**: Pre-populated JSON objects or arrays
- **Auto-formatting**: JSON structure validation and formatting

### Input Modes

- **Single Line**: Compact JSON input for simple objects
- **Multi-line**: Textarea for complex JSON structures
- **Icon Support**: Visual indicators for single-line mode
- **Placeholder Text**: Guidance for JSON structure expectations

### Validation & Control

- **JSON Validation**: Ensures valid JSON syntax
- **String Validation**: Additional validation rules
- **Event Handling**: On change events with JSON context
- **State Management**: Disabled and readonly modes

### User Experience

- **Syntax Highlighting**: Clear JSON structure visualization
- **Error Feedback**: Real-time validation feedback
- **Auto-focus**: Automatic input focus for data entry
- **Debounced Input**: Performance optimization for large JSON
- **Help Text**: Guidance for expected JSON structure

### Advanced Features

- **Conditional Logic**: Dynamic behavior based on JSON content
- **Template Support**: Default JSON structure templates
- **Accessibility**: Keyboard navigation and screen reader support
- **Performance**: Efficient handling of large JSON objects

### Styling & Layout

- **Flexible Positioning**: Label placement options
- **Field Modes**: Form input or inline editing
- **Size Configuration**: Adjustable component width
- **Theme Integration**: Consistent with Budibase design

## 📝 Usage Instructions

### Basic Setup

1. Add the Super Field - JSON component to your form
2. Bind to a JSON field in your data source
3. Choose single-line or multi-line input mode
4. Configure validation and help text

### Advanced Configuration

- **Input Mode**: Select based on expected JSON complexity
- **Validation**: Set JSON format requirements
- **Templates**: Provide default JSON structure examples
- **Events**: Attach actions to JSON value changes

### Common Use Cases

- **Configuration Objects**: Application settings and preferences
- **API Payloads**: JSON data for API integrations
- **Metadata Storage**: Structured metadata and properties
- **Complex Forms**: Multi-field data as JSON objects
- **Data Import/Export**: JSON data handling

## 🔧 Configuration Options

| Setting        | Type    | Description                         |
| -------------- | ------- | ----------------------------------- |
| Field          | JSON    | JSON field binding                  |
| Label          | String  | Display label text                  |
| Placeholder    | String  | Input guidance text                 |
| Default Value  | JSON    | Pre-populated JSON value            |
| Help Text      | String  | Help/instruction text               |
| Validation     | Rules   | JSON format validation              |
| Control Type   | Select  | Single line or multi-line mode      |
| Autofocus      | Boolean | Auto-focus on load                  |
| Debounced      | Boolean | Enable input debouncing             |
| Disabled       | Boolean | Disable JSON input                  |
| Read Only      | Boolean | Read-only mode                      |
| Icon           | Icon    | Visual indicator (single-line only) |
| Field Mode     | Select  | Form or inline input style          |
| Label Position | Select  | Label placement                     |
| Size           | Number  | Component width span                |

## 📋 Events

### On Change

Triggered when the JSON value changes.

**Context:**

- `value`: The current JSON value
- `field`: The bound field information

## 🎨 Styling

Supports Budibase's styling system with:

- **JSON Formatting**: Clear structure visualization
- **Error Highlighting**: Validation error display
- **Theme Consistency**: Matches application design
- **Custom CSS**: Advanced styling options

## 🔍 Best Practices

- Use multi-line mode for complex JSON structures
- Provide example JSON in help text or placeholders
- Implement validation for required JSON fields
- Consider debouncing for real-time JSON editing
- Test JSON parsing and validation thoroughly
- Use single-line for simple key-value pairs
