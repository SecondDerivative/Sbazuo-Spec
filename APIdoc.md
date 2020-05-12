Response - {result, error}

Description method |Method name | Params                             |Result                                 |
-------------------|------------|------------------------------------|---------------------------------------|
join to session    |Join        |{}                                  |{Token, playerID}                      |
get data           |Get         |{TKN}                               |GetResponse                            |
Create block  by left down corner |CreateBlock |{TKN, Position:PNT, BlockId, ShapeID} |\empty                |
Shhot              |Shoot       |{TKN, ProjectileID, MotionDirection:PNT} |\empty                            |



ShapeID - sqare, triangle...

BlockID - physical...


GetResponse

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
events      |TypedEvent[]|all new events (now is empty)    |
state       |GameState|Current game state                  |

TypedEvent

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
type        |string  |all new events                       |
value       |IEvent  |value of event                       |

*TODO: typed game state with gameModId*

GameState

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
conditionId |int     |Preaparation, game, end              |
currentPlayerID|string|id of player, which turn now        | 
blocks      |TypedBlock[]|Array of blocks                  |
projectiles |TypedProjectile[]|Existed projectiles         |
rules       |TypedRules[]|game rules                         |

TypedBlock

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
blockType   |string  |type of block                        |
value       |IBlock  |value of block                       |

IBlock

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
ownerID     |string  |if of block's owner                  |
shapeID     |string  |id of shape                          |
shapePos    |Point   |smth like left down corner           |

PhysicalBlock : IBlock

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
health      |int     |hp of block                          |
maxHp       |int     |max hp of this block                 |


TypedProjectile

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
projectileID|string  |id of projectile                     |
value       |IProjectile|value of projectile               |

IProjectile

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
shape       |Circle  |pos and size of projectile           |
motionVector|Point   |motion vector                        |
ownerId     |string  |id of player who ownthis projectile  |
health      |int     |hp of projectile                     |
maxHp       |int     |max hp of projectile                 |


TypedRules

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
ruleId      |string  |id of rule                           |
value       |IRule   |id of rule                           |

Gravity : IRule

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
direction   |Point   |direction of gravity                 |
