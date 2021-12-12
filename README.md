# fxserver-esx_status
FXServer ESX Status
[INSTALLATION]

1) **Placé le dossier dans ressource et puis dans ESX**
2) **Importer esx_status.sql dans votre base de données**
3) **Ajoutez ceci dans votre server.cfg** :

```
start esx_status
```

[HOWTO]

server.lua
```lua

local name    = 'hunger'
local default = 1000000
local color   = '#CFAD0F'

TriggerEvent('esx_status:registerStatus', name, default, color, 
	function(status) --Rappel visible, s'il retourne vrai, le statut sera visible
		return true
	end,
	function(status) -- Rappel de tick, que faire à chaque tick
		status.remove(200)
	end,
	{remove = 200} -- Client action (add / remove) afin que le client puisse être synchronisé avec le serveur
)


```
