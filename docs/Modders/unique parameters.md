This page contains an overview of all different parameters used in uniques and what values can be filled into them.
Each of the different parameter types is described below, including all possible values for them.
These are split into two categories: 
- descriptions: e.g., "the name of any unit"
- `Text that looks like this`. This last one must be used exactly the same
Note that all of these are case-sensitive!


## action
An action that a unit can preform. Currently, there are only two actions part of this:
- `Spread Religion`
- `Remove Foreign religions from your own cities`


## amount
This indicates a whole number, possibly with a + or - sign, such as `2`, `+13`, or `-3`.


## baseTerrain
The name of any terrain that is a base terrain according to the json file.


## baseUnitFilter
Unit filters can be divided up into two parts: `baseUnitFilter`s and `mapUnitFilter`s. 
The former is tested against the unit as it appears in the json. 
This means it doesn't have an owning civ or tile it stands on, just its base properties. 
The latter is tested against the unit as it appears on the map, including its nation, tile, health and all other properties.

The following are allowed to be used:
- unit name
- unit type - e.g. Melee, Ranged, WaterSubmarine, etc.
- `Land`, `Water`, `Air`
- `land units`, `water units`, `air units`
- `non-air` for non-air non-missile units
- `Military`, `military units`
- `Civilian`, `civilian units`
- `All`
- `Melee`
- `Ranged`
- `Nuclear Weapon`
- `Great Person`, `Great`
- `Embarked`
- Any exact unique the unit has
- Any exact unique the unit type has
- Any combination of the above (will match only if all match). The format is `{filter1} {filter2}` and can match any number of filters. For example: `[{Military} {Water}]` units, `[{non-air} {Armor}]` units, etc. No space or other text is allowed between the `[` and the first `{`.


## belief
The name of any belief


## beliefType
`Pantheon`, `Follower`, `Founder` or `Enhancer`.


## buildingFilter
Allows to only activate a unique for certain buildings. Allowed options are:

- `All`
- `Buildings`, `Building`
- `Wonders`, `Wonders`
- `National Wonder`
- `World Wonder` -- All wonders that are not national wonders
- building name
- The name of the building it replaces (so for example uniques for libraries will apply to paper makers as well)
- an exact unique the building has (e.g.: `spaceship part`)
- `Culture`, `Gold`, etc. if the building is `stat-related` for that stat. Stat-related buildings are defined as one of the following:
  - Provides that stat directly (e.g. +1 Culture)
  - Provides a percentage bonus for that stat (e.g. +10% Production)
  - Provides that stat as a bonus for resources (e.g. +1 Food from every Wheat)
  - Provides that stat per some amount of population (e.g. +1 Science for every 2 population [cityFilter])


## buildingName
The name of any one building


## cityFilter
cityFilters allow us to choose the range of cities affected by this unique:

- `in this city`
- `in all cities`
- `in other cities`
- `in all coastal cities`
- `in capital`
- `in all non-occupied cities` - all cities that are not puppets and don't have extra unhappiness from being recently conquered
- `in all cities with a world wonder`
- `in all cities connected to capital`
- `in all cities with a garrison`
- `in non-enemy foreign cities` - In all cities owned by civs other than you that you are not at war with
- `in foreign cities`
- `in annexed cities`
- `in holy cities`
- `in City-State cities`
- `in cities following this religion` - Should only be used in pantheon/follower uniques for religions
- `in all cities in which the majority religion is a major religion`
- `in all cities in which the majority religion is a enhanced religion`


## combatantFilter
This indicates a combatant, which can either be a unit or a city (when bombarding).
Must either be `City` or a `mapUnitFilter`.


## constructionFilter
A filter for used when testing the current construction of a city. All values of `baseUnitFilter` and `buildingFilter` are allowed.


## costOrStrength
`Cost` or `Strength`


## era
The name of any era


## foundingOrEnhancing
`founding` or `enhancing`


## great person
The name of any great person


## improvementFilter
For filtering a specific improvement.

