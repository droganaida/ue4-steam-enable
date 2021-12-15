## Как протестировать свою сетевую игру в Steam (Unreal Engine UE4)

### 1. Включаем плагин Online Subsystem Steam
Для этого идём в меню Edit->Plugins,  и в поисковой строке набираем что-то вроде "steam online" =)

![Online Subsystem Steam enable](https://github.com/droganaida/ue4-steam-enable/blob/main/sts-1.jpg?raw=true)

### 2. Добавляем Steam App ID в свой конфиг
Находим файл DefaultEngine.ini в папке своего проекта в подпапке Config и добавляем следующий код:
```
[/Script/Engine.GameEngine]
+NetDriverDefinitions=(DefName="GameNetDriver",DriverClassName="OnlineSubsystemSteam.SteamNetDriver",DriverClassNameFallback="OnlineSubsystemUtils.IpNetDriver")

[OnlineSubsystem]
DefaultPlatformService=Steam

[OnlineSubsystemSteam]
bEnabled=true
SteamDevAppId=480

[/Script/OnlineSubsystemSteam.SteamNetDriver]
NetConnectionClassName="OnlineSubsystemSteam.SteamNetConnection"
```
![Steam App ID](https://github.com/droganaida/ue4-steam-enable/blob/main/sts-2.jpg?raw=true)
ID=480 - это код игры Spacewar от Valve, его можно использовать для теста своих игр ;)

### 3. Пакуем игру под свою систему, но обязательно как Shipping Build
Меню Edit->Project Settings, раздел Packaging

![Packaging](https://github.com/droganaida/ue4-steam-enable/blob/main/sts-3.jpg?raw=true)

### 4. Добавляем steam_appid.txt
Создайте текстовый файл в папке с готовым билдом игры в подпапке \Название_Игры\Binaries\Win64
В этом файле только 1 строчка с ID нашей игры:
```
480
```
![steam_appid.txt](https://github.com/droganaida/ue4-steam-enable/blob/main/sts-4.jpg?raw=true)

### 5. Играем с друзьями!
Просто отдайте папку с игрой (лучше зазиповать конечно) своему другу или перекиньте на свой второй комп.
У каждого игрока должен быть включен Steam (и конечно в стим нужно войти).
У всех игроков должен быть установлен один Download Region.

![Download Region Steam](https://github.com/droganaida/ue4-steam-enable/blob/main/sts-5.jpg?raw=true)

Если у вас в игре есть галочка LAN, убираем её и для хоста, и для поиска сервера.

