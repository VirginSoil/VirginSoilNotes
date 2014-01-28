# Database Associations

## User
- Id - int
- Email (required) - string
- Phone number (optional) - string

Has many Gardens
Has one Address

## Garden
- User Id - int
- Zone - string
- Notifications - string - in [:email, :phone, :text]
- Width (?)
- Depth (?)

Belongs to User
Has many Beds

## Bed
- Garden Id - int
- Width - int
- Depth - int

Belongs to Garden
Has many Plantings

## Plant
- Name - string (required)
- Description - text
- DaysToHarvest - int
- Width - int
- Height - int
- Season - string - in [:warm, :cool]
- WaterNeeds - string - in [:light, :medium, :heavy]

Has many Plantings

## Planting
- Bed Id - int
- Plant Id - int
- PlantingDate - time
- EstimatedHarvestDate - time
- Harvested - bool (required)

Joins Plants and Beds

## Resource
- Name - string
- Description - text
- Address Id - int

Has one Address

## Address
- StreetAddress - string
- City - string
- State - string - length in 2 chars
- Zipcode - string - length in 5 chars (cleanup in model)
- PhoneNumber - string - length in 10 chars (cleanup in model)
- Website - string

Belongs to Resource or User (polymorphic)
