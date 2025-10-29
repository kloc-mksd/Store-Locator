# Store Locator Section

A Shopify Liquid theme section that displays an interactive store locator with Google Maps integration, search functionality, and route directions.

## Features

- **Interactive Map**: Displays store locations on a Google Maps interface
- **Store Search**: Search stores by city, postal code, name, address, phone, or state
- **Store List**: Sidebar list of stores with address, phone, and directions button
- **Route Directions**: Click on a store to see directions from your current location using Google Routes API
- **Responsive Design**: Adapts to mobile and desktop layouts
- **Geolocation**: Automatically centers map on user's current location (if permitted)
- **Customizable**: Extensive settings for headings, labels, and default map position

## Installation

1. Copy the `store-locator.liquid` file to your theme's `sections/` directory
2. In the Shopify theme editor, add the "Store locator" section to your desired page

## Configuration

### Section Settings

#### General Settings
- **Heading**: Main heading text (default: "Locate a store")
- **Intro text**: Optional introductory text displayed below the heading
- **Enable search**: Toggle search functionality (default: enabled)
- **Search placeholder**: Placeholder text for the search input (default: "Search by city or pin...")
- **Directions button label**: Text for the directions button (default: "Get directions")

#### API Settings
- **Google Maps API key**: Required for map display. Get your key from [Google Cloud Console](https://console.cloud.google.com/)
- **Google Routes API key**: Optional. Uses Maps API key if left blank. Required for route directions feature
- **Default latitude**: Fallback latitude when stores don't have coordinates (default: India center)
- **Default longitude**: Fallback longitude when stores don't have coordinates (default: India center)

### Store Block Settings

Each store block includes the following fields:

- **Store name**: Name of the store
- **Address**: Full street address
- **City**: City name
- **State / Province**: State or province name
- **Postal / ZIP code**: Postal or ZIP code
- **Phone number**: Contact phone number (clickable `tel:` link)
- **Latitude**: Geographic latitude coordinate
- **Longitude**: Geographic longitude coordinate
- **Custom map link**: Optional custom directions URL (overrides default Google Maps link)

## Google Maps API Setup

### Required APIs

1. **Maps JavaScript API**: Required for displaying the map
2. **Routes API**: Required for route directions feature (optional but recommended)

### Setup Steps

1. Go to [Google Cloud Console](https://console.cloud.google.com/)
2. Create a new project or select an existing one
3. Enable the following APIs:
   - Maps JavaScript API
   - Routes API (for directions)
4. Create credentials (API Key)
5. Restrict the API key to your domain for security
6. Add the API key to the section settings

### API Key Restrictions

For production, configure API key restrictions:
- **Application restrictions**: HTTP referrers (websites)
- **API restrictions**: Restrict to Maps JavaScript API and Routes API only

## Usage

### Adding Stores

1. In the theme editor, click on the Store locator section
2. Click "Add block" → "Store"
3. Fill in the store details:
   - Store name
   - Address information
   - Phone number
   - Latitude and longitude (required for map display)
4. Repeat for additional stores

### Finding Coordinates

To get latitude and longitude coordinates:
1. Open Google Maps
2. Search for the store address
3. Right-click on the exact location
4. Select the coordinates from the popup menu
5. Copy latitude and longitude values

Alternatively, use a geocoding service or Google Maps Geocoding API.

### Custom Map Links

If a store has a custom map link (e.g., Apple Maps, Bing Maps, or a specific Google Maps URL), enter it in the "Custom map link" field. This will override the default Google Maps link generated from coordinates.

## Technical Details

### Dependencies

- Google Maps JavaScript API v3
- Google Maps Geometry Library
- Google Routes API v2 (for directions)

### Browser Support

- Modern browsers with JavaScript enabled
- Geolocation API support (optional, for automatic location detection)

### Search Functionality

The search feature filters stores based on:
- Store name
- Address
- City
- State
- Postal code
- Phone number

Search is case-insensitive and supports partial matches.

### Route Directions

When a user clicks on a store card or marker:
1. The map centers on the selected store
2. If user location is available, a route is automatically drawn
3. The route uses Google Routes API with traffic-aware routing
4. The map automatically adjusts to show the full route

## Styling

The section includes inline styles scoped to the section ID. You can customize the appearance by:

1. Modifying the `<style>` block in the Liquid file
2. Adding custom CSS to your theme's stylesheet
3. Targeting section-specific classes prefixed with `#StoreLocator-{{ section.id }}`

### Key CSS Classes

- `.store-locator`: Main container (grid layout)
- `.store-locator__search`: Search section container
- `.store-list`: Store list container
- `.store-card`: Individual store card
- `.store-map`: Map container
- `.get-dir`: Directions button

## Mobile Responsiveness

On screens smaller than 768px:
- Layout switches from grid to single column
- Map appears above the store list
- Full-width display for better mobile experience

## Troubleshooting

### Map Not Displaying
- Verify Google Maps API key is correct
- Check API key restrictions allow your domain
- Ensure Maps JavaScript API is enabled in Google Cloud Console
- Check browser console for error messages

### Routes Not Working
- Verify Routes API is enabled
- Check Routes API key (or verify Maps API key has Routes API access)
- Ensure API key has proper permissions
- Check browser console for API errors

### Stores Not Appearing
- Verify stores have valid latitude and longitude values
- Check that store blocks are added and saved
- Ensure search filters aren't hiding stores
- Check browser console for JavaScript errors

### Coordinates Not Valid
- Ensure latitude is between -90 and 90
- Ensure longitude is between -180 and 180
- Use decimal format (e.g., `12.969807` not `12°58'11"`)

## License

This section is provided as-is for use in Shopify themes.

