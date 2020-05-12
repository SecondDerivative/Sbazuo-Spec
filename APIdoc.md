# API format

Response - {result, error}

Description method |Method name | Params                             |Result                                 |
-------------------|------------|------------------------------------|---------------------------------------|
join to session    |Join        |{}                                  |{Token, playerID}                      |
get data           |Get         |{TKN}                               |GetResponse                            |
Create block  by left down corner |CreateBlock |{TKN, Position:PNT, BlockId, ShapeID} |\empty                |
Shhot              |Shoot       |{TKN, ProjectileID, MotionDirection:PNT} |\empty                            |



ShapeID - sqare, triangle...

BlockID - physical...

# Get format

GetResponse

Name        |Type     |Description                          |
------------|---------|-------------------------------------|
events      |IEvent[] |all new events (now is empty)        |
state       |GameState|Current game state                   |

IEvent

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
eventId     |string  |id of event                          |

*TODO: IGameState, gameModId and other*

GameState

Name           |Type         |Description                          |
---------------|-------------|-------------------------------------|
conditionId    |int          |Preaparation, game, end              |
currentPlayerID|string       |id of player, which turn now         | 
blocks         |IBlock[]     |Array of blocks                      |
projectiles    |IProjectile[]|Existed projectiles                  |
rules          |IRules[]     |game rules                           |

IBlock

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
blockId     |string  |block id                             |
ownerID     |string  |if of block's owner                  |
shapeID     |string  |id of shape                          |
shapePos    |Point   |smth like left down corner           |

PhysicalBlock : IBlock

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
health      |int     |hp of block                          |
maxHp       |int     |max hp of this block                 |


IProjectile

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
projectileID|string  |id of projectile                     |
shape       |Circle  |pos and size of projectile           |
motionVector|Point   |motion vector                        |
ownerId     |string  |id of player who ownthis projectile  |
health      |int     |hp of projectile                     |
maxHp       |int     |max hp of projectile                 |

IRule

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
ruleId      |string  |id of rule                           |

Gravity : IRule

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
direction   |Point   |direction of gravity                 |
