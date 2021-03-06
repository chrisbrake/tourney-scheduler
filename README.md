# tourney-scheduler

A scheduling app intended for tournaments.

## Keeper

Record games into the system, (including competitor specific actions)

## Competitor

Can easily see their own schedule.

## Organizer

Decide on venus and schedule

## Round

The parent of Organizer, Competitor, and Keeper

## Event

All other objects are children of the Event.

## Schema

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {},
  
  "definitions": {
    "Event" :{
        "type": "object",
        "properties": {
            "id": { "type": "string", "example": "1" },
            "name": { "type": "string", "example": "Tournament of Champions" },
            "rounds": { "type": "array", "items": { "$ref": "#/definitions/Round" }, "default": [] }
        },
    },
    "Round": {
        "type": "object",
        "properties": {
            "id": { "type": "string", "example": "1" },
            "name": { "type": "string", "example": "Ambition" },
            "location": { "type": "string", "example": "Room 1" },
            "keepers": { "type": "array", "items": { "$ref": "#/definitions/Keeper" }, "default": [] },
            "competitors": { "type": "array", "items": { "$ref": "#/definitions/Competitor" }, "default": [] },
            "organizers": { "type": "array", "items": { "$ref": "#/definitions/Organizer" }, "default": [] },
            "teams": { "type": "array", "items": { "$ref": "#/definitions/Team" }, "default": [] },

        }
    },
    "Team": {
        "type": "object",
        "properties": {
            "type": "object",
            "id": { "type": "string", "example": "1" },
            "name": { "type": "string", "example": "Win Machines" },
            "competitors": { "type": "array", "items": { "$ref": "#/definitions/Competitor" }, "default": [] },
            "event": { "$ref": "#/definitions/Event" },
        }
    },
    "Keeper": {
        "type": "object",
        "properties": {
            "type": "object",
            "id": { "type": "string", "example": "1" },
            "name": { "type": "string", "example": "John" },
            "event": { "$ref": "#/definitions/Event" },
        }
    },
    "Competitor": {
        "type": "object",
        "properties": {
            "type": "object",
            "id": { "type": "string", "example": "1" },
            "name": { "type": "string", "example": "Jane" },
            "event": { "$ref": "#/definitions/Event" },
            "team": { "$ref": "#/definitions/Team" },
        }
    },
    "Organizer": {
        "type": "object",
        "properties": {
            "type": "object",
            "id": { "type": "string", "example": "1" },
            "name": { "type": "string", "example": "Jude" },
            "event": { "$ref": "#/definitions/Event" },
        }
    }
  }
}
```
