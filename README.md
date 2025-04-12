# World Geo Data

Simplified geographical data for 172 countries in lightweight formats:
- TypeScript (`countries.ts`): 241 KB
- JSON (`countries.json`): 248 KB

## Data Source

Original data from [world.geo.json](https://github.com/johan/world.geo.json) with these modifications:

   - Converted from 3-letter to 2-letter country codes (ISO 3166-1 alpha-2)
   - Added capital city names and coordinates
   - Included continent information

## Data Structure

- **Country Codes**: ISO 3166-1 alpha-2 (2-letter) codes
- **Basic Info**: Country name, capital city, continent
- **Coordinates**: Capital city latitude/longitude
- **Geometry**: Simplified GeoJSON Polygon/MultiPolygon boundaries

```typescript
export type Country = {
  id: string; // ISO 3166-1 alpha-2 code
  country: string; // Country name
  capital: string; // Capital city name
  continent: string; // Continent name
  capitalCoordinates: Coordinates; // Capital coordinates
  countryGeometry: CountryGeometry; // Simplified country boundary
};

export type Coordinates = {
  lat: number;
  lng: number;
};

export type CountryGeometry = Polygon | MultiPolygon;

export type Polygon = {
  type: 'Polygon';
  coordinates: number[][][];
};

export type MultiPolygon = {
  type: 'MultiPolygon';
  coordinates: number[][][][];
};
```