Allowed values are:
- improvement name (Note that "Road" and "Railroad" _do_ work as improvementFilters, but not as tileFilters at the moment.)
- `All`
- `Great Improvements`, `Great`
- `All Road` - for Roads & Railroads


## improvementName
The name of any improvement


## mapUnitFilter
This indicates a unit as placed on the map. Compare with `baseUnitFilter`. 
It can be any value noted in `baseUnitFilter` or one of the following:
- `Wounded`, `wounded units`
- `City-State`
- `Barbarians`, `Barbarian`
- Again, any combination of the above is also allowed, e.g. `[{Wounded} {Water}]` units.


## plunderableStat
All the following stats can be plundered: `Gold`, `Science`, `Culture`, `Faith`


## policy
The name of any policy


## promotion
The name of any promotion


## regionType
Used for dividing the world into regions in each of which a single player is placed at the start of the game.
Allowed values are `Hybrid` and the name of any terrain that has one of the following two uniques:
- `A Region is formed with at least [amount]% [simpleTerrain] tiles, with priority [amount]`
- `A Region is formed with at least [amount]% [simpleTerrain] tiles and [simpleTerrain] tiles, with priority [amount]`


## resource
The name of any resource


## simpleTerrain
Used by NaturalWonderGenerator to place natural wonders

Allowed values are:
- `Land`
- `Water`
- `Elevated`
- The name of any terrain


## specialist
The name of any specialist


## stats
This indicates a text comprised of specific stats and is slightly more complex.

Each stats is comprised of several stat changes, each in the form of `+{amount} {stat}`, where 'stat' is one of the seven major stats mentioned above.
For example: `+1 Science`.

These can be strung together with ", " between them, for example: `+2 Production, +3 Food`.


## stat
This is one of the 7 major stats in the game - `Gold`, `Science`, `Production`, `Food`, `Happiness`, `Culture` and `Faith`. Note that the stat names need to be capitalized!

 
## tech
The name of any tech


## terrainFilter
This indicates the terrain on a single tile. The following values are allowed:

- A filter names a specific json attribute (by name):
    - Base terrain
    - Terrain features
    - Base terrain uniques
    - Terrain feature uniques
    - Resource
    - Natural wonder
- Or the filter is a constant string choosing a derived test:
    - `All`
    - `Water`, `Land`
    - `Coastal` (at least one direct neighbor is a coast)
    - `River` (as in all 'river on tile' contexts, it means 'adjacent to a river on at least one side')
    - `Open terrain`, `Rough terrain` (note all terrain not having the rough unique is counted as open)
    - `Friendly Land` - land belonging to you, or other civs with open borders to you
    - `Foreign Land` - any land that isn't friendly land
    - `Enemy land` - any land belonging to a civ you are at war with
    - `Water resource`, `Strategic resource`, `Luxury resource`, `Bonus resource`
    - `Natural Wonder` (as opposed to above which means testing for a specific Natural Wonder by name, this tests for any of them)

Please note all of these are _case-sensitive_.

Also note: Resource filters depend on whether a viewing civ is known in the context where the filter runs. Water and specific tests require a viewing civ, and if the resource needs a tech to be visible, that tech to be researched by the viewing civ. The other resource category tests can succeed without a known viewing civ only for resources not requiring any tech. So - test your mod!

So for instance, the unique "[stats] from [tileFilter] tiles [cityFilter]" can match several cases:


## terrainQuality
Used to indicate for what use the terrain should be viewed when dividing the world into regions, in each of which a single player is placed at the start of the game.

Allowed values are:
- improvement name (Note that "Road" and "Railroad" _do_ work as improvementFilters, but not as tileFilters at the moment.)
- "All"
- "Great Improvements", "Great"
- "All Road" - for Roads & Railroads


## tileFilter
Anything that can be used either in an improvementFilter or in a tileFilter can be used here


## victoryType
The name of any victory type:
- `Neutral`
- `Cultural`
- `Diplomatic`
- `Domination`
- `Scientific`
- `Time`