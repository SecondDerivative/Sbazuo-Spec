# API format

Response - {result, error}

Description method |Method name | Params                             |Result                                 |
-------------------|------------|------------------------------------|---------------------------------------|
get data           |Game/Get    |{TKN}                               |GetResponse                            |
Create block  by left down corner |Game/CreateBlock |{TKN, Position:PNT, BlockId, ShapeId} |\empty           |
Shoot              |Game/Shoot    |{TKN, ProjectileId, MotionDirection:PNT} |\empty                          |
creating new lobby |Session/CreateLobby|{TKN, LobbyName:string}      |LobbyInfo                              |
joining to lobby   |Session/JoinLobby|{TKN, LobbyId:string}          |LobbyInfo                              |
leaving from lobby |Session/LeaveLobby|{TKN}                         |\empty                                 |
starting lobby game|Session/Start |{TKN}                             |\empty                                 |
returns existing lobbies|Session/GetLobbies|{TKN}                    |LobbyInfo[]                            |
returns existing players|Session/GetPlayers|{TKN}                    |AccountInfo[]                          |
login to account   |Accounts/Login|{authInfo:AuthRequest}            |TKN                                    |
register and login to account|Accounts/Auth|{authInfo:AuthRequest}   |TKN                                    |


ShapeId - sqare, triangle...

BlockId - physical...

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
conditionId    |string       |Preaparation, game, end              |
currentPlayerId|string       |id of player, which turn now         | 
blocks         |IBlock[]     |Array of blocks                      |
projectiles    |IProjectile[]|Existed projectiles                  |
rules          |IRules[]     |game rules                           |
players        |Map<String, Player>|map from playedId to player's info|


IBlock

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
blockId     |string  |block id                             |
ownerId     |string  |id of block's owner                  |
shapeId     |string  |id of shape                          |
shapePosition|Point  |smth like left down corner           |

PhysicalBlock : IBlock

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
health      |int     |hp of block                          |
maxHealth   |int     |max hp of this block                 |


IProjectile

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
projectileId|string  |id of projectile                     |
position    |Point   |pos of projectile                    |
radius      |double  |radius of projectile                 |
motionVector|Point   |motion vector                        |
ownerId     |string  |id of player who ownthis projectile  |
health      |int     |hp of projectile                     |
maxHealth   |int     |max hp of projectile                 |

IRule

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
ruleId      |string  |id of rule                           |

Gravity : IRule

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
direction   |Point   |direction of gravity                 |

Player

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
catapultPosition|Point|position of player's catapult       |
id          |string  |playerId                             |
ownAreasIds |string[]|array of area's Id                   |
~~nickname~~|string  |nick of player                       |

# Service format

AuthRequest

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
Nickname    |string  |account's nickname                   |
Password    |string  |password                             |

AccountInfo

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
Nickname    |string  |account's nickname                   |
Id          |string  |account's Id                         |

LobbyInfo

Name        |Type    |Description                          |
------------|--------|-------------------------------------|
Id          |string  |lobby's Id                           |
LobbyName   |string  |lobby's name                         |
CreatorId   |string  |Id of player, which created this lobby|
PlayerIds   |string[]|array of players, which joined to lobby|
MapId       |string? |selected map id                      |
ModId       |string? |selected mod id                      |

