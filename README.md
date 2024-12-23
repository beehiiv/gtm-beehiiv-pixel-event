# beehiiv Event Tag for Google Tag Manager

## Overview
The beehiiv Event Tag is a custom Google Tag Manager template that enables easy integration with beehiiv's Ad Network pixel tracking. This template allows you to track various conversion events and user actions on your website.

## Prerequisites
- Google Tag Manager account
- beehiiv Ad Network pixel base code implemented on your website
- beehiiv advertiser account

## Installation

1. Open your Google Tag Manager container
2. Go to Templates > Tag Templates
3. Click "New"
4. Click the three dots menu and select "Import"
5. Upload the template file
6. Save the template

## Base Pixel Implementation
Before using this event tag, ensure you have implemented the base beehiiv pixel code in your container:

```html
<script>bhpx("track", "[event name]", { data: { num_items: 1, currency: "usd", value_cents: 299 } });</script>
```

## Supported Events

| Event Type | Description | Required Parameters | Optional Parameters |
|------------|-------------|-------------------|-------------------|
| conversion | Custom conversion event | currency, value_cents | num_items, predicted_ltv_cents |
| lead | Sign up completion | currency, value_cents | - |
| complete_registration | Registration form completion | currency, value_cents | - |
| purchase | Purchase or checkout completion | currency, value_cents | num_items |
| initiate_checkout | Checkout flow initiation | currency, value_cents | num_items |
| start_trial | Free trial start | currency, value_cents | predicted_ltv_cents |
| subscribe | Subscription start | currency, value_cents | - |

## Parameters

### Event Settings
- **Event Name**: Select the type of event you want to track

### Monetary Values
- **Currency**: Three-letter currency code (e.g., "usd", "eur")
- **Value**: The value in cents (e.g., $1.99 = 199)

### Additional Parameters
- **Number of Items**: Available for purchase, initiate_checkout, and conversion events
- **Predicted LTV**: Available for start_trial and conversion events (in cents)

### Content Parameters (Optional)
- Content Category
- Content IDs
- Content Name
- Content Type
- Search String
- Status

## Usage Examples

### Track a Purchase
```javascript
{
  "eventName": "purchase",
  "currency": "usd",
  "value_cents": 1999,
  "num_items": 2
}
```

### Track a Trial Start
```javascript
{
  "eventName": "start_trial",
  "currency": "usd",
  "value_cents": 0,
  "predicted_ltv_cents": 29900
}
```

### Track a Lead
```javascript
{
  "eventName": "lead",
  "currency": "usd",
  "value_cents": 1000
}
```

## Troubleshooting

1. **Pixel Not Found Error**
   - Ensure the base beehiiv pixel code is implemented on your website
   - Verify the pixel loads before any event tags fire

2. **Invalid Event Name**
   - Check that you've selected a valid event name from the dropdown
   - Verify the event name matches the supported events list

3. **Missing Required Parameters**
   - Ensure all required parameters for your selected event are filled out
   - Check that monetary values are provided in cents

## Data Validation

The template includes built-in validation for:
- Required event name selection
- Valid currency code format (3 letters)
- Numeric values for monetary amounts and quantities
- Required parameters based on event type

## Support
For implementation support, please contact beehiiv support or consult the [beehiiv developer documentation](https://developer.beehiiv.com).
