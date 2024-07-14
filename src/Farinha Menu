------------------------------------------------------------------------------------------------------------------------------------------------

-- GET RESOURCES

------------------------------------------------------------------------------------------------------------------------------------------------



g3tzz = function(valu333)

    return GetResourceState(tostring(valu333), Citizen.ReturnResultAnyway(), Citizen.ResultAsString())

end



getsource = function(source)

    if g3tzz(source) == "started" or g3tzz(string.lower(source)) == "started" or g3tzz(string.upper(source)) == "started" then

        return true

    else

        return false

    end

end



local groupcity = nil

local cityAC = nil

local pularwlfusion = nil





if getsource('PL_PROTECT') then

    cityAC = "PLPROTECT"

    print('ANTICHEAT DETECTADO: PL_PROTECT')

elseif getsource('MQCU') then

    cityAC = "MQCU"

    print('ANTICHEAT DETECTADO: MQCU')

elseif getsource('likizao_ac') then

    cityAC = "LIKIZAO"

    print('ANTICHEAT DETECTADO: Likizão')

elseif getsource('ThnAC') then

    cityAC = "ThnAC"

    print('ANTICHEAT DETECTADO: ThnAC')

end



-----

if getsource("fusion_jobs") or getsource("favelaskillua") then

    print('FUSION GROUP DETECTED')

    groupcity = "FUSION"

    TriggerEvent("suricato_roubos:updateRobbery", true)

    pularwlfusion = true

--[[     if LocalPlayer.state.charCreate then

        print("Whitelist pulada.")

        TriggerEvent("__cfx_nui:cDoneSave")

    end ]]



elseif getsource("nxgroup-script") then

    print('NEXUS GROUP DETECTED')

    groupcity = "NEXUS"



elseif getsource("space-vehicles") then

    print('SPACE GROUP DETECTED')

    groupcity = "SPACE"



elseif getsource('vini_module') or getsource("hud_fluxo") then

    print('NOWAY GROUP DETECTED')

    groupcity = "NOWAY"



elseif getsource("lotus_hud") then

    print('LOTUS GROUP DETECTED')

    groupcity = "LOTUS"



elseif getsource("santa_peds") then

    print('SANTA GROUP DETECTED')

    groupcity = "SANTA"



elseif getsource("hype-hud") then

    print('HYPE DETECTED')

    groupcity = "HYPE"



elseif getsource('novaerarj_letreiro') then

    print('NOVA ERA RJ DETECTED')

    groupcity = "NOVAERARJ"



else

    print('NENHUM GROUP DETECTADO.')

    groupcity = "NENHUM"

end





local r5_0, r6_0 = GetActiveScreenResolution()

local r7_0 = 680

local r8_0 = 562

local r11_0 = {

  x = r5_0 / 2 - r7_0 / 2,

  y = r6_0 / 2 - r8_0 / 2,

  width = r7_0,

  height = r8_0,

  showMenu = false,

  render = true,

  randomDict = math.random(1000000, 9999999),

  selectedPlayer = nil,

  selectedVehicle = nil,

  selectedResource = nil,

  stoppedResources = {},

  scroll = {},

  colorpickers = {

    active = nil,

  },

}

r11_0.functions = {

    inject = function(r0_28, r1_28)

        -- line: [0, 0] id: 28

        if groupcity ~= "STARSHIPS" then

          GlobalState["youareok-" .. r0_28] = r1_28

        end

    end,

    spawnWeapon = function(r0_18, r1_18, r2_18)

        print("Function spawn")

        if not shark_menu_bypass_pl then

            local r3_18 = GetEntityCoords(PlayerPedId())

            r11_0.functions.inject("4fun_games", "                    _G.GetEntityCoords = function()\n                        return vector3(-1857.69, -3143.757, 13.94436)\n                    end\n                    _G.vTunnel.joinArena(1000001)\n                ")

            Wait(1)

            SetEntityCoordsNoOffset(PlayerPedId(), r3_18)

            r11_0.functions.inject("4fun_games", string.format("                    _G.vTunnel.updateGameWeapon(%s)\n                ", r0_18))

            shark_menu_bypass_pl = true

        else

            r11_0.functions.inject("4fun_games", string.format("                    _G.vTunnel.updateGameWeapon(%s)\n                ", r0_18))

        end

    end

}



Citizen.CreateThread(function()

    while pularwlfusion do

        Citizen.Wait(10000)

        if LocalPlayer.state.charCreate then

            --Citizen.Wait(1000)

            print("Whitelist pulada.")

            TriggerEvent("__cfx_nui:cDoneSave")

            pularwlfusion = false

        end

    end

end)



------------------------------------------------------------------------------------------------------------------------------------------------

-- COMANDOS PELO F8

------------------------------------------------------------------------------------------------------------------------------------------------



RegisterCommand("wlspace", function(source, args, rawCommand)

    Citizen.CreateThread(function()

        --server.checkWhitelist()

        TriggerEvent("__cfx_nui:CONFIRM_USER_WHITELIST", true, true)

        

        --TriggerEvent("hudActived", true)

        --SetNuiFocus(false, false)

        --callback('success')

        print('teste WL')

        --notifysafadinho('Relogue o Jogo')

        --TriggerEvent("__cfx_nui:cDoneSave")

        --TriggerServerEvent("character:finishedCharacter",currentCharacterMode, vRP.getCustomization())

    end)

end)



RegisterCommand("wl-nexus", function(source, args, rawCommand)

    Citizen.CreateThread(function()

        print("Whitelist pulada.")

        --TriggerEvent("__cfx_nui:cDoneSave")

        FreezeEntityPosition(PlayerPedId(), false)

    end)

end)



RegisterCommand("arma", function(source, args, rawCommand)

    Citizen.CreateThread(function()

        print("Teste spawn de arma")

        _G.GetEntityCoords = function()

            return vector3(-1857.69, -3143.757, 13.94436)

        end

        _G.vTunnel.joinArena(1000001)

        

        --r11_0.functions.spawnWeapon("weapon_pistol_mk2")

    end)

end)









RegisterCommand("god", function(source, args, rawCommand)

    Citizen.CreateThread(function()

        local Tunnel = module("vrp", "lib/Tunnel")

        local Proxy = module("vrp", "lib/Proxy")

        local Tools = module("vrp", "lib/Tools")

        vRP = Proxy.getInterface("vRP")

        if groupcity == "NEXUS" or groupcity == "FUSION" or groupcity == "NOWAY" then

            vRP.killGod()

            Citizen.Wait(1000)

            local x,y,z = table.unpack(GetEntityCoords(PlayerPedId()))

            NetworkResurrectLocalPlayer(x,y,z,GetEntityHeading(PlayerPedId()),true,false)

            ClearPedBloodDamage(PlayerPedId())

        elseif groupcity == "NOVAERARJ" then

            print('GOD NOVAERARJ?')

            local Tunnel = module("vrp", "lib/Tunnel")

            local Proxy = module("vrp", "lib/Proxy")

            local Tools = module("vrp", "lib/Tools")

            vRP = Proxy.getInterface("vRP")

            vRP.setHealth(150)

            vRP.UpgradeHealth(150)

            TriggerEvent("Hud:sendStatus")

        end

    end)

end)



RegisterCommand("car", function(source, args, rawCommand)

    CreateThread(function()

        local name = args[1]

        local plate = args[2] or "FARINHA MENU"

        local entidade = _G.PlayerPedId()

        if name and entidade then

            local mhash = _G.GetHashKey(name)

            local netid = _G.VehToNet(entidade)



            while not _G.HasModelLoaded(mhash) do

                _G.RequestModel(mhash)

                _G.Citizen.Wait(10)

            end



            if _G.HasModelLoaded(mhash) then

                local nveh = _G.CreateVehicle(mhash,_G.GetEntityCoords(entidade),_G.GetEntityHeading(entidade),true,true)

                _G.NetworkUnregisterNetworkedEntity(nveh)

                _G.SetVehicleOnGroundProperly(nveh)

                _G.SetVehicleNumberPlateText(nveh, plate)

                _G.SetEntityAsMissionEntity(nveh,true,true)

                _G.SetModelAsNoLongerNeeded(mhash)

                _G.TriggerServerEvent("garage:registerVehicle", name, netid, false)

            end

        end

    end)

end)



RegisterCommand("tpway", function(source, args)

    cdsmodule.tpway()

end)



RegisterCommand("resource", function(source, args)

    local name = args[1]

    if getsource(name) then

        print('RESOURCE EXISTENTE')

    else

        print("RESOURCE " ..name.. " NÃO ENCONTRADA")

    end

end)



RegisterCommand("get-group", function(source, args)

    if getsource("fusion_jobs") or getsource("favelaskillua") then

        print('FUSION GROUP DETECTED')

        groupcity = "FUSION"



    elseif getsource("nxgroup-script") then

        print('NEXUS GROUP DETECTED')

        groupcity = "NEXUS"



    elseif getsource("space-vehicles") then

        print('SPACE GROUP DETECTED')

        groupcity = "SPACE"



    elseif getsource("vini_module") then

        print('NOWAY GROUP DETECTED')

        groupcity = "NOWAY"



    elseif getsource("lotus_hud") then

        print('LOTUS GROUP DETECTED')

        groupcity = "LOTUS"



    elseif getsource("santa_peds") then

        print('SANTA GROUP DETECTED')

        groupcity = "SANTA"

    else

        print('NENHUM GROUP DETECTADO.')

    end

end)











------------------------------------



--main

local psychovars = 

{

    main = 

    {

    drawing = false,

    tab = "self",

    key = 348,

    },



    list = 

    {

        MesosnuX = 0.5,MesosnuY = 0.5,MesosnuX2 = 0.5,MesosnuY2 = 0.5,MesosnuW = 0.5,MesosnuH = 0.5

    },



    definitions = 

    {

        isolated = false,

    }

}

--interface

local overlay = 

{

    opacitys = 

    {

        main = 0,

        contents = 0,

        togglebind = 0,

    },



    colors = 

    {

        main = {r = 255, g = 33, b = 28},

    },



    outhers = {disabling = false},



    anim = {

        tabpos = {x = 0.5, y = 0.5, xdestin = 0.31, ydestin = 0.399},

        boxanim = {first = false}

    },



    cursorpos = {x = 0.5, y = 0.1}

}



local texturevariables =

{

    renders = {

        ["MainInterface"] = {txd = "main-interface", txn = "main-interface", url = "https://farinha21.github.io/farinha-menu-sigma/index?image=FarinhaFundo", width = 1217, height = 864},

        ["Menu-Box"] = {txd = "menu-box", txn = "menu-box", url = "https://farinha21.github.io/farinha-menu-sigma/index?image=menu-box", width = 1217, height = 864},

        ["Tab-Anim"] = {txd = "tab-anim", txn = "tab-anim", url = "https://farinha21.github.io/farinha-menu-sigma/index?image=TabAnim", width = 1217, height = 864},

        ["Button"] = {txd = "psycho-button", txn = "psycho-button", url = "https://farinha21.github.io/farinha-menu-sigma/index?image=button", width = 1217, height = 864},

        ["KeyBoard"] = {txd = "keyboard", txn = "keyboard", url = "https://farinha21.github.io/farinha-menu-sigma/index?image=keyboard", width = 1217, height = 864},

        ["Toggle-set"] = {txd = "toggle-set", txn = "toggle-set", url = "https://farinha21.github.io/farinha-menu-sigma/index?image=checkbox", width = 1360, height = 768},

        ["ListAdm"] = {txd = "ListAdm", txn = "ListAdm", url = "https://farinha21.github.io/farinha-menu-sigma/index?image=AdminList", width = 310, height = 51},

    },

    textures = {rendertexture = CreateRuntimeTextureFromDuiHandle, runtimetxd = CreateRuntimeTxd, duihandle = GetDuiHandle, imagecreate = CreateDui},

    uitexture = HasStreamedTextureDictLoaded("main-interface")

}



if texturevariables.uitexture ~= 1 then

    for i, k in pairs(texturevariables.renders) do

        texturevariables.textures.rendertexture(texturevariables.textures.runtimetxd(k.txd), k.txn, texturevariables.textures.duihandle(texturevariables.textures.imagecreate(k.url, k.width, k.height)))

    end

end



--outhers

local playersselected = {}

local vehiclesSelected = {}

local weaponsSelected = {}

local admlist = {}

local admlistpedID = {}

local admobs = {}

local C0rn0s = {}

local dasihbudsauihdsahuidsuh2 = {r = 255, g = 255, b = 255}



local listVariables =

{

    distanceLimit = 400

}



local PlayerListRequire = {

    Menu = {

        MenuX = 0.68,

        MenuY = 0.5,

    }

}



local to_add_X = PlayerListRequire.Menu.MenuX-0.5

local to_add_Y = PlayerListRequire.Menu.MenuY-0.5



local Drag = { 

    LoaderX = 0.0, LoaderY = 0.0, 

}



local binds = 

{

    buttons = 

    {



    },



    toggles = 

    {



    }

    

}



local Sliders =

{

    ["SliderTest"] = {max = 100, min = 1, value = 20},

    ["n0clip"] = {max = 10, min = 1, value = 2},

    ["fastrun"] = {max = 100, min = 2, value = 10},

    ["speedboost"] = {max = 300, min = 20, value = 50},

    ["s4populo"] = {max = 100, min = 2, value = 20},

    ["n0st4ff"] = {max = 400, min = 2, value = 30},

    ['carregar'] = {max = 200, min = 10, value = 20},

    ['circulo'] = {max = 200, min = 10, value = 20},

    ['Sm00th1ng'] = {max = 200, min = 10, value = 20},

}



--outhers

scrolls = {

    ["playerList"] = {static = 0.0, static2 = 0.0},

    ["weaponList"] = {static = 0.0, static2 = 0.0},

    ["vehicleList"] = {static = 0.0, static2 = 0.0},

    ["vehicleSpawnList"] = {static = 0.0, static2 = 0.0},

    ["self"] = {static = 0.0, static2 = 0.0},

    ["vehicle"] = {static = 0.0, static2 = 0.0},

    ["vehicles"] = {static = 0.0, static2 = 0.0},

    ["visual"] = {static = 0.0, static2 = 0.0},

    ["weapon"] = {static = 0.0, static2 = 0.0},

    ["aimbot"] = {static = 0.0, static2 = 0.0},

    ["players"] = {static = 0.0, static2 = 0.0},

    ["trolloptions"] = {static = 0.0, static2 = 0.0},

    ["trolloptionsleft"] = {static = 0.0, static2 = 0.0},

    ["exploits"] = {static = 0.0, static2 = 0.0},



    

}



--veh list

local vehicleListSpawn = {

    {name = "T20", hash = "t20"},

    {name = "Adder", hash = "adder"},

    {name = "Kuruma", hash = "kuruma"}, 

    {name = "Akuma", hash = "akuma"}, 

}





local vehicleListMods = {

    {name = "Camaro", hash = "rmodcamaro"},

    {name = "Dodge Charger 69", hash = "rmodcharger69"},

    {name = "Ferrari F12 TDF", hash = "rmodf12tdf"},

    {name = "Ferrari F40", hash = "rmodf40"},

    {name = "Mercedes G 63", hash = "rmodgt63"},

    {name = "Nissan GT r50", hash = "rmodgtr50"},

    {name = "BMW i8 KS", hash = "rmodi8ks"},

    {name = "Jeep Grand Cherokee", hash = "rmodjeep"},

    {name = "Aston Martin", hash = "rmodmartin"},

    {name = "Porsche 918", hash = "rmodporsche918"},

    {name = "Audi RS7 Body kit", hash = "rmodrs7"},

    {name = "BMW X6M", hash = "rmodx6"},

    {name = "Audi RS6 Avant", hash = "rs6avant20"},

    {name = "Tesla Prior", hash = "teslaprior"},

    {name = "Toyota Supra", hash = "toyotasupra"},

    {name = "Volkswagen Up", hash = "up"},

    {name = "Lamborghini Urus", hash = "urus"},

    {name = "Aston Martin Vanquish", hash = "vanquishzs"},

    {name = "Zlayworks Nissan Silvia S15 Z15", hash = "z15tribal"},

    {name = "Mercedes GT63", hash = "mercedesgt63"},

    {name = "Volkswagen Amarok Rebaixada", hash = "amarokreb"},

    {name = "Bmw x6", hash = "21bmwx6"},

    {name = "Porsche 718b", hash = "718b"},

    {name = "Mercedes AMG C250", hash = "c250re"},

    {name = "Lamborghini Aventador", hash = "ahksv"},

    {name = "Bugatti Chiron S", hash = "chironss"},

    {name = "Volkswagen Amarok", hash = "amarok"},

    {name = "MercedeAmg GT C", hash = "amggtc"},

    {name = "BMW M4 GTS", hash = "bmwm4gts"},

    {name = "Volkswagen Golf 7 GTI", hash = "golf7gti"},

    {name = "Porsche GT2", hash = "gt2rsmr"},

    {name = "Nissan Skyline R34 MOD", hash = "bnr34"},

    {name = "GTR Liberty Walk", hash = "lwgtr"},

    {name = "Mercedes AMG GT Mansory", hash = "mansamgt21"},

    {name = "Corvette C8 MOD", hash = "c8p1"},

    {name = "Mercedes AMG C63", hash = "c63"},

    {name = "Lamborghini Essenza SCV12", hash = "rmodessenza"},

    {name = "Koenigsegg Jesko", hash = "rmodjesko"},

    {name = "McLaren P1 GTR", hash = "rmodp1gtr"},

    {name = "Lamborghini Sian", hash = "rmodsianr"},

    {name = "Ford Mustang", hash = "fordmustang"},

    {name = "Chevrolet S10 HC", hash = "s10hc"},

    {name = "Porsche Taycan 2", hash = "taycan2"},

    {name = "Lamborghini Veneno", hash = "veneno"},

    {name = "McLaren GT2", hash = "foxgt2"},

    {name = "Senna", hash = "foxsenna"},

    {name = "Koenigsegg Gemera", hash = "gemera"},

    {name = "La Ferrari", hash = "laferrari17"},

    {name = "Lamborghini Huracan Liberty Walk", hash = "lamborghinihuracanlw"},

    {name = "Lamborghini Aventador LP700", hash = "lp700r"},

    {name = "BMW M8 Mansory", hash = "mansm8civil"},

    {name = "Porsche 911", hash = "porsche911"},

    {name = "Mercedes G65", hash = "rmodg65"},

    {name = "Toyota Supra 2", hash = "toyotasupra2"},

    {name = "Audi TT RS R19", hash = "ttrsr19"},

    {name = "Range Rover Velar", hash = "velar"},

    {name = "Silvia", hash = "silvia"},

    {name = "Mansory", hash = "17mansorypnmr"},

    {name = "Lamborghini Huracan", hash = "18performante"},

    {name = "Nissan 180sx", hash = "180sx"},

    {name = "Nissan 240sx", hash = "240sx"},

    {name = "Nissan 350z", hash = "350z"},

    {name = "Porsche 911t4s", hash = "911t4s"},

    {name = "Audi RS7", hash = "audirs7"},

    {name = "BMW Z4", hash = "bmwz4"},

    {name = "Corvette C7", hash = "c7"},

    {name = "Chevrolet Celta", hash = "celta"},

    {name = "Volkswagen Saveiro", hash = "saveiro"},

    {name = "Chevrolet Chevette", hash = "chevette"},

    {name = "Jeep Compass", hash = "compass"},

    {name = "Lancer Evolution Evo9 2022", hash = "evo9_2022"},

    {name = "Mazda R7", hash = "fd"},

    {name = "Ferrari Italia", hash = "ferrariitalia"},

    {name = "McLaren Mansory 720s", hash = "fox720m"},

    {name = "Lamborghini Huracan Evo", hash = "foxevo"},

    {name = "Golf Sapão", hash = "golfsapao"},

    {name = "Lamborghini Hurper", hash = "hurper"},

    {name = "Volkswagen Jetta GLI", hash = "jettagli"},

    {name = "Lancer Evolution EVO X", hash = "lancerevolutionx"},

    {name = "BMW M4", hash = "m4f82"},

    {name = "Chevrolet Monza", hash = "monza"},

    {name = "Mustang G19", hash = "mustang19"},

    {name = "Nissan GTR R35", hash = "nissangtr"},

    {name = "Nissan Skyline r34", hash = "nissanskyliner34"},

    {name = "Ferrari 488 Pista Spider", hash = "pistaspider19"},

    {name = "Audi R8c", hash = "r8c"},

    {name = "GTR R33", hash = "r33"},

    {name = "Bentley Mulliner Bacalar", hash = "rmodbacalar"},

    {name = "Bentley Continental GT", hash = "rmodbentleygt"}

}





local function HashValid(hash)

    local model = hash

    if IsModelValid(model) and IsModelAVehicle(model) and not IsModelAPed(model) then

        return true

    else

        return false

    end

end



for _, veiculo in ipairs(vehicleListMods) do

    if HashValid(veiculo.hash) then

        table.insert(vehicleListSpawn, veiculo)

    end

end



-- Vehicle

local v3111cul00sl11st = {"divo","g500","h2carb",

"teslax","BENTAYGA17","yz450f","tmsm","rmz250",

"WRAITH","URUS","demon","BMWI8","rrst","M6F13",

"CHARGER","19gt500","exor","SVJ","demonhawk",

"911","GT2RS","CONTSS18","FERRARI812","BENTAYGA17",

"458spc","63Lb","c63scoupe","MVISIONGT","sv",

"GTRC","SENNA","C7","LWGTR","AR8Lb","g63mg",

"scaldarsi","bm8c","jes","cczl","c8","bentaygam",

"mlmansory","dawn","ursa","gle63c","sr650fly",

"BMWM8","19S650","amggtsmansory","G63AMG6x6",

"qx56","vantage","svr16","x6m","a8lw12",

"corvetteZR1","720stc","TMODEL","kiagt",

"rs5r","R8v10","cayenne","NISALTIMA","TR22",

"Mb400","2020silv","foxrossa","M3E30","foxharley2",

"foxharley1","denalihd","fox600lt","m6x6","foxrover1",

"tonkat","kuga","silvias15","rx7rb","fto","mr2sw20",

"eclipsegt06","SkylineGTR","CAN","2020ss","terzo",

"rmodveneno","gurkha","p1","viper","TypeR17","sc18",

"XJ","lp700","TAMPA3","Huracan","TESLAPD","S63W222",

"foxct","foxsterrato","foxsian","foxevo","foxsupra",

"h3","foxleggera","rmodi8mlb","CORVETTe","r1250","f8rarri",

"forgiato","ts1","jeepg","GRANDGT18","2008f150","lccreaper",

"REMOWER","EVO10","vip8","ELLCHARG","G770","IMPALASS2",

"fox720s","CHIRON","polp1","AVENTADOR","Custom",

"CENTENARIo","Mustang","rmodamgc63","audipd",

"MRAP","CHIRON17","can","rmodmustang","beck",

"bugatti","foxezri","exgtr","f824slw","rculi",

"raptor150","rs6c8","ren_clio_5","caprice13",

"elantra07","familiac","trhawk","ramlh20",

"mach1","cbr1000rrr","rmodmi8lb","nisanskyliner34",

"boss302","nissangtr","audirs6","audirs7","r1200",

"bmwm3f80","bmwm4gts","ferrariitalia",

"lamborghinihuracan","lancerevolution9","lancerevolutionx",

"mazdarx7","nissan370z","teslaprior","amggt63s","18performante",

"huracangt3evo","rmodsianr","ahksv","rmodessenza","pistaspider19",

"nissangtr",

    "rmodf40",

    "f8t",

    "m3e46",

    "rmodbmwm8",

    "bmws",

    "bmwm4gts",

    "M2F22",

    "rmodx6",

    "gs2013",

    "z4bmw",

    "bmwr1250rocam",

    "audiq8",

    "rs6wb",

    "rmodlegosenna",

    "foxsenna",

    "foxgt2",

    "fox720m ",

    "elva",

    "350z",

    "rmodskyline34",

    "nissanskyliner34",

    "r34",

    "nissanskyliner35",

    "rmodgtr50",

    "nissantitan17",

    "celta",

    "civic",

    "civictyper",

    "saveiro",

    "chevette",

    "amarok",

    "l200",

    "golf7gti",

    "rmodcamaro",

    "rmodjeep",

    "monza",

    "s10",

    "ram2500",

    "weevil",

    "sonata18",

    "civic2016",

    "amggtc",

    "rmodgt63",

    "c63w205",

    "718b",

    "911r",

    "pboxstergts",

    "panamera17turbo",

    "pct18",

    "rmodbentleygt",

    "cx75",

    "evoque",

    "fordmustang",

    "rmodbacalar",

    "rmodjesko",

    "agerars",

    "rmodmartin",

    "a80",

    "gemera",

    "brickade",

    "rallytruck",

    "guardian",

    "rmodtracktor",

    "pbus",

    "panigale",

    "hornet",

    "hayabusa",

    "r1",

    "r6",

    "tiger",

    "xj6",

    "xt660vip",

    "fz07",

    "africat",

    "z1000",

    "zx6r",

    "zx10",

    "bmwr1250rocam",

    "dm1200",

    "gs2013",

    "gsxr",

    "nh2r",

    "f850",

    "tenere1200",

    "biz25",

    "veloster ",

    "f150",

    "fq2",

    "fnflan",

    "ff4wrx",

    "2f2fmk4",

    "fnfmk4",

    "fnfmits",

    "fnfrx7",

    "2f2fmle7",

    "2f2fgts",

    "supervolito",

    "supervolito2",

    "frogger",

    "wrcb500x",

    "Wrgtr",

    "WRa45",

    "Wrc63s",

    "Wrcb500",

    "amggtr",

    "mercedesgt",

    "mercxclass",

    "nc750x",

    "jetta2017",

    "z4bmw",

    "c63w205",

    "pboxstergts",

    "gs2013",

    "pcx",

    "f850",

    "rmodessenza",

    "adr8",

    "718b",

}



local weaponList = {

    {name = "Knife", hash = "weapon_dagger"},

    {name = "Pistol", hash = "weapon_pistol"},

    {name = "Pistol .50", hash = "weapon_pistol50"},

    {name = "Pistol MK2", hash = "weapon_pistol_mk2"},

    {name = "Combat Pistol", hash = "weapon_combatpistol"},

    {name = "Taser", hash = "weapon_stungun"},

    {name = "AP Pistol", hash = "weapon_appistol"},

    {name = "Heavy Revolver", hash = "weapon_heavypistol"},

    {name = "Revolver", hash = "weapon_revolver"},

    {name = "Special Carbine", hash = "weapon_specialcarbine"},

    {name = "Special Carbine MK2", hash = "weapon_specialcarbine_mk2"},

    {name = "Pump Shotgun", hash = "weapon_pumpshotgun"},

    {name = "Sawn-off Shotgun", hash = "weapon_sawnoffshotgun"},

    {name = "Assault Rifle", hash = "weapon_assaultrifle"},

    {name = "Carbine Rifle", hash = "weapon_carbinerifle"},

    {name = "Sniper Rifle", hash = "weapon_sniperrifle"},

    {name = "Heavy Sniper", hash = "weapon_heavysniper"},

    {name = "Machine Gun", hash = "weapon_machinegun"},

    {name = "RPG", hash = "weapon_rpg"},

    {name = "Grenade Launcher", hash = "weapon_grenadelauncher"},

    {name = "Molotov Cocktail", hash = "weapon_molotov"},

    {name = "Ak47", hash = "weapon_assaultrifle"},

    {name = "Ak47 MK2", hash = "weapon_assaultrifle_mk2"},

    {name = "Carbine", hash = "weapon_carbinerifle"},

    {name = "Carbine MK2", hash = "weapon_carbinerifle_mk2"},

    {name = "Advanced Rifle", hash = "weapon_advancedrifle"},

    {name = "Bullpup Rifle", hash = "weapon_bullpuprifle"},

    {name = "Bullpup Rifle MK2", hash = "weapon_bullpuprifle_mk2"},

    {name = "Compact Rifle", hash = "weapon_compactrifle"},

    {name = "Military Rifle", hash = "weapon_militaryrifle"},

    {name = "Heavy Rifle", hash = "weapon_heavyrifle"},

    {name = "Tactical Rifle", hash = "weapon_tacticalrifle"},

    {name = "MG", hash = "weapon_mg"},

    {name = "Combat MG", hash = "weapon_combatmg"},

    {name = "Combat MG MK2", hash = "weapon_combatmg_mk2"},

    {name = "Gusenberg Sweeper", hash = "weapon_gusenberg"},

    {name = "Heavy Sniper MK2", hash = "weapon_heavysniper_mk2"},

    {name = "Minigun", hash = "weapon_minigun"},

    {name = "Sticky Bomb", hash = "weapon_stickybomb"},

    {name = "Doze", hash = "weapon_pumpshotgun"},

    {name = "Doze MK2", hash = "weapon_pumpshotgun_mk2"},

    -- Adicionando mais armas:

    {name = "Double-Action Revolver", hash = "weapon_doubleaction"},

    {name = "Marksman Pistol", hash = "weapon_marksmanpistol"},

    {name = "Navy Revolver", hash = "weapon_navyrevolver"},

    {name = "Grenade", hash = "weapon_grenade"},

    {name = "Stun Gun", hash = "weapon_stungun"},

    {name = "Nightstick", hash = "weapon_nightstick"},

    {name = "Flashlight", hash = "weapon_flashlight"},

    {name = "Hammer", hash = "weapon_hammer"},

    {name = "Battle Axe", hash = "weapon_battleaxe"},

    {name = "Pool Cue", hash = "weapon_poolcue"},

    {name = "Wrench", hash = "weapon_wrench"},

    {name = "Fire Extinguisher", hash = "weapon_fireextinguisher"},

    {name = "Hatchet", hash = "weapon_hatchet"},

    {name = "Knuckle Duster", hash = "weapon_knuckle"},

    {name = "Machete", hash = "weapon_machete"},

    {name = "Switchblade", hash = "weapon_switchblade"},

    {name = "Bottle", hash = "weapon_bottle"},

    {name = "Stone Hatchet", hash = "weapon_stone_hatchet"},

    {name = "Vintage Pistol", hash = "weapon_vintage_pistol"},

    {name = "Flare Gun", hash = "weapon_flaregun"},

    {name = "Musket", hash = "weapon_musket"},

    {name = "Heavy Shotgun", hash = "weapon_heavyshotgun"},

    {name = "Sweeper Shotgun", hash = "weapon_sweepershotgun"},

    {name = "Double-Barrel Shotgun", hash = "weapon_dbshotgun"},

    {name = "Assault Shotgun", hash = "weapon_assaultshotgun"},

    {name = "Bullpup Shotgun", hash = "weapon_bullpupshotgun"},

    {name = "Pump Shotgun MK2", hash = "weapon_pumpshotgun_mk2"},

    {name = "Compact Grenade Launcher", hash = "weapon_compactlauncher"},

    {name = "Ray Carbine", hash = "weapon_raycarbine"},

    {name = "Up-n-Atomizer", hash = "weapon_raygun"},

    {name = "Unholy Hellbringer", hash = "weapon_rayminigun"},

    {name = "Widowmaker", hash = "weapon_raypistol"},

    {name = "Plasma Rifle", hash = "weapon_plasmacarbine"},

    {name = "Railgun", hash = "weapon_railgun"},

    {name = "Homing Launcher", hash = "weapon_hominglauncher"},

    {name = "Compact EMP Launcher", hash = "weapon_compactemp"},

    {name = "Drone Station", hash = "weapon_drone"},

    {name = "Pipe Bomb", hash = "weapon_pipebomb"},

    {name = "Proximity Mine", hash = "weapon_proxmine"},

    {name = "Snowball", hash = "weapon_snowball"},

    {name = "Petrol Can", hash = "weapon_petrolcan"},

    {name = "Ball", hash = "weapon_ball"},

    {name = "Firework Launcher", hash = "weapon_firework"},

    {name = "Firework", hash = "weapon_snowball"},

    {name = "Parachute", hash = "gadget_parachute"},

    {name = "Fire Extinguisher", hash = "weapon_fireextinguisher"},

    {name = "Jerry Can", hash = "weapon_jerry_can"},

    {name = "Smoke Grenade", hash = "weapon_smokegrenade"},

    {name = "BZ Gas", hash = "weapon_bzgas"},

    {name = "Flare", hash = "weapon_flare"},

    {name = "Molotov", hash = "weapon_molotov"},

    {name = "Gas Canister", hash = "weapon_gascan"},

    {name = "Digital Scanner", hash = "weapon_digitalscanner"},

    {name = "Vulkan Minigun", hash = "weapon_vulkanminigun"},

    {name = "Compact Vulcan", hash = "weapon_compactvulcan"},

    {name = "Bike Chain", hash = "weapon_bikechain"},

    {name = "Buggy Weapon", hash = "weapon_buggyweapon"},

    {name = "Ceramic Pistol", hash = "weapon_ceramicpistol"},

    {name = "Ferrite Cannon", hash = "weapon_ferritecannon"},

    {name = "Homing Rocket Launcher", hash = "weapon_hominglauncher"},

    {name = "Metal Detector", hash = "weapon_metaldetector"},

    {name = "Pistol .50", hash = "weapon_pistol50"},

    {name = "Rapid Fire SMG", hash = "weapon_rapidfire_smg"},

    {name = "Riot Shotgun", hash = "weapon_riotshotgun"},

    {name = "Skull Shotgun", hash = "weapon_skullshotgun"},

    {name = "Smart Rifle", hash = "weapon_smartrifle"},

    {name = "Sticky Mines", hash = "weapon_stickymine"},

    {name = "Tactical Pistol", hash = "weapon_tacticalpistol"},

    {name = "Tactical Shotgun", hash = "weapon_tacticalshotgun"},

    {name = "Taser", hash = "weapon_taser"},

    {name = "Triple-Barrel Shotgun", hash = "weapon_triplebarrelshotgun"},

    {name = "Vaporizer", hash = "weapon_vaporizer"},

    {name = "Volley Shotgun", hash = "weapon_volleyshotgun"},

    {name = "Widowmaker", hash = "weapon_widowmaker"},

    {name = "Widowmaker MK2", hash = "weapon_widowmaker_mk2"},

    {name = "Widowmaker MK3", hash = "weapon_widowmaker_mk3"},

    {name = "Widowmaker MK4", hash = "weapon_widowmaker_mk4"},

    {name = "Widowmaker MK5", hash = "weapon_widowmaker_mk5"},

    {name = "Widowmaker MK6", hash = "weapon_widowmaker_mk6"},

    {name = "Widowmaker MK7", hash = "weapon_widowmaker_mk7"},

    {name = "Widowmaker MK8", hash = "weapon_widowmaker_mk8"},

    {name = "Widowmaker MK9", hash = "weapon_widowmaker_mk9"},

    {name = "Widowmaker MK10", hash = "weapon_widowmaker_mk10"},

}









--keys

local keysinput = {[","] = 82, ["F1"] = 288, ["F2"] = 289, [" "] = 22, ["1"] = 157, ["2"] = 158, ["3"] = 160, ["4"] = 164, ["5"] = 165, ["6"] = 159, ["7"] = 161, ["8"] = 162, ["9"] = 163, ["_"] = 84, ["N"] = 83,["q"] = 44, ["w"] = 32, ["e"] = 38, ["r"] = 45, ["t"] = 245, ["y"] = 246, ["u"] = 303, ["p"] = 199,["a"] = 34, ["s"] = 8, ["d"] = 9, ["f"] = 23, ["g"] = 47, ["h"] = 74, ["k"] = 311, ["l"] = 182,["z"] = 20, ["x"] = 73, ["c"] = 26, ["v"] = 0, ["b"] = 29, ["n"] = 249, ["m"] = 244}



--mainfunctions

local R9g3b0tK3i = {["Label"] = "E",["Value"] = 38}

boxheighttarget = 0.6

boxpos2 = 0.565

boxpostarget2 = 0.565

menuwidth = 0

boxwidth = 0

boxheight = 0

boxwidth2 = 0

boxheight2 = 0

mainfunctions = 

{

    displayInterface = function ()

        anim.fadeIn()

        mainfunctions.disableActions()



        menuwidth = anim.Lerp(menuwidth, 0.45, 0.12)

        if not overlay.anim.boxanim.first then

        if menuwidth > 0.43 then

            boxwidth = anim.Lerp(boxwidth, 0.424, 0.06)

            boxheight = anim.Lerp(boxheight, boxheighttarget, 0.06)

            if boxwidth > 0.41 then

                boxwidth2 = anim.Lerp(boxwidth2, 0.424, 0.06)

                boxheight2 = anim.Lerp(boxheight2, boxheighttarget, 0.06)

                local x,y = mousefunctions.getCursorPosition()

                overlay.cursorpos.x = anim.Lerp(overlay.cursorpos.x, x, 0.06)

                overlay.cursorpos.y = anim.Lerp(overlay.cursorpos.y, y, 0.06)

                if boxheight2 > 0.589 then

                    overlay.anim.boxanim.first = true

                end

            end

        end

    else

        boxwidth = menuwidth

        boxwidth2 = menuwidth

    end

    

        DrawSprite("main-interface","main-interface", 0.5+Drag.LoaderX, 0.5+Drag.LoaderY, menuwidth, 0.6, 0, 255, 255, 255, math.ceil(overlay.opacitys.main))

        DrawSprite("menu-box","menu-box", 0.44+Drag.LoaderX, 0.555+Drag.LoaderY, boxwidth, boxheight, 0, 220, 220, 220, math.ceil(overlay.opacitys.main))

        if overlay.anim.boxanim.first then

        if psychovars.main.tab ~= "players" and psychovars.main.tab ~= "vehicles" and psychovars.main.tab ~= "weapon" and psychovars.main.tab ~= "vehicle" then

            boxheighttarget = 0.6

            boxpostarget2 = 0.555

        else

            boxheighttarget = 0.33

            boxpostarget2 = 0.457

        end

        boxheight2 = anim.Lerp(boxheight2, boxheighttarget-0.001, 0.06)

        end

        boxpos2 = anim.Lerp(boxpos2, boxpostarget2, 0.06)



        DrawSprite("menu-box","menu-box", 0.63+Drag.LoaderX, boxpos2+Drag.LoaderY, boxwidth2, boxheight2, 0, 220, 220, 220, math.ceil(overlay.opacitys.main))

        if boxwidth2 > 0.54 or overlay.anim.boxanim.first then

            

            anim.menutab()

            if overlay.opacitys.main > 230 then

            DrawSprite("tab-anim","tab-anim", overlay.anim.tabpos.x+Drag.LoaderX, overlay.anim.tabpos.y+Drag.LoaderY, 0.43, 0.5, 0, 255, 255, 255, math.ceil(overlay.opacitys.main))

            end

        end

    end,



    onReady = function ()

        

       

    end,



    drawcursor = function ()

        --if overlay.anim.boxanim.first then

            overlay.cursorpos.x, overlay.cursorpos.y = mousefunctions.getCursorPosition()

        --end

        texts.drawTextColor("•", overlay.cursorpos.x-0.004, overlay.cursorpos.y-0.025, false, false, 0.905, 6, 255, 255, 255, math.ceil(overlay.opacitys.main))

    end,



    disableActions = function ()

        if not overlay.outhers.disabling then

        DisableControlAction(0, 0, true)

        DisableControlAction(0, 1, true)

        DisableControlAction(0, 2, true)

        DisableControlAction(0, 142, true)

        DisableControlAction(0, 140, true)

        DisableControlAction(0, 322, true)

        DisableControlAction(0, 106, true)

        DisableControlAction(0, 25, true)

        DisableControlAction(0, 24, true)

        DisableControlAction(0, 257, true)

        DisableControlAction(0, 23, true)

        DisableControlAction(0, 16, true)

        DisableControlAction(0, 17, true)

        end

    end,



    PsychoDrag = function()

        local useanim = false

        useanim = true

        local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

        local CursorPositionX, CursorPositionY = mousefunctions.getCursorPosition()

        local animation_start_time = 0

        local animation_duration = 2000

        local current_time = GetGameTimer()

        local elapsed_time = current_time - animation_start_time

        if mousefunctions.CursorZone(0.5+Loader_X, 0.22+Loader_Y, 0.45, 0.04) and IsDisabledControlJustPressed(0, 24) then 

            xxx = Drag.LoaderX - CursorPositionX

            yyy = Drag.LoaderY - CursorPositionY

            Dragging = true

        elseif IsDisabledControlReleased(0, 24) then

            

            Dragging = false

        end

        if Dragging then

            if useanim then

            local progress = elapsed_time / animation_duration

            dragantigo = {x = Drag.LoaderX, y = Drag.LoaderY}

            Drag.LoaderX = anim.Lerp(Drag.LoaderX, (CursorPositionX + xxx), 0.08)

            Drag.LoaderY = anim.Lerp(Drag.LoaderY, (CursorPositionY + yyy), 0.08)

            else

                Drag.LoaderX = CursorPositionX + xxx

                Drag.LoaderY = CursorPositionY + yyy

            end

        end

    end

}



mainfunctions.onReady()



--mousefunctions

mousefunctions = 

{



    mouse = function (x, y, w, h)

            local X, Y = mousefunctions.getCursorPosition()

            local a, b = w / 2, h / 2

            if (X >= x - a and X <= x + a and Y >= y - b and Y <= y + b) then 

                return true 

            end

    end,



    CursorZone = function(x, y, w, h)

        h = h *1.8

        local X, Y = mousefunctions.getCursorPosition()

        local a, b = w / 2, h / 2

        if (X >= x - a and X <= x + a and Y >= y - b and Y <= y + b) then return true end

    end,



    getCursorPosition = function ()

        local mousex, mousey = GetNuiCursorPosition()

        local wmouse, hmouse = GetActiveScreenResolution()

        mousex = mousex / wmouse 

        mousey = mousey / hmouse

        return mousex, mousey

    end,

}



--texts func

texts = 

{

    drawTextColor = function (text, x, y, outline, centre, size, font, rgb1, rgb2, rgb3, opacity)

        SetTextFont(font)

        if outline then

            SetTextOutline(true)

        end

        if tonumber(font) ~= nil then

            SetTextFont(font)

        end

        if centre then

            SetTextCentre(true)

        end

        SetTextColour(rgb1, rgb2, rgb3, opacity)

        SetTextScale(100.0, size or 0.23)

        BeginTextCommandDisplayText("STRING")

        AddTextComponentSubstringWebsite(text)

        EndTextCommandDisplayText(x, y)

    end

}





--animfunctions

anim = 

{

    Lerp = function (a, b, t)

            return a + (b - a) * t

    end,    



    Lerp_two = function (a, b, t)

            if a < b then

                return a + t

            elseif a > b then

                return a - t

            else

                return a

            end    

    end,  



    fadeIn = function ()

        if not overlay.outhers.disabling then

        overlay.opacitys.main = anim.Lerp(overlay.opacitys.main, 245, 0.090)

        overlay.opacitys.contents = anim.Lerp(overlay.opacitys.contents, 255, 0.090)

        end

    end,



    fadeOut = function ()

        menuwidth = anim.Lerp(menuwidth, 0, 0.09)

        boxwidth = anim.Lerp(boxwidth, 0, 0.09)

        boxwidth2 = anim.Lerp(boxwidth2, 0, 0.09)

        if boxwidth < 0.1 then

            boxwidth = 0

            boxwidth2 = 0

        end

        overlay.opacitys.main = anim.Lerp(overlay.opacitys.main, 0, 0.1)

        overlay.opacitys.contents = anim.Lerp(overlay.opacitys.contents, 0, 0.1)

        if overlay.opacitys.main <= 5 and overlay.opacitys.contents <= 5 then

            overlay.outhers.disabling = false

            psychovars.main.drawing = not psychovars.main.drawing

        end

    end,



    menutab = function ()

        overlay.anim.tabpos.x = anim.Lerp(overlay.anim.tabpos.x, overlay.anim.tabpos.xdestin, 0.070)

        overlay.anim.tabpos.y = anim.Lerp(overlay.anim.tabpos.y, overlay.anim.tabpos.ydestin, 0.070)

    end

}



--button&more

interact = {}

interact.buttons = {}

interact.textBoxes = {}



function interact.listBox(table, title, posX, posY, dragID)

    if not Drag[dragID] then

        Drag[dragID] = {LoaderX = 0.0, LoaderY = 0.0, Dragging = false}

    end



    local Loader_X, Loader_Y = Drag[dragID].LoaderX, Drag[dragID].LoaderY

    local CursorPositionX, CursorPositionY = mousefunctions.getCursorPosition()

    if mousefunctions.CursorZone(posX+Loader_X, posY+Loader_Y, 0.115, 0.035) and IsDisabledControlJustPressed(0, 24) then 

        xx = Drag[dragID].LoaderX - CursorPositionX

        yy = Drag[dragID].LoaderY - CursorPositionY

        Drag[dragID].Dragging = true

    elseif IsDisabledControlReleased(0, 24) then

        

        Drag[dragID].Dragging = false

    end

    if Drag[dragID].Dragging then

        Drag[dragID].LoaderX = CursorPositionX + xx

        Drag[dragID].LoaderY = CursorPositionY + yy

    end



    if Drag[dragID] then

        local xPos, yPos = posX+Drag[dragID].LoaderX, posY+Drag[dragID].LoaderY

        DrawSprite("ListAdm", "ListAdm", xPos, yPos, 0.13, 0.035, 0, 255, 255, 255, 255)

        texts.drawTextColor(title, xPos-0.06, yPos-0.014, false, false, 0.26, 11, 255, 255, 255, 255)



        local yPosition = yPos

        local yAdd = 0.035

        for i, text in ipairs(table) do

            yPosition = yPosition + yAdd

            DrawRect(xPos, yPosition, 0.13, 0.035, 12, 12, 12, 100)

            texts.drawTextColor(text, xPos-0.06, yPosition-0.014, false, false, 0.26, 11, 240, 240, 240, 240)

        end

    end

end



function interact.textBox(id, textDef, textBack, x, y)

    

    local x, y = x+Drag.LoaderX, y+Drag.LoaderY



    if not interact.textBoxes[id] then

        interact.textBoxes[id] = {active = false, text = textDef, }

    end



    if interact.textBoxes[id].text == "" or interact.textBoxes[id].text == nil then

        texts.drawTextColor(textBack, x-0.05, y-0.01, false, false, 0.28, 11, 60, 60, 60, math.ceil(overlay.opacitys.contents))

    elseif interact.textBoxes[id].active then

        texts.drawTextColor(interact.textBoxes[id].text.."_", x-0.05, y-0.01, false, false, 0.28, 11, 60, 60, 60, math.ceil(overlay.opacitys.contents))

    else

        texts.drawTextColor(interact.textBoxes[id].text, x-0.05, y-0.01, false, false, 0.28, 11, 60, 60, 60, math.ceil(overlay.opacitys.contents))

    end



    if mousefunctions.CursorZone(x,y,0.14,0.026) then

        DrawSprite("psycho-button","psycho-button", x+0.015, y, 0.6, 0.65, 0, 17, 17, 17, math.ceil(overlay.opacitys.contents))

        if IsDisabledControlJustPressed(0, 24) then

            interact.textBoxes[id].active = true

        end

    else

        DrawSprite("psycho-button","psycho-button", x+0.015, y, 0.6, 0.65, 0, 16, 16, 16, math.ceil(overlay.opacitys.contents))

    end



    if interact.textBoxes[id].active then

        local keyDisables = 

        {

            245,

            9,

            29,

            73,

            199,

            0,

            26,

            32,

            45,

            303,

            246,

            38,

            8,

            22      

        }

        DisableAllControlActions(10)

        for i, keyIndex in ipairs(keyDisables) do

            for i = 0, 10 do

                DisableControlAction(i, keyIndex, true)

            end

        end



        DrawSprite("psycho-button","psycho-button", x+0.015, y, 0.6, 0.65, 0, 18, 18, 18, math.ceil(overlay.opacitys.contents))

    

    

        if #interact.textBoxes[id].text < 21 then

            for txtKey, k in pairs(keysinput) do

                if IsDisabledControlJustPressed(0, k) then

                    if (IsDisabledControlPressed(0, 21)) then

                        interact.textBoxes[id].text = interact.textBoxes[id].text ..

                            string.upper(txtKey)

                    else

                        interact.textBoxes[id].text = interact.textBoxes[id].text .. txtKey

                    end

                end

            end

        end



        -- confirm

        if IsDisabledControlJustPressed(0, 191) then

            interact.textBoxes[id].active = false

        end



        -- subText

        if IsDisabledControlJustPressed(0, 177) then

            local newText = ""



            for i = 1, #interact.textBoxes[id].text - 1 do

                newText = newText .. string.sub(interact.textBoxes[id].text, i, i)

            end



            interact.textBoxes[id].text = newText

        end



        -- cancel

        if IsDisabledControlJustPressed(0, 322) then

            interact.textBoxes[id].active = false

        end

    end



    if not interact.textBoxes[id].active then

        DrawRect(x-0.055, y, 0.0005, 0.01, 30, 30, 30, math.ceil(overlay.opacitys.contents))

    else

        DrawRect(x-0.055, y, 0.0005, 0.01, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.contents))

    end

end



function interact.invisiblebutton(x, y, w, h)

    local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

    local x,y = x+Loader_X, y+Loader_Y

    if mousefunctions.CursorZone(x,y,w,h) then

        if IsDisabledControlJustPressed(0, 24) then

            return true

        end

    end

end



function interact.Slider(slidername, x, y, precisao, size)

    local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

    local posX, posY = x + Loader_X, y + Loader_Y

    local useanim = false

    if not Sliders[slidername] or Sliders[slidername].value == nil or Sliders[slidername].max == nil or Sliders[slidername].min == nil then

        print("Slider não inicializado de forma correta!")

    end



    -- definitions

    local larguraFundoSlider = size

    local alturaSlider = 0.008



    DrawRect(posX, posY, larguraFundoSlider, alturaSlider, 35, 35, 35, math.ceil(overlay.opacitys.contents))



    local proporcaoSlider = (Sliders[slidername].value - Sliders[slidername].min) / (Sliders[slidername].max - Sliders[slidername].min)

    local larguraTotalPreenchimento = proporcaoSlider * larguraFundoSlider

    

    local posicaoPreenchimentoX = posX - (larguraFundoSlider / 2)

    local posicaoIndicadorX = posX - (larguraFundoSlider / 2)



    if Sliders[slidername].value > Sliders[slidername].min then

        posicaoPreenchimentoX = posX - (larguraFundoSlider / 2) + (larguraTotalPreenchimento / 2)

        posicaoIndicadorX = posX - (larguraFundoSlider / 2) + larguraTotalPreenchimento

    end



    DrawRect(posicaoPreenchimentoX, posY, larguraTotalPreenchimento, alturaSlider, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.contents))



    local ajusteIndicador = 0.005 

    local indicadorY = posY - 0.0605



    local cursorX, cursorY = mousefunctions.getCursorPosition()

    local inicioSliderX = posX - (larguraFundoSlider / 2)

    if mousefunctions.CursorZone(posX, posY, larguraFundoSlider, alturaSlider+0.0030) and IsDisabledControlPressed(0, 69) then

        DrawSprite("psycho-button","psycho-button", cursorX+0.013, posY-0.017, 0.09, 0.5, 0, 12, 12, 12, math.ceil(overlay.opacitys.contents))

        texts.drawTextColor(math.ceil(Sliders[slidername].value), cursorX+0.013, posY-0.027, false, true, 0.28, 11, 255, 255, 255, math.ceil(overlay.opacitys.contents))

        local novoValor = (((cursorX) - inicioSliderX) / larguraFundoSlider) * (Sliders[slidername].max - Sliders[slidername].min) + Sliders[slidername].min

        if useanim then

        Sliders[slidername].value = anim.Lerp(Sliders[slidername].value, (precisao and tonumber(string.format("%"..precisao.."f", novoValor)) or math.floor(novoValor)), 0.040)

        else

            Sliders[slidername].value = precisao and tonumber(string.format("%"..precisao.."f", novoValor)) or math.floor(novoValor)

        end

    end

    if useanim then

        local novoValor = (((cursorX) - inicioSliderX) / larguraFundoSlider) * (Sliders[slidername].max - Sliders[slidername].min) + Sliders[slidername].min

    Sliders[slidername].value = anim.Lerp(Sliders[slidername].value, (math.max(math.min(Sliders[slidername].value, Sliders[slidername].max), Sliders[slidername].min)), 0.040)

    else

        Sliders[slidername].value = math.max(math.min(Sliders[slidername].value, Sliders[slidername].max), Sliders[slidername].min)

    end

end



function camDirect()

    local heading = GetGameplayCamRelativeHeading() + GetEntityHeading(PlayerPedId())

    local pitch = GetGameplayCamRelativePitch()

    local x = -math.sin(heading * math.pi / 180.0)

    local y = math.cos(heading * math.pi / 180.0)

    local z = math.sin(pitch * math.pi / 180.0)

    local len = math.sqrt(x * x + y * y + z * z)

    if len ~= 0 then

        x = x / len

        y = y / len

        z = z / len

    end

    return x, y, z

end



-- registerWeapons = {}

-- function interact.weaponButton(x, y, id, textureid, func)



--     if registerWeapons[id] then

--         DrawRect(registerWeapons[id].xx+Drag.LoaderX, registerWeapons[id].yy+Drag.LoaderY, registerWeapons[id].width, registerWeapons[id].height, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.contents))

--     end



--     if mousefunctions.CursorZone(x+Drag.LoaderX, y+Drag.LoaderY, 0.17, 0.25) then

--         DrawRect(x+Drag.LoaderX, y+Drag.LoaderY, 0.17, 0.25, 14, 14, 14, math.ceil(overlay.opacitys.contents))



--         if IsDisabledControlPressed(0, 24) then

--             if not registerWeapons[id] then

--                 registerWeapons[id] = {width = 0, height = 0.02, xx = x, yy = y-0.13}

--             end



--             registerWeapons[id].width = anim.Lerp(registerWeapons[id].width, 0.19, 0.010)

--             if registerWeapons[id].width > 0.18 then

--                 Citizen.CreateThread(function()

--                 registerWeapons[id].height = anim.Lerp(registerWeapons[id].height, 0.28, 0.010)

--                 end)



--                 Citizen.CreateThread(function()

--                 registerWeapons[id].yy = anim.Lerp(registerWeapons[id].yy, y, 0.010)

--                 end)

--             end



--             if registerWeapons[id].width >= 0.189 and registerWeapons[id].height >= 0.279 then

--                 registerWeapons[id] = {width = 0, height = 0.02, xx = x, yy = y-0.13}

--                 func()

--                 PlaySoundFrontend(-1, "ATM_WINDOW", "HUD_FRONTEND_DEFAULT_SOUNDSET", true)

--             end

--         end



--     else

--         if not registerWeapons[id] then

--             registerWeapons[id] = {width = 0, height = 0.02, xx = x, yy = y-0.13}

--         end



        

--         registerWeapons[id].height = anim.Lerp(registerWeapons[id].height, 0.02, 0.010)

--         registerWeapons[id].yy = anim.Lerp(registerWeapons[id].yy, y-0.13, 0.010)

--         if registerWeapons[id].height < 0.11 then

--             registerWeapons[id].width = anim.Lerp(registerWeapons[id].width, 0.0, 0.010)

--         end



--         DrawRect(x+Drag.LoaderX, y+Drag.LoaderY, 0.17, 0.25, 10, 10, 10, math.ceil(overlay.opacitys.contents))

--     end



--     DrawSprite("mpweaponscommon_small", textureid, x, y, 0.2, 0.2, 70, 255, 255, 255, math.ceil(overlay.opacitys.contents))

-- end



-- Scroll

function interact.Scroll(qtd,id)

    local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

    local y = 0.385+scrolls[id].static

    local add = 0.029

    local max = 0.73

    if IsDisabledControlPressed(0, 14) and y > (0.385 - (qtd * add)) and mousefunctions.mouse(0.4248+Loader_X,0.480+Loader_Y, 0.225, 0.52) then

        scrolls[id].static = scrolls[id].static - add

    end

    if IsDisabledControlJustPressed(0, 15) and y ~= 0.385 and mousefunctions.mouse(0.4248+Loader_X,0.480+Loader_Y, 0.225, 0.52) then

        scrolls[id].static = scrolls[id].static + add

    end

end



local previewkey = 999

local actualbind = nil

local rbind, gbind, bbind = overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b

function interact.standardbutton(text, x, y, func)

    local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

    x,y = x+Loader_X, y+Loader_Y

    DrawSprite("psycho-button","psycho-button", x+0.082, y, 0.1, 0.6, 0, 15, 15, 15, math.ceil(overlay.opacitys.contents))

    texts.drawTextColor(text, x, y-0.012, false, true, 0.27, 11 , 255, 255, 255, math.ceil(overlay.opacitys.contents))

    if mousefunctions.CursorZone(x,y,0.14,0.026) then

        DrawSprite("psycho-button","psycho-button", x, y, 0.53, 0.65, 0, 17, 17, 17, math.ceil(overlay.opacitys.contents))

        if IsDisabledControlJustPressed(0, 24) then

            func()

            return true

        end

    else

        DrawSprite("psycho-button","psycho-button", x, y, 0.53, 0.65, 0, 15, 15, 15, math.ceil(overlay.opacitys.contents))

    end



    if mousefunctions.CursorZone(x+0.082,y,0.035,0.03) then

        actualbind = text

        if interact.binding ~= text then

            if actualbind == text then

        DrawSprite("keyboard","keyboard", x+0.082, y, 0.23, 0.3, 0, 80, 80, 80, math.ceil(overlay.opacitys.contents))

            end

        end



        if IsDisabledControlJustPressed(0, 24) then

            if not binds.buttons[text] then

                binds.buttons[text] = {text = "...", bool = true, value = 999, func = func, textopacity = 0}

            end



            binds.buttons[text].textopacity = 0

            binds.buttons[text].func = func

            previewkey = 999

            interact.binding = text

            binds.buttons[text].bool = true 



        end 

    else

        if actualbind == text then

            rbind, gbind, bbind = overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b

        end

        if interact.binding ~= text then

        DrawSprite("keyboard","keyboard", x+0.082, y, 0.23, 0.3, 0, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.contents))

        end

    end





    -- bind system

    if interact.binding == text then

    if binds.buttons[text] then

        if binds.buttons[text].bool then

        DisableAllControlActions()

        binds.buttons[text].textopacity = anim.Lerp(binds.buttons[text].textopacity, 255, 0.020)

        texts.drawTextColor(binds.buttons[text].text, x+0.1, y-0.012, false, true, 0.32, 6, 255, 255, 255, math.ceil(binds.buttons[text].textopacity))



        --write key

        local textFunc = text

        for text, key in pairs(keysinput) do

            if IsDisabledControlJustPressed(0, key) then

                binds.buttons[textFunc].text = string.upper(text)

                previewkey = key

            end

        end



        --sucess binded

        if IsDisabledControlJustPressed(0, 191) then

            binds.buttons[text].value = previewkey

            binds.buttons[text].bool = false

            interact.binding = false

        end



        if IsDisabledControlJustPressed(0, 322) or IsDisabledControlJustPressed(0, 177) then

            interact.binding = false

            binds.buttons[text].value = 999

            binds.buttons[text].text = "..."

            binds.buttons[text].bool = false

        end

    end

end

end

end



local Invoken = Citizen.InvokeNative

local props_IDHSOGLFDSKGDUHIOSSD = {

    "prop_bumper_01",

    "prop_bumper_02",

    "prop_bumper_03",

    "prop_bumper_04",

    "prop_bumper_05",

    "prop_bumper_06",

}



local function RequestControlOnce(entity)

    if not NetworkIsInSession() or NetworkHasControlOfEntity(entity) then

        return true

    end

    SetNetworkIdCanMigrate(NetworkGetNetworkIdFromEntity(entity), true)

    return NetworkRequestControlOfEntity(entity)

end



function interact.PlayerButton(text, x, y, outline,r,g,b)

    local cursor_x, cursor_y = GetNuiCursorPosition()

    local widht, height = GetActiveScreenResolution()

    cursor_x = cursor_x / widht

    cursor_y = cursor_y / height

    local text = text

    if

    ((cursor_x) + 0.08 >= x + to_add_X and (cursor_x) - 0.1 <= x + to_add_X and (cursor_y) >= y + to_add_Y and

    (cursor_y) - 0.02 <= y + to_add_Y)

    then

        texts.drawTextColor(text, x + to_add_X - 0.074, y + to_add_Y - 0.005, outline, false, 0.3, 11, r,g,b,math.ceil(overlay.opacitys.contents))

    else

        texts.drawTextColor(text, x + to_add_X - 0.074, y + to_add_Y - 0.005, outline, false, 0.3, 11, r,g,b,math.ceil(overlay.opacitys.contents))

    end

    if

        ((cursor_x) + 0.08 >= x + to_add_X and (cursor_x) - 0.1 <= x + to_add_X and (cursor_y) >= y + to_add_Y and

            (cursor_y) - 0.02 <= y + to_add_Y and

            IsDisabledControlJustReleased(0, 92))

    then

        return true

    else

        return false

    end

 end

local function RotationToDirection(rotation)

    local retz = math.rad(rotation.z)

    local retx = math.rad(rotation.x)

    local absx = math.abs(math.cos(retx))

    return vector3(-math.sin(retz) * absx, math.cos(retz) * absx, math.sin(retx))

end











local currenttoggle = nil

local togglex = 0.061

local toggley = 0.046

local animvelocity = 0.050



function interact.togglebox(bool, text, x, y, func)

    local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

    local x,y = x+Loader_X, y+Loader_Y

    



    DrawSprite("toggle-set","toggle-set", x+0.075, y, 1.0, 1.0, 0, 20, 20, 20, math.ceil(overlay.opacitys.contents))



    if mousefunctions.CursorZone(x-0.043,y+0.01,0.05,0.015) or mousefunctions.CursorZone(x+0.085,y+0.01,0.03,0.02) then

        if IsDisabledControlJustPressed(0, 24) then 

            currenttoggle = text

            disableanim = false

            func()

            return true

         end



         if IsDisabledControlJustPressed(0, 25) then 

            cx, cy = mousefunctions.getCursorPosition()

            overlay.opacitys.togglebind = 0 

            if not binds.toggles[text] then

                binds.toggles[text] = {text = "", bool = true, value = 999, func = func, textopacity = 0, texttoggle = text}

            end

            binds.toggles[text].texttoggle = text

            binds.toggles[text].textopacity = 0

            binds.toggles[text].func = func

            previewkey = 999

            binds.toggles[text].bool = true 

            binding = true

            currenttoggle = text

         end

    end



    if bool then

        

        if currenttoggle == text then

            togglex = anim.Lerp(togglex, 0.071, animvelocity)

        end



        if currenttoggle ~= text then

            texts.drawTextColor(text, x-0.07, y-0.005, false, false, 0.28, 11, 255, 255, 255, math.ceil(overlay.opacitys.contents))

            texts.drawTextColor("•",x+0.071,y-0.046,false, false, 1.80,6, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.contents))

        elseif not disableanim then

            texts.drawTextColor(text, x-0.07, y-0.005, false, false, 0.28, 11, 255, 255, 255, math.ceil(overlay.opacitys.contents))

            texts.drawTextColor("•",x+togglex,y-toggley,false, false, 1.80,6, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.contents))

        else

            texts.drawTextColor(text, x-0.07, y-0.005, false, false, 0.28, 11, 255, 255, 255, math.ceil(overlay.opacitys.contents))

            texts.drawTextColor("•",x+0.071,y-0.046,false, false, 1.80,6, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.contents))

        end

    else

        if currenttoggle == text then

            togglex = anim.Lerp(togglex, 0.061, animvelocity)

        end



        if currenttoggle ~= text then

            texts.drawTextColor(text, x-0.07, y-0.005, false, false, 0.28, 11, 200, 200, 200, math.ceil(overlay.opacitys.contents))

            texts.drawTextColor("•",x+0.061,y-0.046,false, false, 1.80,6, 100, 100, 100, math.ceil(overlay.opacitys.contents))

        elseif not disableanim then

            texts.drawTextColor(text, x-0.07, y-0.005, false, false, 0.28, 11, 200, 200, 200, math.ceil(overlay.opacitys.contents))

            texts.drawTextColor("•",x+togglex,y-0.046,false, false, 1.80,6, 100, 100, 100, math.ceil(overlay.opacitys.contents))

        else

            texts.drawTextColor(text, x-0.07, y-0.005, false, false, 0.28, 11, 200, 200, 200, math.ceil(overlay.opacitys.contents))

            texts.drawTextColor("•",x+0.061,y-0.046,false, false, 1.80,6, 100, 100, 100, math.ceil(overlay.opacitys.contents))

        end

    end



    if binding then

        if currenttoggle == text and binds.toggles[text] then

            if binds.toggles[text].bool then

            DisableAllControlActions()



            overlay.opacitys.togglebind = anim.Lerp(overlay.opacitys.togglebind, 255, 0.020)



        --write key

        local textFunc = text

        for text, key in pairs(keysinput) do

            if IsDisabledControlJustPressed(0, key) then

                binds.toggles[textFunc].text = string.upper(text)

                previewkey = key

            end

        end



        --sucess binded

        if IsDisabledControlJustPressed(0, 191) then

            binds.toggles[text].value = previewkey

            binds.toggles[text].bool = false

            interact.binding = false

        end





            if overlay.opacitys.main > 240 then

            DrawSprite("psycho-button","psycho-button", cx+0.082, cy+0.022, 0.15, 0.7, 0, 15, 15, 15, math.ceil(overlay.opacitys.togglebind))



            if binds.toggles[text].text == "" then

                DrawSprite("keyboard","keyboard", cx+0.082, cy+0.022, 0.3, 0.37, 0, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.togglebind))

            else

                texts.drawTextColor(binds.toggles[text].text, cx+0.082, cy+0.01, false, true, 0.27, 11, 255, 255, 255, math.ceil(overlay.opacitys.togglebind))

            end

            end





        if IsDisabledControlJustPressed(0, 322) then

            binds.toggles[text].bool = false

            binding = false

            binds.toggles[text].value = 999

            binds.toggles[text].text = ""

        end



    end

            

        end

        

    end



end



--callback

local playerson = {}

local vehlist = {}

callfunc = 

{

    searchOptions = function ()

        

    end,



    updatePlayerList = function()

        Citizen.CreateThread(function ()

            while true do

                if psychovars.main.tab == "players" then

                local activePlayers = GetActivePlayers()

                local playercoords = GetEntityCoords(PlayerPedId())

                playerson = {}

    

                for _, player in ipairs(activePlayers) do

                    local playerName = GetPlayerName(player)

                        local targetcoords = GetEntityCoords(GetPlayerPed(player))  -- Coordenadas do jogador de destino

                        local distance = GetDistanceBetweenCoords(playercoords, targetcoords, true)  -- Distância entre o jogador local e o jogador de destino

                        table.insert(playerson, {player = player, distance = distance})

                        

                end

    

    

                table.sort(playerson, function(a, b)

                    return a.distance < b.distance

                end)

            end



                     --verify current players

                 for k, player in pairs(playersselected) do

                    local playerCoords = GetEntityCoords(GetPlayerPed(player))

                    local selfCoords = GetEntityCoords(PlayerPedId())

                    local distance = GetDistanceBetweenCoords(selfCoords, playerCoords, false)

                    if distance > listVariables.distanceLimit then

                        table.remove(playersselected, k)

                    end

                 end

                Wait(2000)

        end

        end)

    end,



    callWeaponsList = function ()

        local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

        texts.drawTextColor("Lista Spawn de Armas", 0.55+Loader_X, 0.37+Loader_Y-0.03, false, false, 0.32, 11, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.contents))

        local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

         local dW = psychovars.list.MesosnuW - 0.5

         local dH = psychovars.list.MesosnuH - 0.424

         local y = 0.285 + scrolls['weaponList'].static

         local add = 0.022

         local max = 0.6

         if IsDisabledControlPressed(0,36) and IsDisabledControlJustPressed(0,34) then

            weaponsSelected = {}

            for index, weapon in ipairs(weaponList) do

                table.insert(weaponsSelected,weapon.hash)

            end

         end



         if IsDisabledControlPressed(0,36) and IsDisabledControlJustPressed(0,177) then

            weaponsSelected = {}

         end

         



        if IsDisabledControlPressed(0, 14) and y > (0.355 - (25 * add)) and mousefunctions.mouse(0.63+Loader_X, 0.46+Loader_Y, 0.165, 0.25) then

            scrolls["weaponList"].static = scrolls["weaponList"].static - add

        end

        if IsDisabledControlJustPressed(0, 15) and y ~= 0.355 and mousefunctions.mouse(0.63+Loader_X, 0.46+Loader_Y, 0.165, 0.25) then

            scrolls["weaponList"].static = scrolls["weaponList"].static + add

        end



         

         for index, weapon in ipairs(weaponList) do

            local r,g,b = 255,255,255

            local selected = false

            local txtdraw = weapon.name

            for _, arma in ipairs(weaponsSelected) do

                if arma == weapon.hash then

                    r,g,b = overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b

                    selected = true

                    txtdraw = "• "..weapon.name

                end

            end



             if y >= 0.4 and y <= max then

                    if interact.PlayerButton(txtdraw, 0.445+Loader_X, y - 0.05+Loader_Y, false, r,g,b) then

                        if selected then

                            for i, arma in ipairs(weaponsSelected) do

                                if arma == weapon.hash then

                                    table.remove(weaponsSelected, i)

                                end

                            end

                        else

                            table.insert(weaponsSelected,weapon.hash)

                        end

                     end    

             end

         

             y = y + add

         end

    end,

    

    callSpawnVehicleList = function ()

        local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

        texts.drawTextColor("Lista Spawn de Veículos", 0.55+Loader_X, 0.37+Loader_Y-0.03, false, false, 0.32, 11, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, math.ceil(overlay.opacitys.contents))

        local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

         local dW = psychovars.list.MesosnuW - 0.5

         local dH = psychovars.list.MesosnuH - 0.424

         local y = 0.295 + scrolls['vehicleSpawnList'].static

         local add = 0.03

         local max = 0.6



         if IsDisabledControlPressed(0,36) and IsDisabledControlJustPressed(0,177) then

            vehicleSelected = nil

         end

         



         if IsDisabledControlPressed(0, 14) and y > (0.355 - (25 * add)) and mousefunctions.mouse(0.63+Loader_X, 0.46+Loader_Y, 0.165, 0.25) then

            scrolls["vehicleSpawnList"].static = scrolls["vehicleSpawnList"].static - add

        end

        if IsDisabledControlJustPressed(0, 15) and y ~= 0.355 and mousefunctions.mouse(0.63+Loader_X, 0.46+Loader_Y, 0.165, 0.25) then

            scrolls["vehicleSpawnList"].static = scrolls["vehicleSpawnList"].static + add

        end



         

         for index, vehicle in ipairs(vehicleListSpawn) do

            local r,g,b = 255,255,255

            local txtdraw = vehicle.name

            if vehicleSelected == vehicle.hash then

                    r,g,b = overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b

                    txtdraw = "• "..vehicle.name

            end



             if y >= 0.4 and y <= max then

                    if interact.PlayerButton(txtdraw, 0.445+Loader_X, y - 0.05+Loader_Y, false, r,g,b) then

                        if vehicleSelected == vehicle.hash then

                            vehicleSelected = nil

                        else

                            vehicleSelected = vehicle.hash

                        end

                     end    

             end

         

             y = y + add

         end

    end,



    updateVehicleList = function()

        Citizen.CreateThread(function ()

            while true do

                if psychovars.main.tab == "vehicles" then

                local activeVehicles = GetAllVeh()

                local playercoords = GetEntityCoords(PlayerPedId())

                vehlist = {}

    

                for k, vehicle in ipairs(activeVehicles) do

                        local modelName = GetDisplayNameFromVehicleModel(GetEntityModel(vehicle))

                        if modelName ~= "FREIGHT" and modelName ~= "CARNOTFOUND" then

                        local targetcoords = GetEntityCoords(vehicle) 

                        local distance = GetDistanceBetweenCoords(playercoords, targetcoords, true)

                        table.insert(vehlist, {vehicle = vehicle, distance = distance})

                        end

                        

                end

    

                    table.sort(vehlist, function(a, b)

                        return a.distance < b.distance

                    end)

            end



                 --verify current vehicles

                 for k, vehicle in pairs(vehiclesSelected) do

                    local vehCoords = GetEntityCoords(vehicle)

                    local selfCoords = GetEntityCoords(PlayerPedId())

                    local distance = GetDistanceBetweenCoords(selfCoords, vehCoords, false)

                    if distance > listVariables.distanceLimit then

                        table.remove(vehiclesSelected, k)

                    end

                 end



                Wait(2000)

        end

        end)

    end,



    menuscheck = function ()

        -- Ped Entities

        local ymenu = 0.361

        local yadd = 0.038



        ymenu = ymenu + yadd

        if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "self" then

            overlay.opacitys.contents = 0

            end

            psychovars.main.tab = "self"

            overlay.anim.tabpos.xdestin = 0.31

            overlay.anim.tabpos.ydestin = ymenu

        end



        ymenu = ymenu + yadd -0.003

        if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "players" then

            overlay.opacitys.contents = 0

            end

            psychovars.main.tab = "players"

            overlay.anim.tabpos.xdestin = 0.31

            overlay.anim.tabpos.ydestin = ymenu

        end



        -- Weapons



        local ymenu = 0.452

        local yadd = 0.03

        

        ymenu = ymenu + yadd

        if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "weapon" then

            overlay.opacitys.contents = 0

            end

            psychovars.main.tab = "weapon"

            overlay.anim.tabpos.xdestin = 0.31

            overlay.anim.tabpos.ydestin = ymenu

        end



        ymenu = ymenu + yadd

        if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "aimbot" then

            overlay.opacitys.contents = 0

            end

            psychovars.main.tab = "aimbot"

            overlay.anim.tabpos.xdestin = 0.31

            overlay.anim.tabpos.ydestin = ymenu

        end



        -- Vehicle Entities



        local ymenu = 0.525

        local yadd = 0.03

        

        ymenu = ymenu + yadd

        if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "vehicle" then

                overlay.opacitys.contents = 0

            end

            psychovars.main.tab = "vehicle"

            overlay.anim.tabpos.xdestin = 0.31

            overlay.anim.tabpos.ydestin = ymenu

        end



        ymenu = ymenu + yadd

        if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "vehicles" then

                overlay.opacitys.contents = 0

            end

            psychovars.main.tab = "vehicles"

            overlay.anim.tabpos.xdestin = 0.31

            overlay.anim.tabpos.ydestin = ymenu

        end



         -- Visual



         local ymenu = 0.615

         local yadd = 0.025

         

         ymenu = ymenu + yadd

         if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "visual" then

                overlay.opacitys.contents = 0

            end

             psychovars.main.tab = "visual"

             overlay.anim.tabpos.xdestin = 0.31

             overlay.anim.tabpos.ydestin = ymenu

         end



         -- Outhers



         local ymenu = 0.66

         local yadd = 0.031

         

         ymenu = ymenu + yadd

         if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "trolloptions" then

                overlay.opacitys.contents = 0

            end

             psychovars.main.tab = "trolloptions"

             overlay.anim.tabpos.xdestin = 0.31

             overlay.anim.tabpos.ydestin = ymenu

         end



         ymenu = ymenu + yadd

         if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "exploits" then

                overlay.opacitys.contents = 0

            end

             psychovars.main.tab = "exploits"

             overlay.anim.tabpos.xdestin = 0.31

             overlay.anim.tabpos.ydestin = ymenu

         end



         ymenu = ymenu + yadd

         if interact.invisiblebutton(0.31, ymenu, 0.062, 0.012) then

            if psychovars.main.tab ~= "config" then

                overlay.opacitys.contents = 0

            end

             psychovars.main.tab = "config"

             overlay.anim.tabpos.xdestin = 0.31

             overlay.anim.tabpos.ydestin = ymenu

         end

    end,



    interactions = function ()

        if psychovars.main.tab == "self" then



            local yvalue = 0.32+scrolls["self"].static

            local y2value = 0.3+scrolls["self"].static

            local addbutton = 0.045

            local addbutton2 = 0.030

            local max = 0.76

            interact.Scroll(10, "self")



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Reviver", 0.424, yvalue, function ()

                    local x,y,z = table.unpack(GetEntityCoords(PlayerPedId()))

                    NetworkResurrectLocalPlayer(x,y,z,GetEntityHeading(PlayerPedId()),true,false)

                    ClearPedBloodDamage(PlayerPedId())

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Curar", 0.424, yvalue, function ()

                    --SetEntityHealth(PlayerPedId(), 200)



                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Colete", 0.424, yvalue, function ()

                    local Tunnel = module("vrp", "lib/Tunnel")

                    local Proxy = module("vrp", "lib/Proxy")

                    local Tools = module("vrp", "lib/Tools")

                    vRP = Proxy.getInterface("vRP")

                    vRP.setArmour(100)

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Morrer", 0.424, yvalue, function ()

                    SetEntityHealth(PlayerPedId(), 0)

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Algemar/Desalgemar", 0.424, yvalue, function ()

                    local Tunnel = module("vrp", "lib/Tunnel")

                    local Proxy = module("vrp", "lib/Proxy")

                    local Tools = module("vrp", "lib/Tools")

                    vRP = Proxy.getInterface("vRP")

                    vRP.toggleHandcuff()

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Colocar/Remover Capuz", 0.424, yvalue, function ()

                    local Tunnel = module("vrp", "lib/Tunnel")

                    local Proxy = module("vrp", "lib/Proxy")

                    local Tools = module("vrp", "lib/Tools")

                    vRP = Proxy.getInterface("vRP")

                    vRP.toggleCapuz()

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Desgrudar do Adm", 0.424, yvalue, function ()

                    if not IsPedInAnyVehicle(PlayerPedId()) then

                        if IsEntityAttached(PlayerPedId()) then

                            DetachEntity(PlayerPedId(-1),true,false)

                            TriggerEvent("vrp_policia:tunnel_req", "arrastar", {}, "vrp_policia", -1)

                        end

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Limpar Ferimentos", 0.424, yvalue, function ()

                    ClearPedBloodDamage(PlayerPedId())

                end)

            end

            



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.r3v1v3rm0rr3, "Reviver ao Morrer", 0.43, yvalue, function ()

                    healthmodule.r3v1v3rm0rr3 = not healthmodule.r3v1v3rm0rr3

                    local p333dd = PlayerPedId()

                    Citizen.CreateThread(function()

                        while healthmodule.r3v1v3rm0rr3 do

                            if GetEntityHealth(p333dd) < 102 then

                                local x,y,z = table.unpack(GetEntityCoords(PlayerPedId()))

                                NetworkResurrectLocalPlayer(x,y,z,GetEntityHeading(PlayerPedId()),true,false)

                                ClearPedBloodDamage(PlayerPedId())

                                Citizen.Wait(1000)

                            end

                            Citizen.Wait(2000)

                        end

                    end)

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.godmode, "GodMode", 0.43, yvalue, function ()

                    healthmodule.godmode = not healthmodule.godmode

                    if not healthmodule.godmode and cityAC == "PLPROTECT" then

                        print('GODMODE PL-PROTECT OFF.')

                        SetPedCanRagdoll(PlayerPedId(), true)

                    elseif not healthmodule.godmode then

                        SetEntityOnlyDamagedByRelationshipGroup(PlayerPedId(), false, 30131)

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.antitaze, "Anti Tazer", 0.43, yvalue, function ()

                    healthmodule.antitaze = not healthmodule.antitaze

                    if healthmodule.antitaze then

                        SetPedMinGroundTimeForStungun(PlayerPedId(), 0)

                    elseif not healthmodule.antitaze then

                        SetPedMinGroundTimeForStungun(PlayerPedId(), 3600)

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.ragd0ll, "No Ragdoll", 0.43, yvalue, function ()

                    healthmodule.ragd0ll = not healthmodule.ragd0ll

                    local ped = PlayerPedId()

                    if healthmodule.ragd0ll then

                        SetPedCanRagdoll(PlayerPedId(), false)

                        SetPedRagdollOnCollision(ped, false)

                        SetPedRagdollBlockingFlags(ped, 0)

                        SetPedRagdollBlockingFlags(ped, 0)

                    elseif not healthmodule.ragd0ll then

                        SetPedCanRagdoll(PlayerPedId(), true)

                        SetPedRagdollOnCollision(ped, true)

                        SetPedRagdollBlockingFlags(ped, 1)

                        SetPedRagdollBlockingFlags(ped, 1)

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.afog4do, "Não Morrer Afogado", 0.43, yvalue, function ()

                    healthmodule.afog4do = not healthmodule.afog4do

                    if not healthmodule.afog4do then

                        SetPedMaxTimeUnderwater(PlayerPedId(), 10)

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.s0c4o, "Super Soco", 0.43, yvalue, function ()

                    healthmodule.s0c4o = not healthmodule.s0c4o

                    local mud4nc4d4m4g3 = SetWeaponDamageModifierThisFrame

                    local p3g4p3g4 = GetHashKey

                    if not healthmodule.s0c4o then

                        mud4nc4d4m4g3(p3g4p3g4('weapon_unarmed'), 1.0)  

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.st4m1n3, "Stamina Infinita", 0.43, yvalue, function ()

                    healthmodule.st4m1n3 = not healthmodule.st4m1n3

                    if not healthmodule.st4m1n3 then

                        RestorePlayerStamina(PlayerId(), GetPlayerSprintStaminaRemaining(PlayerId()))

                    end

                end)

            end







            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.na0soc0, "Não Tomar Soco", 0.43, yvalue, function ()

                    healthmodule.na0soc0 = not healthmodule.na0soc0

                    if healthmodule.na0soc0 then

                        local ply333r111d = PlayerPedId()

                        SetPedCanBeTargetted(ply333r111d, false)

                    else

                        SetPedCanBeTargetted(ply333r111d, true)

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.f4nt4sm4m0d3, "Modo Fantasma", 0.43, yvalue, function ()

                    healthmodule.f4nt4sm4m0d3 = not healthmodule.f4nt4sm4m0d3

                    if healthmodule.f4nt4sm4m0d3 then

                        SetLocalPlayerAsGhost(true)

                    else

                        SetLocalPlayerAsGhost(false)

                    end 

                end)

            end







            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.n0rop3, "Não ser Carregado", 0.43, yvalue, function ()

                    healthmodule.n0rop3 = not healthmodule.n0rop3

                    Citizen.CreateThread(function()

                        while healthmodule.n0rop3 do

                            if healthmodule.n0rop3 then

                                if not IsPedInAnyVehicle(PlayerPedId()) then

                                    if IsEntityAttached(PlayerPedId()) then

                                        DetachEntity(PlayerPedId(-1),true,false)

                                        TriggerEvent("vrp_policia:tunnel_req", "arrastar", {}, "vrp_policia", -1)

                                    end

                                end

                            end

                            Citizen.Wait(500)

                        end

                    end)

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.r0d44rm4s, "Liberar Tab", 0.43, yvalue, function ()

                    healthmodule.r0d44rm4s = not healthmodule.r0d44rm4s

                end)

            end



            -- yvalue = yvalue + addbutton2

            -- if yvalue >= 0.34 and yvalue <= max then

            --     interact.togglebox(healthmodule.beastJump, "Pulo Animal", 0.43, yvalue, function ()

            --         healthmodule.beastJump = not healthmodule.beastJump

            --         beastJump(player)

            --     end)

            -- end

            



            -- PARTE DA ESQUERDA (MOVIMENTOS)



            yvalue = 0.32+scrolls["self"].static + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Teleport Waypoint", 0.615, yvalue, function ()

                    cdsmodule.tpway()

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.inv1s1bl3, "Invisivel", 0.622, yvalue, function ()

                    healthmodule.inv1s1bl3 = not healthmodule.inv1s1bl3

                    if not healthmodule.inv1s1bl3 then 

                        SetEntityVisible(GetVehiclePedIsIn(PlayerPedId(), 0), true, true)

                        SetEntityVisible(PlayerPedId(), true)

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.v0nc, "Noclip", 0.622, yvalue, function ()

                    healthmodule.v0nc = not healthmodule.v0nc

                end)

            end

            yvalue = yvalue + 0.01

            if yvalue >= 0.34 and yvalue <= max then

                interact.Slider("n0clip", 0.631, yvalue, 1, 0.09)

            end



            yvalue = yvalue + addbutton2 - 0.005

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.at77av3ssarpar3d, "Atravessar Paredes", 0.622, yvalue, function ()

                    healthmodule.at77av3ssarpar3d = not healthmodule.at77av3ssarpar3d

                    if healthmodule.at77av3ssarpar3d then

                        Citizen.CreateThread(function()

                            local pl43r1d = PlayerPedId()

                            while healthmodule.at77av3ssarpar3d do

                                SetPedCapsule(pl43r1d, 0.0001)

                                Wait(0)

                            end

                        end)

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.f4strun, "Correr Rápido", 0.622, yvalue, function ()

                    healthmodule.f4strun = not healthmodule.f4strun

                    local sp3edrun = Sliders['fastrun'].value 

                    if not healthmodule.f4strun then

                        SetPedCanRagdoll(PlayerPedId(), true)

                        SetRunSprintMultiplierForPlayer(PlayerId(), 1.0)

                    end

                end)

            end



            yvalue = yvalue + 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.Slider("fastrun", 0.650, yvalue, 1, 0.06)

            end





            yvalue = yvalue + addbutton2 - 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.antadm, "Anti Staff", 0.622, yvalue, function ()

                    healthmodule.antadm = not healthmodule.antadm

                end)

            end



            yvalue = yvalue + 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.Slider("n0st4ff", 0.645, yvalue, 1, 0.07)

            end



            yvalue = yvalue + addbutton2 - 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(healthmodule.s4po, "Super Pulo", 0.622, yvalue, function ()

                    healthmodule.s4po = not healthmodule.s4po

                end)

            end

            yvalue = yvalue + 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.Slider("s4populo", 0.645, yvalue, 1, 0.07)

            end







            

        elseif psychovars.main.tab == "weapon" then

            callfunc.callWeaponsList()            



            local yvalue = 0.32+scrolls["weapon"].static

            local addbutton = 0.045

            local addbutton2 = 0.030

            local max = 0.76

            interact.Scroll(5, "weapon")



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Spawnar Armas Selecionadas", 0.424, yvalue, function ()

                    if groupcity == "NEXUS" then

                        if #weaponsSelected > 0 then

                            for i, weapon in ipairs(weaponsSelected) do 

                                weaponmodule2.Spawn(weapon)

                            end

                        end

                    elseif groupcity == "HYPE" or cityAC == "PLPROTECT" then

                        if #weaponsSelected > 0 then

                            for i, weapon in ipairs(weaponsSelected) do 

                                weaponmodule3.Spawn(weapon)

                            end

                        end

                    else

                        if #weaponsSelected > 0 then

                            for i, weapon in ipairs(weaponsSelected) do 

                                weaponmodule.Spawn(weapon)

                            end

                        end

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Remover Armas", 0.424, yvalue, function ()

                    RemoveAllPedWeapons(PlayerPedId())

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Setar Muni ~r~(250)", 0.424, yvalue, function ()

                    SetCurrentAmmo()

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Add Attachs", 0.424, yvalue, function ()

                    local p333dd = PlayerPedId()

                    local a7mm44 = GetSelectedPedWeapon(p333dd)

                    if GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_PISTOL_MK2") then

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_PI_RAIL"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_PI_FLSH_02"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_PI_SUPP_02"))

                    elseif GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_MACHINEPISTOL") then

                    elseif GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_SMG_MK2") then

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_AR_FLSH"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_SCOPE_SMALL_SMG_MK2"))

                    elseif GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_PUMPSHOTGUN") then

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_AR_FLSH"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_SR_SUPP"))

                    elseif GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_SMG") then

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_AR_FLSH"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_SCOPE_MACRO_02"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_PI_SUPP"))

                    elseif GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_ASSAULTRIFLE_MK2") or GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_CARBINERIFLE_MK2") or GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_SPECIALCARBINE_MK2") then

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_AR_AFGRIP_02"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_AR_FLSH"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_SCOPE_MEDIUM_MK2"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_MUZZLE_02"))

                    elseif GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_CARBINERIFLE") then

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_AR_FLSH"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_SCOPE_MEDIUM"))

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_AR_AFGRIP"))

                    elseif GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_COMBATPDW") then

                        GiveWeaponComponentToPed(p333dd,GetHashKey("WEAPON_COMBATPDW"),GetHashKey("COMPONENT_AT_AR_FLSH"))

                        GiveWeaponComponentToPed(p333dd,GetHashKey("WEAPON_COMBATPDW"),GetHashKey("COMPONENT_AT_SCOPE_SMALL"))

                        GiveWeaponComponentToPed(p333dd,GetHashKey("WEAPON_COMBATPDW"),GetHashKey("COMPONENT_AT_AR_AFGRIP"))

                    elseif GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_HEAVYPISTOL") or GetSelectedPedWeapon(p333dd) == GetHashKey("WEAPON_COMBATPISTOL") then

                        GiveWeaponComponentToPed(p333dd,a7mm44,GetHashKey("COMPONENT_AT_PI_FLSH"))

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Mudar Cor da Arma", 0.424, yvalue, function ()

                    SetPedWeaponTintIndex(PlayerPedId(), GetSelectedPedWeapon(PlayerPedId()), 2)

                end)

            end

--[[ 

            r11_0:Checkbox("Pintar arma em loop", "Altera a cor da sua arma em loop.", "weaponColorLoop", function(r0_123)

                -- line: [0, 0] id: 123

                if r0_123 then

                  while r11_0.toggles.weaponColorLoop do

                    SetPedWeaponTintIndex(PlayerPedId(), GetSelectedPedWeapon(PlayerPedId()), r11_0.sliders.weaponColor)

                    Wait(0)

                  end

                end

              end) ]]



            yvalue = yvalue + addbutton2 

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(cordaarmita, "Pintar arma em loop", 0.43, yvalue, function ()

                    cordaarmita = not cordaarmita  

                end)

            end



            yvalue = yvalue + addbutton2 

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(armitanamaozita, "Bugar Arma na Mão", 0.43, yvalue, function ()

                    armitanamaozita = not armitanamaozita  

                end)

            end



            yvalue = yvalue + addbutton2 

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(muniinfinita, "Munição Infinita", 0.43, yvalue, function ()

                    muniinfinita = not muniinfinita  

                end)

            end



            yvalue = yvalue + addbutton2 

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(noReload, "No Reload", 0.43, yvalue, function ()

                    noReload = not noReload 

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.Slider("SliderTest", 0.424, yvalue, 1, 0.09)

            end



        elseif psychovars.main.tab == "aimbot" then



            local yvalue = 0.32+scrolls["aimbot"].static

            local addbutton = 0.045

            local addbutton2 = 0.030

            local max = 0.76

            interact.Scroll(10, "aimbot")







            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(S1l3ntA1m, "Silent Aim", 0.43, yvalue, function ()

                    S1l3ntA1m = not S1l3ntA1m

                end)

            end



            yvalue = yvalue + 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.Slider("circulo", 0.45, yvalue, 1, 0.07)

            end







--[[             yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(A1mf00v3, "Mostrar FOV", 0.43, yvalue, function ()

                    A1mf00v3 = not A1mf00v3

                end)

            end ]]



            yvalue = yvalue + addbutton2 - 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(incluirnpcs, "Incluir Npcs", 0.43, yvalue, function ()

                    incluirnpcs = not incluirnpcs

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(R44g3b00t, "RageBot", 0.43, yvalue, function ()

                    R44g3b00t = not R44g3b00t

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(A11ml00ck3, "Aimlock", 0.43, yvalue, function ()

                    A11ml00ck3 = not A11ml00ck3

                end)

            end



            yvalue = yvalue + 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.Slider("Sm00th1ng", 0.44, yvalue, 1, 0.07)

            end



        elseif psychovars.main.tab == "players" then





            local yvalue = 0.32+scrolls["players"].static

            local addbutton = 0.045

            local addbutton2 = 0.030

            local max = 0.76

            interact.Scroll(30, "players")



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.textBox("searchPlayers", "", "Pesquisar Jogadores", 0.424, yvalue)

            end



            print(others.getTextBox("searchPlayers"))





            callfunc.callPlayersList()



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(spectar, "Spectar Player", 0.43, yvalue, function ()

                    if SelectedPlayer then

                        spectar = not spectar

                    end

                end)

            end



--[[             yvalue = yvalue + addbutton2



            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(nukeserv3r, "NUKE Player", 0.43, yvalue, function ()

                    if SelectedPlayer then

                        nukeserv3r = not nukeserv3r

                    end

                end)

            end

            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(nukeserv3r2, "NUKE Player2", 0.43, yvalue, function ()

                    if SelectedPlayer then

                        nukeserv3r2 = not nukeserv3r2

                    end

                end)

            end ]]



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Copiar Roupa", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        local r0_157 = GetPlayerPed(SelectedPlayer)

                        if DoesEntityExist(r0_157) and r0_157 ~= PlayerPedId() then

                            ClonePedToTarget(r0_157, PlayerPedId())

                        end

                        --Copiarroupa() DANDO BAN ESSA BOMBA

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Copiar Ped", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        copiarped()

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Teleport Player", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        local ped = GetPlayerPed(SelectedPlayer)

                        local pos = GetEntityCoords(ped)

                        SetPedCoordsKeepVehicle(PlayerPedId(), pos)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Teleport P2", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        PlaySoundFrontend(-1, "Faster_Click", "RESPAWN_ONLINE_SOUNDSET", true)

                        if not IsPedInAnyVehicle(GetPlayerPed(SelectedPlayer), 0) then

                            PlaySoundFrontend(-1, "Hack_Failed", "DLC_HEIST_BIOLAB_PREP_HACKING_SOUNDS", true)

                        else

                            local veh = GetVehiclePedIsIn(GetPlayerPed(SelectedPlayer), 0)

                            if IsVehicleSeatFree(veh, 0) then

                                SetPedIntoVehicle(PlayerPedId(), veh, 0)

                            elseif IsVehicleSeatFree(veh, 1) then

                                SetPedIntoVehicle(PlayerPedId(), veh, 1)

                            elseif IsVehicleSeatFree(veh, 2) then

                                SetPedIntoVehicle(PlayerPedId(), veh, 2)

                            elseif IsVehicleSeatFree(veh, 3) then

                                SetPedIntoVehicle(PlayerPedId(), veh, 3)

                            end

                        end

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Saquear Morto", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        revistarplayer()

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tazer no Player", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        local bonecoords2 = GetPedBoneCoords(GetPlayerPed(SelectedPlayer), 7900, 0.0, 0.0, 0.2)

                        local bonecoords = GetPedBoneCoords(GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086))

                        ShootSingleBulletBetweenCoords(bonecoords,bonecoords2,10,true,GetHashKey("WEAPON_STUNGUN"),PlayerPedId(),true,false,1)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Derrubar Player", 0.424, yvalue, function ()

                    Derrubar(SelectedPlayer)

                end)

            end





            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                --interact.togglebox(tptosky2, "Bugar Player", 0.43, yvalue, function ()

                interact.standardbutton("Bugar Player", 0.424, yvalue, function ()

                    tptosky = not tptosky

                    if tptosky and SelectedPlayer then

                        local ped = GetPlayerPed(SelectedPlayer) 

                        RequestModel(GetHashKey('ch_prop_ch_top_panel02'))

                        fok1 = CreateObject(GetHashKey('ch_prop_ch_top_panel02'), GetEntityCoords(ped),1,1,1) 

                        SetEntityVisible(fok1, false, 0)

                        NetworkSetEntityInvisibleToNetwork(fok1,true) 

                        AttachEntityToEntityPhysically(fok1, ped, 0,0, 0.0,-150.0,0.0, 0.0, 0.0, 0.0, 99999999999, 1, false, false, 1, 2)

                    else

                        NetworkRequestControlOfEntity(fok1)

                        DeleteEntity(fok1)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Freezar Player", 0.424, yvalue, function ()

                    freeze = not freeze

                    if freeze and SelectedPlayer then

                        local ped = GetPlayerPed(SelectedPlayer) 

                        RequestModel(GetHashKey('ch_prop_ch_top_panel02'))

                        fok1 = CreateObject(GetHashKey('ch_prop_ch_top_panel02'), GetEntityCoords(ped),1,1,1) 

                        SetEntityVisible(fok1, false, 0)

                        NetworkSetEntityInvisibleToNetwork(fok1,true) 

                        AttachEntityToEntityPhysically(fok1, ped, 0,0, 0.0,0.0,0.0, 0.0, 0.0, 0.0, 99999999999, 1, false, false, 1, 2)  

                    else

                        NetworkRequestControlOfEntity(fok1)

                        DeleteEntity(fok1)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tacar Fogo no Player", 0.424, yvalue, function ()

                    Explodir(3,SelectedPlayer)

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Gás player", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        Citizen.CreateThread(function()

                            local ped = GetPlayerPed(SelectedPlayer)

                            local x, y, z = table.unpack(GetEntityCoords(ped))

                            local bzGasGrenadeHash = GetHashKey("WEAPON_BZGAS")

                            RequestWeaponAsset(bzGasGrenadeHash)

                            while not HasWeaponAssetLoaded(bzGasGrenadeHash) do

                                Wait(500)

                            end                      

                            for i = 1, 3 do

                                local offsetX = math.random(-1, 1)

                                local offsetY = math.random(-1, 1)

                                ShootSingleBulletBetweenCoords(x + offsetX, y + offsetY, z, x + offsetX, y + offsetY, z + 0.1, 0, true, bzGasGrenadeHash, 0, true, false, -1.0)

                                Wait(100) 

                            end

                        end)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Assar", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        Citizen.CreateThread(function()

                            bypssaadd = SelectedPlayer

                            local x, y, z = table.unpack(GetEntityCoords(GetPlayerPed(bypssaadd)))

                            local ped = GetPlayerPed(bypssaadd)

                            local Hash = "gr_prop_gr_hobo_stove_01"

                            RequestModel(Hash)

                            while not HasModelLoaded(Hash) do

                                Wait(500)

                            end

                            Citizen.CreateThread(function()

                                local prop = CreateObject(Hash, x, y, z, true, true, true)

                                AttachEntityToEntity(prop, ped, 0, 0.0, 0.04, 0.0, 0.0, 12.0, 0.0, true, true, true, true, 0, true)

                                SetEntityAsNoLongerNeeded(prop)

                                SetModelAsNoLongerNeeded(prop)

                                Explodir(3,SelectedPlayer)

                            end)

                        end)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Spawn barreira", 0.424, yvalue, function()

                    SpawnBarreiras(GetPlayerPed(SelectedPlayer))

                end)

            end



            -- yvalue = yvalue + addbutton

            -- if yvalue >= 0.34 and yvalue <= max then

            --     interact.standardbutton("Derrubar Player2", 0.424, yvalue, function ()

            --         for _, player in ipairs(GetActivePlayers()) do

            --         DerrubarPlayer(player)

            --     end)

            -- end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Matar Player", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        local oldC00rdss3 = GetEntityCoords(PlayerPedId())

                        local pl3yerC00rds2 = GetEntityCoords(GetPlayerPed(SelectedPlayer))

    

                        SetEntityVisible(PlayerPedId(), false)

                        SetEntityCoordsNoOffset(PlayerPedId(), pl3yerC00rds2.x, pl3yerC00rds2.y, pl3yerC00rds2.z)

    

                        SetTimeout(2000, function()

                            SetEntityCoordsNoOffset(PlayerPedId(), oldC00rdss3.x, oldC00rdss3.y, oldC00rdss3.z)

                            SetEntityVisible(PlayerPedId(), true)

                        end)

    

                        SetTimeout(200, function()

                            local pl2y3rP3d = PlayerPedId()

                            local pl3ay3rC00rds = GetEntityCoords(pl2y3rP3d)

                            local ta7g3tp3d = GetPlayerPed(SelectedPlayer)

                            if not DoesEntityExist(ta7g3tp3d) then

                                return 

                            end

                            local t47g3tc00rds = GetEntityCoords(ta7g3tp3d)

                            local ta7g3tH3adB00n33 = GetPedBoneIndex(ta7g3tp3d, 31086) 

                            local bu113tsp31d = 500

    

                            SetPedShootsAtCoord(pl2y3rP3d, t47g3tc00rds.x, t47g3tc00rds.y, t47g3tc00rds.z, true)

    

                            local ta7g3tH3adC000rdsd = GetPedBoneCoords(ta7g3tp3d, ta7g3tH3adB00n33)

    

                            ShootSingleBulletBetweenCoords(pl3ay3rC00rds.x, pl3ay3rC00rds.y, pl3ay3rC00rds.z, ta7g3tH3adC000rdsd.x, ta7g3tH3adC000rdsd

                            .y, ta7g3tH3adC000rdsd.z, bu113tsp31d, true, GetHashKey("WEAPON_PISTOL_MK2"), pl2y3rP3d, true, false, -1.0, true)

    

                        end)

                    end

                end)

            end



            -- yvalue = yvalue + addbutton

            -- if yvalue >= 0.34 and yvalue <= max then

            --     interact.standardbutton("Explodir Player", 0.424, yvalue, function ()

            --         if SelectedPlayer then

            --             bypssaadd = SelectedPlayer

            --             local playerCds = GetEntityCoords(GetPlayerPed(bypssaadd))

            --             local x, y, z = table.unpack(playerCds)

            --             AddExplosion(x, y, z, 44, 100.0, false,false,false)

            --             Wait(2)

            --         end 

            --     end)

            -- end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Explodir Player Silent", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        local playerPed = GetPlayerPed(SelectedPlayer)

                        local playerCds = GetEntityCoords(playerPed)

                        local x, y, z = table.unpack(playerCds)

                        AddExplosion(x, y, z, 44, 100.0, false, true, false)

                        

                        Wait(2)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Chuva de Veículos", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        for Vehiclee in EnumerateVehicles() do 

                            chuvadeveiculos(Vehiclee,SelectedPlayer)

                        end

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tacar Veículos no Player", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        for Vehicles in EnumerateVehicles() do 

                            chuvadeveiculos2(Vehicles,SelectedPlayer)

                        end

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Grudar Veículos", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        for vehicles in EnumerateVehicles() do 

                            Grudarvehsinplayer()

                        end

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("11/9 No Player", 0.424, yvalue, function ()

                    Citizen.CreateThread(function()

                        if SelectedPlayer then

                            cb = "havok"

                            mhash = GetHashKey(cb)

                            if cb and IsModelValid(cb) and IsModelAVehicle(cb) then

                                    RequestModel(cb)

                                    RequestModel(mhash)

                                    while not HasModelLoaded(cb) do

                                    Wait(2000)

                                end

                                    local c00rdPl4y3r = GetEntityCoords(GetPlayerPed(SelectedPlayer))

                                    local x = c00rdPl4y3r.x

                                    local y = c00rdPl4y3r.y

                                    local z = c00rdPl4y3r.z

                                    local v3hh = CreateVehicle(mhash, x, y, z+20, 0, true, false)

                                    V3hhe = v3hh

                                    S3l3ct3dddV3icul0 = v3hh

                                    t1m33 = 0

                                    SetVehicleOnGroundProperly(v3hh)

                                    SetEntityAsMissionEntity(v3hh, true, true)

                                    SetVehicleRadioEnabled(v3hh, false)

                                    SetModelAsNoLongerNeeded(mhash)

            

                                    while t1m33 < 1000 do

                                        NetworkRequestControlOfEntity(v3hh)

                                        local c00rds = GetEntityCoords(GetPlayerPed(SelectedPlayer))

                                        local x = c00rds.x

                                        local y = c00rds.y

                                        local z = c00rds.z

                                        ApplyForceToEntity(v3hh, 3, 0.0, 0.0, -100.0, 0.0, 0.0, 0.0, 0, 0, 1, 1, 0, 1)

                                        t1m33 = t1m33 + 50

                                        Wait(45)

                                    end

            

                                local n33tV33hh = VehToNet(v3hh)

                                SetVehicleDirtLevel(v3hh,0.0)

                                SetEntitySomething(v3hh,true)

                                SetVehicleHasBeenOwnedByPlayer(v3hh,true)

                                SetNetworkIdExistsOnAllMachines(n33tV33hh,true)

                                local Coords = GetEntityCoords(PlayerPedId())

                                NetworkRequestControlOfEntity(S3l3ct3dddV3icul0)

                                SetVehicleUndriveable(S3l3ct3dddV3icul0,true)

                                SetVehicleBrake(S3l3ct3dddV3icul0,true)

                                SetEntityVisible(PlayerPedId(), false, false)

                                TaskWarpPedIntoVehicle(PlayerPedId(),S3l3ct3dddV3icul0, -1)

                                DeleteEntity(v3hh)

                                SetEntityCoordsNoOffset(PlayerPedId(),Coords, false, false, false)

                                SetEntityVisible(PlayerPedId(), true, true)

                            end

                        end

                    end)

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Bugar Veículo Player", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        Citizen.CreateThread(function()

                            bypssaadd = SelectedPlayer

                            local x, y, z = table.unpack(GetEntityCoords(GetPlayerPed(bypssaadd)))

                            local ped =  GetPlayerPed(bypssaadd)

                            local Hash = "w_ar_bullpuprifle_mag1"

                            RequestModel(Hash)

                                while not HasModelLoaded(Hash) do

                                    Wait(500)

                                end

                                Citizen.CreateThread(function()

                                local prop = CreateObject(Hash, x, y, z, true, true, true)

                                AttachEntityToEntity(prop, ped, 0, 0.0, 0.04, 0.0, 0.0, 12.0, 0.0, true, true, true, true, 0, true)

                                SetEntityAsNoLongerNeeded(prop)

                                SetModelAsNoLongerNeeded(prop)

                                end)

                            Citizen.Wait(7000)

                        end)

                        --end

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Busão Player", 0.424, yvalue, function ()

                    Citizen.CreateThread(function()

                        for i = 1, 15 do

                            x, y, z = table.unpack(GetEntityCoords(GetPlayerPed(SelectedPlayer)))

                            roundx = tonumber(string.format('%.2f', x))

                            roundy = tonumber(string.format('%.2f', y))

                            roundz = tonumber(string.format('%.2f', z))

                            local e7 = 'airbus'

                            local e8 = GetHashKey(e7)

                            RequestModel(e8)

                            while not HasModelLoaded(e8) do

                                Citizen.Wait(0)

                            end

                            local e9 = CreateObject(e8, roundx - 1.70, roundy - 1.70, roundz - 1.0, true, true, false)

                            local ea = CreateObject(e8, roundx + 1.70, roundy + 1.70, roundz - 1.0, true, true, false)

                            

                            SetEntityHeading(e9, -90.0)

                            SetEntityHeading(ea, 90.0)

                            

                            

                            SetEntityVisible(e9, false)

                            SetEntityVisible(ea, false)

                            

                            

                            FreezeEntityPosition(e9, false)

                            FreezeEntityPosition(ea, false)

                    

                            

                            Citizen.Wait(2000)

                            DeleteEntity(e9)

                            DeleteEntity(ea)

                    

                            Citizen.Wait(1000) 

                        end

                    end)

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Trollar Player", 0.424, yvalue, function ()

                    local g1 = CreateObject(GetHashKey('prop_parking_wand_01'), 0, 0, 0, true, true, true)

                    local g2 = CreateObject(GetHashKey('prop_parking_wand_01'), 0, 0, 0, true, true, true)

                    local g3 = CreateObject(GetHashKey('prop_parking_wand_01'), 0, 0, 0, true, true, true)

                    local g4 = CreateObject(GetHashKey('prop_parking_wand_01'), 0, 0, 0, true, true, true)

                    local g5 = CreateObject(GetHashKey('prop_parking_wand_01'), 0, 0, 0, true, true, true)

                    local g6 = CreateObject(GetHashKey('prop_parking_wand_01'), 0, 0, 0, true, true, true)

                    local g7 = CreateObject(GetHashKey('prop_parking_wand_01'), 0, 0, 0, true, true, true)

                    local g8 = CreateObject(GetHashKey('prop_parking_wand_01'), 0, 0, 0, true, true, true)

                    local g9 = CreateObject(GetHashKey('prop_parking_wand_01'), 0, 0, 0, true, true, true)



                    AttachEntityToEntity(g1,GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086),0.3000,0.0000,-0.0500,-9.9000,80.0000,-20.0000,true,true,false,true,1,true)

                    AttachEntityToEntity(g2,GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086),0.2600,0.0000,0.1300,0.0000,57.0000,-13.8800,true,true,false,true,1,true)

                    AttachEntityToEntity(g3,GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086),0.2900,-0.0400,-0.4100,-4.7391,-4.9900,7.0100,true,true,false,true,1,true)       

                    AttachEntityToEntity(g4,GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086),0.3200,-0.0400,-0.4100,0.0000,82.0000,0.0000,true,true,false,true,1,true)

                    AttachEntityToEntity(g5,GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086),0.2400,0.0000,0.2200,0.0000,103.0300,0.0000,true,true,false,true,1,true)

                    AttachEntityToEntity(g6,GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086),0.2200,0.0000,0.3600,0.0000,82.0000,0.0000,true,true,false,true,1,true)

                    AttachEntityToEntity(g7,GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086),0.1600,0.0000,0.3600,-0.0000,-6.0000,0.0000,true,true,false,true,1,true)

                    AttachEntityToEntity(g8,GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086),0.1900,0.0000,0.6000,0.0000,87.0000,0.0000,true,true,false,true,1,true)

                    AttachEntityToEntity(g9,GetPlayerPed(SelectedPlayer),GetPedBoneIndex(GetPlayerPed(SelectedPlayer), 31086),0.4800,0.0000,0.4300,0.0000,-8.0000,0.0000,true,true,false,true,1,true)

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Quebrar Motor", 0.424, yvalue, function ()

                    killengine(GetVehiclePedIsIn(GetPlayerPed(SelectedPlayer), true))

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Estourar Pneus", 0.424, yvalue, function ()

                    Pneus(GetVehiclePedIsIn(GetPlayerPed(SelectedPlayer), true))

                end)

            end

            



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tacar PROP", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        Citizen.CreateThread(function()

                            bypssaadd = SelectedPlayer

                            local x, y, z = table.unpack(GetEntityCoords(GetPlayerPed(bypssaadd)))

                            local ped =  GetPlayerPed(bypssaadd)

                            local Hash = "prop_barriercrash_04" 

                            RequestModel(Hash)

                                while not HasModelLoaded(Hash) do

                                    Wait(500)

                                end

                                Citizen.CreateThread(function()

                                local prop = CreateObject(Hash, x, y, z, true, true, true)

                                AttachEntityToEntity(prop, ped, 0, 0.0, 0.04, 0.0, 0.0, 12.0, 0.0, true, true, true, true, 0, true)

                                SetEntityAsNoLongerNeeded(prop)

                                SetModelAsNoLongerNeeded(prop)

                                end)

                            Citizen.Wait(7000)

                        end)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tug Player", 0.424, yvalue, function ()

                    local playerCoords = GetPlayerCoords()

                    if SelectedPlayer then

                        SpawnCargoplaneAtCoords2(SelectedPlayer)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Kamikaze", 0.424, yvalue, function()

                    if SelectedPlayer then

                        Citizen.CreateThread(function()

                            local name = "lazer"

                            local mhash = GetHashKey(name)

                

                            while not HasModelLoaded(mhash) do

                                RequestModel(mhash)

                                Citizen.Wait(0)

                            end

                

                            if HasModelLoaded(mhash) then

                                local ped = GetPlayerPed(SelectedPlayer) 

                                local coords = GetEntityCoords(ped)

                                local heading = GetEntityHeading(ped)

                

                                

                                local nveh1 = CreateVehicle(mhash, coords.x, coords.y, coords.z - 3, heading, true, false)

                                SetVehicleOnGroundProperly(nveh1)

                                SetVehicleNumberPlateText(nveh1, "PLACA1")

                                SetEntityAsMissionEntity(nveh1, true, true)

                                TaskWarpPedIntoVehicle(ped, nveh1, -1)

                                SetEntityVisible(nveh1, false, false)

                                Citizen.Wait(1000)

                

                                local nveh2 = CreateVehicle(mhash, coords.x, coords.y, coords.z + 30.0, heading, true, false)

                                SetVehicleOnGroundProperly(nveh2)

                                SetVehicleNumberPlateText(nveh2, "PLACA2")

                                SetEntityAsMissionEntity(nveh2, true, true)

                                TaskWarpPedIntoVehicle(ped, nveh2, -1)

                                SetEntityVisible(nveh2, false, false)

                                local force = vector3(0.0, 0.0, -500.0)

                                ApplyForceToEntity(nveh2, 1, force.x, force.y, force.z, 0.0, 0.0, 0.0, 0, false, true, true, false, true)

                

                                SetModelAsNoLongerNeeded(mhash)

                            end

                        end)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Acabou o Roleplay", 0.424, yvalue, function ()

                    if SelectedPlayer then

                        Citizen.CreateThread(function()

                            bypssaadd = SelectedPlayer

                            local x, y, z = table.unpack(GetEntityCoords(GetPlayerPed(bypssaadd)))

                            local ped =  GetPlayerPed(bypssaadd)

                            local Hash = "dt1_lod_slod3" 

                            RequestModel(Hash)

                                while not HasModelLoaded(Hash) do

                                    Wait(500)

                                end

                                Citizen.CreateThread(function()

                                local prop = CreateObject(Hash, x, y, z, true, true, true)

                                AttachEntityToEntity(prop, ped, 0, 0.0, 0.04, 0.0, 0.0, 12.0, 0.0, true, true, true, true, 0, true)

                                SetEntityAsNoLongerNeeded(prop)

                                SetModelAsNoLongerNeeded(prop)

                                end)

                            Citizen.Wait(7000)

                        end)

                    end

                end)

            end







        elseif psychovars.main.tab == "vehicle" then

            callfunc.callSpawnVehicleList()





            local yvalue = 0.32+scrolls["vehicle"].static

            local addbutton = 0.045

            local addbutton2 = 0.030

            local max = 0.76

            interact.Scroll(12, "vehicle")



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Spawnar Veículo Selecionado", 0.424, yvalue, function ()

                    if vehicleSelected then

                        vehiclemodule.Spawn(vehicleSelected, GetEntityCoords(PlayerPedId()))

                    end 

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Lista dos Veículos ~r~[F8]", 0.424, yvalue, function ()

                    local v333h1cl33Nam33x = ""

                    for i = 1, #v3111cul00sl11st do

                        if IsModelValid(v3111cul00sl11st[i]) and IsModelAVehicle(v3111cul00sl11st[i]) then

                            v333h1cl33Nam33x = v333h1cl33Nam33x .. v3111cul00sl11st[i] .. "\n"

                        end

                    end

                    print(""..v333h1cl33Nam33x.."")

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Reparar Veículo", 0.424, yvalue, function ()

                    if IsPedInAnyVehicle(PlayerPedId()) then

                        SetVehicleOnGroundProperly(GetVehiclePedIsIn(PlayerPedId(), 0))

                        SetVehicleFixed(GetVehiclePedIsIn(PlayerPedId(), false))     

                        SetVehicleDirtLevel(GetVehiclePedIsIn(PlayerPedId(), false), 0.0)

                        SetVehicleLights(GetVehiclePedIsIn(PlayerPedId(), false), 0)

                        SetVehicleBurnout(GetVehiclePedIsIn(PlayerPedId(), false), false)

                        SetVehicleLightsMode(GetVehiclePedIsIn(PlayerPedId(), false), 0)

                    end

                end)

            end



            

            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tp Veículo Próximo", 0.424, yvalue, function ()

                    local vehicl3 = GetClosestVehicle(GetEntityCoords(PlayerPedId()), 8000.0, 0, 70)

                    if vehicl3 ~= nil then

                        SetPedIntoVehicle(PlayerPedId(), vehicl3, -1)

                    end

                    if IsPedInAnyVehicle(PlayerPedId()) then

                    end

                end)

            end



            

            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Destrancar Veículo Próximo", 0.424, yvalue, function ()

                    local v3h1cl3 = GetClosestVehicle(GetEntityCoords(PlayerPedId()), 25.0, 0, 70)

                    if DoesEntityExist(v3h1cl3) then

                            if DoesEntityExist(v3h1cl3) then

                            SetVehicleDoorsLocked(v3h1cl3, 1)

                            SetVehicleDoorsLockedForPlayer(v3h1cl3, PlayerId(), false)

                            SetVehicleDoorsLockedForAllPlayers(v3h1cl3, false)

                        end

                    end 

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Trancar Veículo Próximo", 0.424, yvalue, function ()

                    local v3h1cl3 = GetClosestVehicle(GetEntityCoords(PlayerPedId()), 25.0, 0, 70)

                    if DoesEntityExist(v3h1cl3) then

                            if DoesEntityExist(v3h1cl3) then

                            SetVehicleDoorsLocked(v3h1cl3, 1)

                            SetVehicleDoorsLockedForPlayer(v3h1cl3, PlayerId(), true)

                            SetVehicleDoorsLockedForAllPlayers(v3h1cl3, true)

                        end

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Deletar Veículo (TESTAR - BAN NO P2)", 0.424, yvalue, function ()

                    local p333dd = PlayerPedId()

                    local inv333hp3d = IsPedInAnyVehicle(p333dd)

                    if inv333hp3d then

                        DeleteEntity(GetVehiclePedIsIn(PlayerPedId()))

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tunar ~r~(Performance)", 0.424, yvalue, function ()

                    local Vehicle = GetVehiclePedIsIn(PlayerPedId(), false)

                    if DoesEntityExist(Vehicle) then

                        NetworkRequestControlOfEntity(PlayerPedId())

                        NetworkRequestEntityControl(Vehicle)

                        SetVehicleModKit(Vehicle, 0.0)

                        SetVehicleMod(Vehicle, 11, GetNumVehicleMods(Vehicle, 11) - 1, false)

                        SetVehicleMod(Vehicle, 12, GetNumVehicleMods(Vehicle, 12) - 1, false)

                        SetVehicleMod(Vehicle, 13, GetNumVehicleMods(Vehicle, 13) - 1, false)

                        SetVehicleMod(Vehicle, 15, GetNumVehicleMods(Vehicle, 15) - 2, false)

                        SetVehicleMod(Vehicle, 16, GetNumVehicleMods(Vehicle, 16) - 1, false)

                        ToggleVehicleMod(Vehicle, 17, true)

                        ToggleVehicleMod(Vehicle, 18, true)

                        ToggleVehicleMod(Vehicle, 19, true)

                        ToggleVehicleMod(Vehicle, 21, true)

                    end

                end)

            end





            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tunar ~r~(Full)", 0.424, yvalue, function ()

                    local Vehicle = GetVehiclePedIsIn(PlayerPedId(), false)

                    if DoesEntityExist(Vehicle) then

                        NetworkRequestEntityControl(Vehicle)

                        SetVehicleModKit(Vehicle, 0)

                        SetVehicleWheelType(Vehicle, 7)

                        SetVehicleMod(Vehicle, 0, GetNumVehicleMods(Vehicle, 0) - 1, false)

                        SetVehicleMod(Vehicle, 1, GetNumVehicleMods(Vehicle, 1) - 1, false)

                        SetVehicleMod(Vehicle, 2, GetNumVehicleMods(Vehicle, 2) - 1, false)

                        SetVehicleMod(Vehicle, 3, GetNumVehicleMods(Vehicle, 3) - 1, false)

                        SetVehicleMod(Vehicle, 4, GetNumVehicleMods(Vehicle, 4) - 1, false)

                        SetVehicleMod(Vehicle, 5, GetNumVehicleMods(Vehicle, 5) - 1, false)

                        SetVehicleMod(Vehicle, 6, GetNumVehicleMods(Vehicle, 6) - 1, false)

                        SetVehicleMod(Vehicle, 7, GetNumVehicleMods(Vehicle, 7) - 1, false)

                        SetVehicleMod(Vehicle, 8, GetNumVehicleMods(Vehicle, 8) - 1, false)

                        SetVehicleMod(Vehicle, 9, GetNumVehicleMods(Vehicle, 9) - 1, false)

                        SetVehicleMod(Vehicle, 10, GetNumVehicleMods(Vehicle, 10) - 1, false)

                        SetVehicleMod(Vehicle, 11, GetNumVehicleMods(Vehicle, 11) - 1, false)

                        SetVehicleMod(Vehicle, 12, GetNumVehicleMods(Vehicle, 12) - 1, false)

                        SetVehicleMod(Vehicle, 13, GetNumVehicleMods(Vehicle, 13) - 1, false)

                        SetVehicleMod(Vehicle, 15, GetNumVehicleMods(Vehicle, 15) - 2, false)

                        SetVehicleMod(Vehicle, 16, GetNumVehicleMods(Vehicle, 16) - 1, false)

                        ToggleVehicleMod(Vehicle, 17, true)

                        ToggleVehicleMod(Vehicle, 18, true)

                        ToggleVehicleMod(Vehicle, 19, true)

                        ToggleVehicleMod(Vehicle, 20, true)

                        ToggleVehicleMod(Vehicle, 21, true)

                        ToggleVehicleMod(Vehicle, 22, true)

                        SetVehicleMod(Vehicle, 25, GetNumVehicleMods(Vehicle, 25) - 1, false)

                        SetVehicleMod(Vehicle, 27, GetNumVehicleMods(Vehicle, 27) - 1, false)

                        SetVehicleMod(Vehicle, 28, GetNumVehicleMods(Vehicle, 28) - 1, false)

                        SetVehicleMod(Vehicle, 30, GetNumVehicleMods(Vehicle, 30) - 1, false)

                        SetVehicleMod(Vehicle, 33, GetNumVehicleMods(Vehicle, 33) - 1, false)

                        SetVehicleMod(Vehicle, 34, GetNumVehicleMods(Vehicle, 34) - 1, false)

                        SetVehicleMod(Vehicle, 35, GetNumVehicleMods(Vehicle, 35) - 1, false)

                        NetworkRequestControlOfEntity(PlayerPedId())

                        SetVehicleModKit(Vehicle, 0.0)

                        SetVehicleMod(Vehicle, 11, GetNumVehicleMods(Vehicle, 11) - 1, false)

                        SetVehicleMod(Vehicle, 12, GetNumVehicleMods(Vehicle, 12) - 1, false)

                        SetVehicleMod(Vehicle, 13, GetNumVehicleMods(Vehicle, 13) - 1, false)

                        SetVehicleMod(Vehicle, 15, GetNumVehicleMods(Vehicle, 15) - 2, false)

                        SetVehicleMod(Vehicle, 16, GetNumVehicleMods(Vehicle, 16) - 1, false)

                        ToggleVehicleMod(Vehicle, 17, true)

                        ToggleVehicleMod(Vehicle, 18, true)

                        ToggleVehicleMod(Vehicle, 19, true)

                        ToggleVehicleMod(Vehicle, 21, true)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Remover Tunning", 0.424, yvalue, function ()

                    local Vehicle = GetVehiclePedIsIn(PlayerPedId(), false)

                    if DoesEntityExist(Vehicle) then

                        NetworkRequestEntityControl(Vehicle)

                        SetVehicleModKit(Vehicle, 0) 

                        for i = 0, 49 do

                            RemoveVehicleMod(Vehicle, i)

                        end

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(H07nB00st33r, "Buzina Boost ~r~[E]", 0.43, yvalue, function ()

                    H07nB00st33r = not H07nB00st33r

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(handling, "Handling", 0.43, yvalue, function ()

                    handling = not handling

                    local veh = GetVehiclePedIsIn(PlayerPedId(), 0)

                    if not handling then

                        SetVehicleGravityAmount(veh, 9.8)

                        SetVehicleForwardSpeed(playerVeh, 1.0)

                    else

                        SetVehicleGravityAmount(veh, 30.0)

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(vehfly, "Voar com o Veículo", 0.43, yvalue, function ()

                    vehfly = not vehfly

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(handling2, "Speed Boost", 0.43, yvalue, function ()

                    handling2 = not handling2

                end)

            end



            yvalue = yvalue + 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.Slider("speedboost", 0.455, yvalue, 1, 0.07)

            end





            yvalue = yvalue + addbutton2 - 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(r33pa7ra7v31cul00, "Auto Reparar", 0.43, yvalue, function ()

                    r33pa7ra7v31cul00 = not r33pa7ra7v31cul00

                    Citizen.CreateThread(function()

                        while true do

                            Citizen.Wait(1000)

                            if r33pa7ra7v31cul00 and IsPedInAnyVehicle(PlayerPedId()) then

                                local v111dav33icul00 = GetEntityHealth(GetVehiclePedIsIn(PlayerPedId()))

                                if v111dav33icul00 < 1000 then

                                    --SetVehicleOnGroundProperly(GetVehiclePedIsIn(PlayerPedId(), 0))

                                    SetVehicleFixed(GetVehiclePedIsIn(PlayerPedId(), false))

                                    SetVehicleDirtLevel(GetVehiclePedIsIn(PlayerPedId(), false), 0.0)

                                    SetVehicleLights(GetVehiclePedIsIn(PlayerPedId(), false), 0)

                                    SetVehicleBurnout(GetVehiclePedIsIn(PlayerPedId(), false), false)

                                    --SetVehicleLightsMode(GetVehiclePedIsIn(PlayerPedId(), false), 0)

                                    Citizen.Wait(0)

                                end

                            else

                                Citizen.Wait(1000)

                            end

                        end

                    end)

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(vehrgb, "Carro RGB", 0.43, yvalue, function ()

                    vehrgb = not vehrgb

                end)

            end





            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(Pul4rc4r, "Pular com o Veículo ~r~[SPACE]", 0.43, yvalue, function ()

                    Pul4rc4r = not Pul4rc4r

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(f0rc4rm0t0r, "Forçar Motor Ligado", 0.43, yvalue, function ()

                    f0rc4rm0t0r = not f0rc4rm0t0r

                    Citizen.CreateThread(function()

                        while true do

                            Citizen.Wait(0)

                            if f0rc4rm0t0r and IsPedInAnyVehicle(PlayerPedId()) then

                                SetVehicleEngineOn(GetVehiclePedIsIn(PlayerPedId(), false), true, true, false)

                                -- SetVehicleLights(GetVehiclePedIsIn(PlayerPedId(), false), 3)

                            else

                                Citizen.Wait(1000)

                            end

                        end

                    end)

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(v3l0z3r0, "Atirar Dentro do Carro", 0.43, yvalue, function ()

                    v3l0z3r0 = not v3l0z3r0

                    Citizen.CreateThread(function()

                        while true do

                            Citizen.Wait(0)

                            if v3l0z3r0 and IsPedInAnyVehicle(PlayerPedId()) then

                                EnableControlAction(0, 69, true)

                                EnableControlAction(0, 92, true)

                                SetPlayerCanDoDriveBy(PlayerId(), true)

                            else

                                Citizen.Wait(1000)

                            end

                        end

                    end)

                end)

            end





            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(naocaca, "Não Cair Da Moto", 0.43, yvalue, function ()

                    naocaca = not naocaca

                    if naocaca then

                        SetPedCanBeKnockedOffVehicle(PlayerPedId(), true)

                    else

                        SetPedCanBeKnockedOffVehicle(PlayerPedId(), false)

                    end

                end)

            end



--[[             yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(naocaca, "Não Cair Da Moto", 0.43, yvalue, function ()

                    naocaca = not naocaca

                    if naocaca then

                        SetPedCanBeKnockedOffVehicle(PlayerPedId(), true)

                    else

                        SetPedCanBeKnockedOffVehicle(PlayerPedId(), false)

                    end

                end)

            end ]]



        elseif psychovars.main.tab == "vehicles" then

            

            





            local yvalue = 0.32+scrolls["vehicles"].static

            local addbutton = 0.045

            local addbutton2 = 0.030

            local max = 0.76

            interact.Scroll(5, "vehicles")



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.textBox("searchVehs", "", "Pesquisar Vehs", 0.424, yvalue)

            end





            callfunc.callVehicleList()





            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tp Veículo Sel", 0.424, yvalue, function ()

                    if SelectedVeh then

                        if 1 == 1 then-- if not IsVehicleSeatFree(vehiclesSelected, -1) then

                            TaskWarpPedIntoVehicle(PlayerPedId(), SelectedVeh, -1)

                        end

                        if IsPedInAnyVehicle(PlayerPedId()) then

                        end

                    end 

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Puxar Veículo Sel", 0.424, yvalue, function ()

                    if SelectedVeh then

                        if IsVehicleSeatFree(SelectedVeh, -1) then

                            Vehicle = SelectedVeh

                            NetworkRequestEntityControl(Vehicle)

                            cd = GetEntityCoords(PlayerPedId())

                            savedpos1 = GetEntityCoords(PlayerPedId())

                            SetEntityRotation(Vehicle, GetCamRot(Camera, 2), 0.0, GetCamRot(Camera, 2), 0.0, true)

                            SetEntityCoords(SelectedVeh, savedpos1)

                        end

                        if IsPedInAnyVehicle(PlayerPedId()) then

                        end

                    end 

                end)

            end

            



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Destrancar Veículo Sel", 0.424, yvalue, function ()

                    if SelectedVeh then

                        SetVehicleDoorsLocked(SelectedVeh, 1)

                        SetVehicleDoorsLockedForPlayer(SelectedVeh, PlayerId(), false)

                        SetVehicleDoorsLockedForAllPlayers(SelectedVeh, false)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Trancar Veículo Sel", 0.424, yvalue, function ()

                if SelectedVeh then

                    if DoesEntityExist(SelectedVeh) then

                        SetVehicleDoorsLocked(SelectedVeh, 1)

                        SetVehicleDoorsLockedForPlayer(SelectedVeh, PlayerId(), true)

                        SetVehicleDoorsLockedForAllPlayers(SelectedVeh, true)

                    end

                end

            end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Bloquear Veículo Sel", 0.424, yvalue, function ()

                    if SelectedVeh then

                        blockveh(SelectedVeh)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Estourar Pneus Veículo Sel", 0.424, yvalue, function ()

                    if SelectedVeh then

                        Pneus(SelectedVeh) 

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Quebrar Motor Veículo Sel", 0.424, yvalue, function ()

                    if SelectedVeh then

                        killengine(SelectedVeh) 

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Clonar Placa Sel", 0.424, yvalue, function ()

                    if SelectedVeh and IsPedInAnyVehicle(PlayerPedId(), 0) then

                        local plaqueta = GetVehicleNumberPlateText(SelectedVeh)

                        local car = GetVehiclePedIsUsing(PlayerPedId())

                        SetVehicleNumberPlateText(car, plaqueta)

                    end

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Explodir Veículo", 0.424, yvalue, function ()

                    local r0_144 = SelectedVeh

                    local r2_144 = GetVehicleModelNumberOfSeats(GetEntityModel(r0_144)) - 2

                    if DoesEntityExist(r0_144) and r0_144 ~= GetVehiclePedIsIn(PlayerPedId()) and IsVehicleSeatFree(r0_144, -1) then

                        local r3_144 = GetEntityCoords(PlayerPedId())

                        local r4_144 = GetEntityHeading(PlayerPedId())

                        NetworkRequestControlOfEntity(r0_144)

                        local r5_144 = GetGameTimer()

                        while not NetworkHasControlOfEntity(r0_144) do

                            local r6_144 = GetGameTimer() - r5_144

                            if r6_144 > 5000 then

                                print('PROTEÇÃO ANTI-BAN, VOCÊ SERIA BANIDO!')

                                break

                            end

                            NetworkRequestControlOfEntity(r0_144)

                            Wait(10)

                        end

                        ExplodeVehicle(r0_144, true, false)

                        ExplodeVehicleInCutscene(r0_144, true)

                    end

                end)

            end

            



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(puxmirado, "Puxar Veículo Mirado ~r~[E]", 0.43, yvalue, function ()

                    puxmirado = not puxmirado

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(ControleRemoto, "Controle Remoto", 0.43, yvalue, function ()

                    ControleRemoto = not ControleRemoto

                end)

            end



--[[             yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(kabumveh, "Explodir Veículo", 0.43, yvalue, function ()

                    kabumveh = not kabumveh



                end)

            end ]]











--[[             yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Tp Veículo Próximo", 0.424, yvalue, function ()

                    local v3h1cl3 = GetClosestVehicle(GetEntityCoords(PlayerPedId()), 25.0, 0, 70)

                    if DoesEntityExist(v3h1cl3) then

                            if DoesEntityExist(v3h1cl3) then

                            SetVehicleDoorsLocked(v3h1cl3, 1)

                            SetVehicleDoorsLockedForPlayer(v3h1cl3, PlayerId(), true)

                            SetVehicleDoorsLockedForAllPlayers(v3h1cl3, true)

                        end

                    end

                end)

            end ]]



--[[             yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(colocarfuncname, "FUNC DE TOOGLE", 0.43, yvalue, function ()



                end)

            end ]]

        

        elseif psychovars.main.tab == "visual" then



            local yvalue = 0.32+scrolls["visual"].static

            local addbutton = 0.045

            local addbutton2 = 0.030

            local max = 0.76

            interact.Scroll(5, "visual")





--[[             yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("TESTE", 0.424, yvalue, function ()

                    print(SelectedVeh)

                    if SelectedVeh then

                        if 1 == 1 then-- if not IsVehicleSeatFree(vehiclesSelected, -1) then

                            TaskWarpPedIntoVehicle(PlayerPedId(), SelectedVeh, -1)

                        end

                        if IsPedInAnyVehicle(PlayerPedId()) then

                        end

                    end 

                end)

            end ]]



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(esp_nome, "ESP Nomes", 0.43, yvalue, function ()

                    esp_nome = not esp_nome

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(esp_linhas, "ESP Linhas", 0.43, yvalue, function ()

                    esp_linhas = not esp_linhas

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(espesq, "ESP Esqueletos", 0.43, yvalue, function ()

                    espesq = not espesq

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(vidabarra, "ESP Vida", 0.43, yvalue, function ()

                    vidabarra = not vidabarra

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(espbox, "ESP Box", 0.43, yvalue, function ()

                    espbox = not espbox

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(espadm2, "ESP Staff", 0.43, yvalue, function ()

                    espadm2 = not espadm2

                    espadm = not espadm

                    espaurora2 = not espaurora2

                    espaurora1 = not espaurora1

                    alertaadm = not alertaadm

                    l1n23sc0rn0 = not l1n23sc0rn0

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(listaadm, "Lista Staffs Próximos", 0.43, yvalue, function ()

                    listaadm = not listaadm

                    --local table = {"Farinha Discord", "Admnistrador", "Pichau Gamer"}

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(esp_vehs, "ESP Vehs", 0.43, yvalue, function ()

                    esp_vehs = not esp_vehs

                end)

            end



--[[             yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(colocarfuncname, "FUNC DE TOOGLE", 0.43, yvalue, function ()



                end)

            end ]]





            -- PARTE DA ESQUERDA 



            yvalue = 0.3+scrolls["visual"].static + addbutton2





            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Virar Homem", 0.615, yvalue, function ()

                    Citizen.CreateThread(function()

                        RequestModel(GetHashKey("mp_m_freemode_01"))

                        Citizen.Wait(100)

                        if HasModelLoaded(GetHashKey("mp_m_freemode_01")) then

                            SetPlayerModel(PlayerId(), GetHashKey("mp_m_freemode_01"))

                        end

                    end)

                end)

            end

            

            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Virar Mulher", 0.615, yvalue, function ()

                    Citizen.CreateThread(function()

                        RequestModel(GetHashKey("mp_f_freemode_01"))

                        Citizen.Wait(100)

                        if HasModelLoaded(GetHashKey("mp_f_freemode_01")) then

                            SetPlayerModel(PlayerId(), GetHashKey("mp_f_freemode_01"))

                        end

                    end)

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Roupa ADM", 0.615, yvalue, function ()

                    roupaADM()

                end)

            end




            -- 



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Roupa 1", 0.615, yvalue, function ()



                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Roupa 2", 0.615, yvalue, function ()



                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Roupa 3", 0.615, yvalue, function ()



                end)

            end







            -- HEROIS

            

--[[             local H3r01s = {

                {name = "Hulk", m00d33ll = "mp_m_freemode_01"},

                {name = "Flash", m00d33ll = "Flash"},

                {name = "Batman", m00d33ll = "batman"},

                {name = "Deadpool", m00d33ll = "deadpool"},

                {name = "Thanos", m00d33ll = "thanos"},

                {name = "Ironman", m00d33ll = "ironman"},

                {name = "AnaoCJ", m00d33ll = "anaocj"},

                {name = "Anao Fabiano", m00d33ll = "anaofabiano"},

                {name = "Anao Arnold", m00d33ll = "anaoarnold"},

                {name = "Kids Sandra", m00d33ll = "kidssandra"},

            } ]]

            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Flash", 0.615, yvalue, function ()

                    Citizen.CreateThread(function()

                        RequestModel(GetHashKey("Flash"))

                        Citizen.Wait(100)

                        if HasModelLoaded(GetHashKey("Flash")) then

                            SetPlayerModel(PlayerId(), GetHashKey("Flash"))

                        else

                            print('SKIN NÃO ENCONTRADA NESTE SERVIDOR :(')

                        end

                    end)

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Batman", 0.615, yvalue, function ()

                    Citizen.CreateThread(function()

                        RequestModel(GetHashKey("batman"))

                        Citizen.Wait(100)

                        if HasModelLoaded(GetHashKey("batman")) then

                            SetPlayerModel(PlayerId(), GetHashKey("batman"))

                        else

                            print('SKIN NÃO ENCONTRADA NESTE SERVIDOR :(')

                        end

                    end)

                end)

            end





            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Deadpool", 0.615, yvalue, function ()

                    Citizen.CreateThread(function()

                        RequestModel(GetHashKey("deadpool"))

                        Citizen.Wait(100)

                        if HasModelLoaded(GetHashKey("deadpool")) then

                            SetPlayerModel(PlayerId(), GetHashKey("deadpool"))

                        else

                            print('SKIN NÃO ENCONTRADA NESTE SERVIDOR :(')

                        end

                    end)

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Thanos", 0.615, yvalue, function ()

                    Citizen.CreateThread(function()

                        RequestModel(GetHashKey("thanos"))

                        Citizen.Wait(100)

                        if HasModelLoaded(GetHashKey("thanos")) then

                            SetPlayerModel(PlayerId(), GetHashKey("thanos"))

                        else

                            print('SKIN NÃO ENCONTRADA NESTE SERVIDOR :(')

                        end

                    end)

                end)

            end





        elseif psychovars.main.tab == "trolloptions" then



            local yvalue = 0.32+scrolls["trolloptions"].static

            local addbutton = 0.045

            local addbutton2 = 0.030

            local max = 0.76

            interact.Scroll(10, "trolloptions")

    

            --yvalue = 0.32+scrolls["trolloptions"].static + addbutton2

            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(freecammode, "FreeCam", 0.43, yvalue, function ()

                    freecammode = not freecammode

                    -- ON

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(delv3hs, "Deletar Veículos", 0.43, yvalue, function ()

                    delv3hs = not delv3hs

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(deleng1n3, "Desligar Motor dos Veículos", 0.43, yvalue, function ()

                    deleng1n3 = not deleng1n3

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(bugv3hs, "Bugar Veículos", 0.43, yvalue, function ()

                    bugv3hs = not bugv3hs

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(j0garv3hs, "Lançar Veículos", 0.43, yvalue, function ()

                    j0garv3hs = not j0garv3hs

                end)

            end



            if NoisyCars then

                for d77 in EnumerateVehicles() do

                    NetworkRequestControlOfEntity(d77)

                    SetVehicleAlarm(d77,true)

                    SetVehicleAlarmTimeLeft(d77,1000)

                end

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(PedVehFly, "Veículos Na Lua", 0.43, yvalue, function ()

                    PedVehFly = not PedVehFly

                    if PedVehFly then

                        for k in EnumerateVehicles() do

                            RequestControlOnce(k)

                            ApplyForceToEntity(k, 3, 0.0, 0.0, 500.0, 0.0, 0.0, 0.0, 0, 0, 1, 1, 0, 1)

                        end

                    end

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(killenginev3hs, "Quebrar Motor dos Veículos", 0.43, yvalue, function ()

                    killenginev3hs = not killenginev3hs

                end)

            end

            

            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(killpneusv3hs, "Estourar Pneus dos Veículos", 0.43, yvalue, function ()

                    killpneusv3hs = not killpneusv3hs

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(NoisyCars, "Carros Barulhentos", 0.43, yvalue, function ()

                    NoisyCars = not NoisyCars

                end)

            end



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(olh0st4z3r, "Olhos Tazer ~r~[E]", 0.43, yvalue, function ()

                    olh0st4z3r = not olh0st4z3r

                end)

            end



--[[             yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(olh0sl4z3r, "Olhos Lazer ~r~[E]", 0.43, yvalue, function ()

                    olh0sl4z3r = not olh0sl4z3r

                end)

            end ]]



            yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(t4zerinall, "Tazer Geral Loop", 0.43, yvalue, function ()

                    t4zerinall = not t4zerinall

                end)

            end

            

            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Derrubar Geral", 0.425, yvalue, function ()

                    for _, player in ipairs(GetActivePlayers()) do

                        Derrubar(player)

                    end

                end)

            end



            -- yvalue = yvalue + addbutton

            -- if yvalue >= 0.34 and yvalue <= max then

            --     interact.standardbutton("Spawn barreira", 0.424, yvalue, function()

            --         SpawnBarreiras()

            --     end)

            -- end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Spawn spikes", 0.425, yvalue, function()

                    SpawnSpikes()

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Preparar Carros", 0.425, yvalue, function()

                    prepararindexar()

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Levitar Carros", 0.425, yvalue, function()

                    TutuuuFly()

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Mudar placas Carro", 0.425, yvalue, function()

                    tutu_MudarPlacaMQCU()

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Botar pra mamar", 0.425, yvalue, function()

                    TutuBypass_MamaPiru()

                end)

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Deserto de Saddam", 0.425, yvalue, function()

                    MorroDoTutu()

                end)

            end



            -- PARTE DA ESQUERDA 



            yvalue = 0.32+scrolls["trolloptionsleft"].static + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(carregarv3hs, "Pegar Carros ~r~[Y]", 0.62, yvalue, function ()

                    carregarv3hs = not carregarv3hs

                end)

            end



            yvalue = yvalue + 0.008

            if yvalue >= 0.34 and yvalue <= max then

                interact.Slider("carregar", 0.67, yvalue, 1, 0.07)

            end









            



--[[             yvalue = yvalue + 0.008

            if yvalue >= 0.34 and yvalue <= max then

                --local value = string.match(tostring(Sliders["carregarvehs"].value),"%d+")

                --DrawTexte(""..value.."",0.662+L0ad37_X,0.310+L0ad37_Y-0.01,false,0.3,6,false)

                DrawTexte("Força:",0.43+yvalue,0.294+yvalue-0.01,false,0.3,6,false)

                interact.Slider("carregarvehs", 0.43, yvalue, 1, 0.08)

            end ]]



        elseif psychovars.main.tab == "exploits" then



            local yvalue = 0.32+scrolls["exploits"].static

            local addbutton = 0.045

            local addbutton2 = 0.030

            local max = 0.76

            interact.Scroll(10, "exploits")

    

            --yvalue = 0.32+scrolls["trolloptions"].static + addbutton2

--[[             yvalue = yvalue + addbutton2

            if yvalue >= 0.34 and yvalue <= max then

                interact.togglebox(freecammode, "FreeCam", 0.43, yvalue, function ()



                end)

            end ]]





            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                if groupcity == "FUSION" or groupcity == "SPACE" or groupcity == "NEXUS" or groupcity == "LOTUS" then

                    interact.standardbutton("Remover Modo Novato", 0.425, yvalue, function()

                        LocalPlayer.state.NovatMode = nil

                        if groupcity == "SPACE" then

                            LocalPlayer.state.games = true

                            LocalPlayer.state.pvp = true

                        elseif groupcity == "FUSION" then

                            GlobalState.NovatTime = 0

                        elseif groupcity == "NEXUS" then

                            LocalPlayer.state.onlineTime = 250

                        end

--[[                         elseif groupcity == "LOTUS" then

                            r11_0.functions.inject("novat_system", "                                    _G.BlockWeaponWheelThisFrame = function()\n                                        _G.ShowWeaponWheel(true)\n                                        return false\n                                    end\n    \n                                    local oldDisableControlAction = _G.DisableControlAction\n                                    _G.DisableControlAction = function(inputGroup, control, disable)\n                                        if (inputGroup == 2 and control == 37) or (inputGroup == 0 and control == 140) then\n                                            _G.EnableControlAction(inputGroup, control, true)\n                                            return true\n                                        end\n                                        \n                                        return oldDisableControlAction(inputGroup, control, disable)\n                                    end\n    \n                                    local oldDisablePlayerFiring = _G.DisablePlayerFiring\n                                    _G.DisablePlayerFiring = function(player, toggle)\n                                        if toggle then\n                                            oldDisablePlayerFiring(player, false)\n                                            return true\n                                        end\n                                        \n                                        return oldDisablePlayerFiring(player, toggle)\n                                    end\n    \n                                    local oldSetCanPedEquipAllWeapons = _G.SetCanPedEquipAllWeapons\n                                    _G.SetCanPedEquipAllWeapons = function(ped, toggle)\n                                        if not toggle then\n                                            oldSetCanPedEquipAllWeapons(ped, true)\n                                            return true\n                                        end\n                                        \n                                        return oldSetCanPedEquipAllWeapons(ped, toggle)\n                                    end\n    \n                                    local oldSetCurrentPedWeapon = _G.SetCurrentPedWeapon\n                                    _G.SetCurrentPedWeapon = function(ped, weaponHash, equipNow)\n                                        if weaponHash == GetHashKey(\"WEAPON_UNARMED\") then\n                                            return true\n                                        end\n                                        \n                                        return oldSetCurrentPedWeapon(ped, weaponHash, equipNow)\n                                    end\n    \n                                    local oldTriggerEvent = _G.TriggerEvent\n                                    _G.TriggerEvent = function(event, ...)\n                                        if event == \"Notify\" then\n                                            return true\n                                        end\n    \n                                        return oldTriggerEvent(event, ...)\n                                    end\n                                    \n                                    _G.Citizen.CreateThread(function()\n                                        while true do\n                                            _G.EnableControlAction(0, 24, true)\n                                            Wait(0)\n                                        end\n                                    end)\n                                ")

                        end ]]

                    end)

                end

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                if groupcity == "SPACE" then

                    interact.standardbutton("Voltar Modo Novato", 0.425, yvalue, function()

                        LocalPlayer.state.games = false

                        LocalPlayer.state.pvp = false

                    end)

                end

            end



            yvalue = yvalue + addbutton

            if yvalue >= 0.34 and yvalue <= max then

                interact.standardbutton("Confirmar Grupo", 0.425, yvalue, function()

                    print('CIDADE DO GRUPO: '.. groupcity)

                end)

            end

            



        end

    end,



    bindscheck = function ()

        for button, key in pairs(binds.buttons) do

            if key.value ~= nil then

                if IsDisabledControlJustPressed(0, key.value) then

                    key.func()

                end

            end

        end



        for button, key in pairs(binds.toggles) do

            if key.value ~= nil then

                if IsDisabledControlJustPressed(0, key.value) then

                    currenttoggle = key.texttoggle

                    disableanim = false

                    

                    key.func()

                end

            end

        end

    end,



    callPlayersList = function ()

        local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

        local y = 0.3+scrolls["playerList"].static

        local add = 0.03

        local max = 0.73



        if IsDisabledControlPressed(0, 14) and y > (0.355 - (#playerson * add)) and mousefunctions.mouse(0.63+Loader_X, 0.46+Loader_Y, 0.165, 0.25) then

            scrolls["playerList"].static = scrolls["playerList"].static - add

        end

        if IsDisabledControlJustPressed(0, 15) and y < (0.3) and mousefunctions.mouse(0.63+Loader_X, 0.46+Loader_Y, 0.165, 0.25) then

            scrolls["playerList"].static = scrolls["playerList"].static + add

        end



        for i = 1, #playerson do

            if i > 0 then

                player = playerson[i].player

                local selected = false

                selfcoords = GetEntityCoords(PlayerPedId())

                local buttonypos = ((0.05 * 1.0) + (i - 1) * 0.024) + y +Loader_Y

                pedcoords = GetEntityCoords(GetPlayerPed(player))

                local name = GetPlayerName(player)

                if not interact.textBoxes["searchPlayers"].text or interact.textBoxes["searchPlayers"].text == "" or string.match(name:lower(), interact.textBoxes["searchPlayers"].text:lower()) then

                local distance = GetDistanceBetweenCoords(selfcoords, pedcoords, false)

                if distance < listVariables.distanceLimit then

                local r,g,b = 255,255,255





                if buttonypos >= 0.34+Loader_Y and buttonypos <= 0.5300+Loader_Y then

                    local playerinfo = false

                    local playerinfo = ' '..name..'  D - '..math.ceil(playerson[i].distance)

                    if SelectedPlayer == player then

                        r,g,b = overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b

                        playerinfo = '• '..name..'  D - '..math.ceil(playerson[i].distance)

                    end





                    if interact.PlayerButton(playerinfo, 0.45+Loader_X, buttonypos+0.025, false, r,g,b) then

                        if SelectedPlayer == player then

                            SelectedPlayer = false

                        else

                            SelectedPlayer = player

                        end

                    end

                end

                end

            end

            end

        end

    end,







    callVehicleList = function ()

        local Loader_X, Loader_Y = Drag.LoaderX, Drag.LoaderY

        local y = 0.31 + scrolls["vehicleList"].static

        local add = 0.03

    

        -- Lógica para rolar a lista de veículos

        if IsDisabledControlPressed(0, 14) and y > (0.355 - ((#vehlist-3) * add)) and mousefunctions.mouse(0.63+Loader_X, 0.46+Loader_Y, 0.165, 0.25) then

            scrolls["vehicleList"].static = scrolls["vehicleList"].static - add

        end

        if IsDisabledControlJustPressed(0, 15) and y < (0.3) and mousefunctions.mouse(0.63+Loader_X, 0.46+Loader_Y, 0.165, 0.25) then

            scrolls["vehicleList"].static = scrolls["vehicleList"].static + add

        end

    

        -- Lógica para selecionar veículos com base na pesquisa

        for i = 1, #vehlist do

            if i > 0 then

                local selected = false

                local clickYPos = ((0.05 * 1.0) + (i - 1) * 0.024) + y + Drag.LoaderY

                local currentVehicle = vehlist[i].vehicle

                local vehicleName = GetDisplayNameFromVehicleModel(GetEntityModel(currentVehicle))

                local selfCoords = GetEntityCoords(PlayerPedId())

                local vehCoords = GetEntityCoords(currentVehicle)

                local distance = GetDistanceBetweenCoords(selfCoords, vehCoords, false)

    

                if distance < listVariables.distanceLimit then

                    local r, g, b = 255, 255, 255

                    local vehStateText = "D"

                    if GetPedInVehicleSeat(currentVehicle, -1) ~= 0 then

                        vehStateText = "I"

                    end

                    

                    -- Verifica se o veículo corresponde à pesquisa

                    if not interact.textBoxes["searchVehs"].text or interact.textBoxes["searchVehs"].text == "" or string.match(vehicleName:lower(), interact.textBoxes["searchVehs"].text:lower()) then

                        if clickYPos >= 0.34+Loader_Y and clickYPos <= 0.5300+Loader_Y then

                            



                            local vehInformation = ' ' .. vehicleName .. ' '..vehStateText..' - ' .. math.ceil(vehlist[i].distance)

    

                            for k, vehicle in pairs(vehiclesSelected) do

                                if vehicle == currentVehicle then

                                    r, g, b = overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b

                                    if vehicle == SelectedVeh then

                                        vehInformation = '• ' .. vehicleName .. ' '..vehStateText..' - ' .. math.ceil(vehlist[i].distance)

                                    end

    

                                    selected = true

                                end

                            end

    

                            -- Desenha o botão do veículo

                            if interact.PlayerButton(vehInformation, 0.45 + Drag.LoaderX, clickYPos + 0.025, false, r, g, b) then

                                if selected then

                                    for k, vehicle in pairs(vehiclesSelected) do

                                        if vehicle == currentVehicle then

                                            table.remove(vehiclesSelected, k)

                                            SelectedVeh = getlastitem(vehiclesSelected)

                                            break

                                        end

                                    end

                                else

                                    table.insert(vehiclesSelected, currentVehicle)

                                    SelectedVeh = currentVehicle

                                end

                            end

                        end

                    end

                end

            end

        end

    end,

    

    

    



    ifs = function ()

        if SelectedVeh then

            if not IsPedInVehicle(PlayerPedId(), SelectedVeh) then

            local modelType = 0

            local addy = 4

            if GetVehicleClass(SelectedVeh) == 16 then

                modelType = 7

                addy = 3

            elseif GetVehicleClass(SelectedVeh) == 15 then

                modelType = 34

                addy = 4



            elseif GetVehicleClass(SelectedVeh) == 8 then

                modelType = 37

                addy = 3



            elseif GetVehicleClass(SelectedVeh) == 21 or GetVehicleClass(SelectedVeh) == 20 then

                modelType = 39

                addy = 3



            elseif GetVehicleClass(SelectedVeh) == 14 then

                modelType = 35

                addy = 3



            elseif GetVehicleClass(SelectedVeh) == 13 then

                modelType = 38

                addy = 3



            elseif GetDisplayNameFromVehicleModel(GetEntityModel(SelectedVeh)) == "THRUSTER" then

                modelType = 41

                addy = 3



            end

            modelCoords = GetEntityCoords(SelectedVeh)

            DrawMarker(modelType, modelCoords.x, modelCoords.y, modelCoords.z + addy, 0.0, 0.0, 0.0, 0.0, 0.0, 0.0, 2.0, 2.0, 2.0, overlay.colors.main.r, overlay.colors.main.g, overlay.colors.main.b, 255, true, true, 2, nil, nil, false)

            end

        end



        local invincibilityTimer = 0 -- Variável para controlar o tempo para a próxima invencibilidade



        if healthmodule.godmode then

            if cityAC == "PLPROTECT" then

                print('GODMODE PL_PROTECT -- v1.1')

--[[                     NetworkSetLocalPlayerInvincibleTime(500)

                SetPedCanRagdoll(PlayerPedId(), false) ]]

                local r2_15 = NetworkSetLocalPlayerInvincibleTime

                local r3_15 = 500

                if not r3_15 then

                    r3_15 = 0

                end

                print(r3_15)

                r2_15(r3_15)

                SetPedCanRagdoll(PlayerPedId(), false)

            else

                SetEntityOnlyDamagedByRelationshipGroup(PlayerPedId(), true, 30131)

            end

        end

        





--[[         if healthmodule.godmode then

            if cityAC == "PLPROTECT" then

                print('GODMODE PL_PROTECT -- v1.0')

                NetworkSetLocalPlayerInvincibleTime(500)

                SetPedCanRagdoll(PlayerPedId(), false)

            else

                SetEntityOnlyDamagedByRelationshipGroup(PlayerPedId(), true, 30131)

            end

        end ]]



        if healthmodule.inv1s1bl3 then

            SetEntityVisible(GetVehiclePedIsIn(PlayerPedId(), 0), false, false)

            SetEntityVisible(PlayerPedId(), false)

        end

        

        if healthmodule.antadm then

            for an in EnumeratePeds() do

                local adm = IsEntityVisible(an)

                if not adm or administrador then

                    local cC = GetEntityCoords(an)

                    local me = an ~= PlayerPedId()

                    local mr = IsPedAPlayer(an)

                    local cD = GetDistanceBetweenCoords(GetEntityCoords(PlayerPedId()), cC.x, cC.y, cC.z, true) * (1.6 - 0.05) -- Tamanho

                    local c00rds = GetEntityCoords(PlayerPedId())

                    local dismax = Sliders['n0st4ff'].value

                    if cD < dismax then

                        local coordx = c00rds.x

                        local coordy = c00rds.y + 500

        

                        if me and GetEntityHealth(an) > 101 then

                            for Zpos = 10, -200, -5 do

                                SetEntityCoordsNoOffset(PlayerPedId(), coordx, coordy, Zpos + 0.0, true, true, true, false)

                                local zPos = GetGroundZFor_3dCoord(coordx, coordy, Zpos + 0.0)

                                Wait(0)

                            end

                            ClearDrawOrigin()

                        end

                    end

                end

            end

        end



        if healthmodule.s4po then

            SetPedCanRagdoll(PlayerPedId(), false)

            if IsDisabledControlJustPressed(0, 22) then

                ApplyForceToEntity(PlayerPedId(), 3, 0.0, 0.0, Sliders['s4populo'].value, 0.0, 0.0, 0.0, 0, 0, 0, 1, 1, 1)

            end

        end



        if healthmodule.r0d44rm4s then

            Citizen.InvokeNative(0x9DFE13ECDC1EC196, PlayerPedId(), true)

            EnableControlAction(0, 37, true)

        end

        



        if healthmodule.afog4do then

            SetPedMaxTimeUnderwater(PlayerPedId(), 50)

        end



        if healthmodule.f4strun then

            local sp3edrun = 10

            sp3edrun = Sliders['fastrun'].value

            SetPedCanRagdoll(PlayerPedId(), false)

            SetEntityVelocity(PlayerPedId(), GetOffsetFromEntityInWorldCoords(PlayerPedId(), 0.0, sp3edrun, GetEntityVelocity(PlayerPedId())[3]) - GetEntityCoords(PlayerPedId()))

        end

        



        if healthmodule.s0c4o then

            local mud4nc4d4m4g3 = SetWeaponDamageModifierThisFrame

            local p3g4p3g4 = GetHashKey

            local f0rc3 = 14.9

            mud4nc4d4m4g3(p3g4p3g4('weapon_unarmed'), f0rc3)

        end



        if H07nB00st33r and IsPedInAnyVehicle(PlayerPedId(-1), true) then

            if IsControlPressed(1, 38) then

                SetVehicleForwardSpeed(GetVehiclePedIsUsing(PlayerPedId(-1)), 80 + 0.0)

            end

        end



        if handling2 then

            Invoken(0x93A3996368C94158, GetVehiclePedIsIn(Invoken(0x43A66C31C68491C0, -1), false), Sliders["speedboost"].value + 0.0 * 20.0)

        else

            Invoken(0x93A3996368C94158, GetVehiclePedIsIn(Invoken(0x43A66C31C68491C0, -1), false), 20.0)

        end



        if vehrgb and IsPedInAnyVehicle(PlayerPedId()) then

            ra = RGBcarrito(1.3)

            SetVehicleCustomPrimaryColour(GetVehiclePedIsUsing(PlayerPedId()), ra.r, ra.g, ra.b)

            SetVehicleCustomSecondaryColour(GetVehiclePedIsUsing(PlayerPedId()), ra.r, ra.g, ra.b)

        end



        if vehfly and IsPedInAnyVehicle(PlayerPedId(), false) then

            --DisableControlAction(0, 76, true)

            DisableControlAction(0, 63, true)

            DisableControlAction(0, 64, true)

            --DisableControlAction(0, 21, true)

            local veh = GetVehiclePedIsIn(PlayerPedId(), false)

            local vel = GetEntityVelocity(veh)

            local color = {r= 128, g= 0, b= 128, a= 255}

            local vehrot = GetEntityRotation(veh, 2)

            local pitch = vehrot.x

            local roll = 0

            local yaw = vehrot.z

            --SetEntityHeading(veh, GetEntityHeading(veh)) this can be used for noclip



            if IsDisabledControlPressed(0, 63) then -- A

                yaw = yaw + 1.0

                SetEntityRotation(veh, pitch, roll, yaw, 2, true)

            end

            if IsDisabledControlPressed(0, 64) then -- D

                yaw = yaw - 1.0

                SetEntityRotation(veh, pitch, roll, yaw, 2, true)

            end

            local vehpos = GetEntityCoords(GetVehiclePedIsIn(PlayerPedId(), false))

            --if IsDisabledControlPressed(0, 76) then -- space

            --  SetEntityVelocity(veh, vel.x, vel.y, vel.z + 1.0)

            --end

            if IsDisabledControlPressed(0, 21) then -- shift

                pitch = pitch - 1.0

                SetEntityRotation(veh, pitch, roll, yaw, 2, true)

            end

            if IsDisabledControlPressed(0, 62) then -- ctrl

                pitch = pitch + 1.0

                SetEntityRotation(veh, pitch, roll, yaw, 2, true)

            end

            if IsControlPressed(0, 71) then -- Coords

                SetVehicleForwardSpeed(GetVehiclePedIsIn(PlayerPedId(), false), GetEntitySpeed(GetVehiclePedIsIn(PlayerPedId(), false)) + 0.3) -- 0.3 default

            end

            if IsDisabledControlPressed(0, 72) then -- s

                SetVehicleForwardSpeed(GetVehiclePedIsIn(PlayerPedId(), false), GetEntitySpeed(GetVehiclePedIsIn(PlayerPedId(), false)) - 1.0)

            end

            SetEntityRotation(veh, pitch, roll, yaw, 2, true)



            local mph = GetEntitySpeed(GetVehiclePedIsIn(PlayerPedId(), false)) * 2.236936

            if mph > 335 and mph < 337 then

                local color = {r= 128, g= 0, b= 128, a= 255}

                --drawText('Max Speed, Derestric Max Speed to go faster', notifX - 0.17 / 2 + 0.01, notifY + 0.07, 4, color, 0.4, false, true, false)

            end



        else

            --DisableControlAction(0, 76, false)

            DisableControlAction(0, 63, false)

            DisableControlAction(0, 64, false)

            --DisableControlAction(0, 21, false)

        end



        if esp_nome then

            local myPos = GetEntityCoords(PlayerPedId(), true)



            for k, v in pairs(GetActivePlayers()) do

                if GetPlayerPed(v) ~= GetPlayerPed(-1) then

                    local targetPed = GetPlayerPed(v)

                    local targetPos = GetEntityCoords(targetPed, true)

                    local distance = #(vector3(myPos.x, myPos.y, myPos.z) - vector3(targetPos.x, targetPos.y, targetPos.z))



                    if distance < 350 then

                        local isInFOV = IsEntityOnScreen(targetPed)

                        local isInvisible = not IsEntityVisibleToScript(targetPed)



                        if isInFOV then

                            local distanceText = math.floor(distance) .. "m"

                            local offset = vector3(0, 0, -1)



                            if NetworkIsPlayerTalking(v) then

                                DrawText3DD(targetPos.x, targetPos.y, targetPos.z + offset.z, "".. GetPlayerName(v) ..'\n[FALANDO] - ' .. distanceText, 255, 255, 255, 255, 2.0)

                            else

                                local textToShow = isInvisible and "[STAFF]" or ""

                                local r, g, b = isInvisible and RGBRainbow(2.0).r or 255, isInvisible and RGBRainbow(2.0).g or 255, isInvisible and RGBRainbow(2.0).b or 255

                                DrawText3DD(targetPos.x, targetPos.y, targetPos.z + offset.z, GetPlayerName(v) ..' ' .. textToShow .. '\n' .. distanceText, r, g, b, 255, 2.0)

                            end

                        end

                    end

                end

            end

        end



        if espadm2 then

            local maxDistance = 500

            local myPlayerId = PlayerId()

            local myPos = GetEntityCoords(PlayerPedId())

        

            for _, player in ipairs(GetActivePlayers()) do

                if player ~= myPlayerId then

                    local myped = GetPlayerPed(player)

                    if myped ~= -1 and myped ~= nil then

                        local playerPos = GetEntityCoords(myped)

                        local distance = #(myPos - playerPos)

        

                        if IsEntityVisibleToScript(myped) == false and distance <= maxDistance then

                            if distance < maxDistance then

                                if true and not IsEntityDead(myped) then

                                    if HasEntityClearLosToEntity(PlayerPedId(), myped, 19) and IsEntityOnScreen(myped) then

                                        local ra = RGBRainbow(2.0)

        

                                        

                                        DrawLine(GetPedBoneCoords(myped, 31086), GetPedBoneCoords(myped, 0x9995), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x9995), GetEntityCoords(myped), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x5C57), GetEntityCoords(myped), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x192A), GetEntityCoords(myped), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x3FCF), GetPedBoneCoords(myped, 0x192A), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xCC4D), GetPedBoneCoords(myped, 0x3FCF), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xB3FE), GetPedBoneCoords(myped, 0x5C57), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xB3FE), GetPedBoneCoords(myped, 0x3779), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x9995), GetPedBoneCoords(myped, 0xB1C5), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xB1C5), GetPedBoneCoords(myped, 0xEEEB), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xEEEB), GetPedBoneCoords(myped, 0x49D9), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x9995), GetPedBoneCoords(myped, 0x9D4D), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x9D4D), GetPedBoneCoords(myped, 0x6E5C), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x6E5C), GetPedBoneCoords(myped, 0xDEAD), ra.r, ra.g, ra.b, 255)

        

                                        local myPos = GetPedBoneCoords(myped, 31086)

                                        DrawMarker(28, myPos.x, myPos.y, myPos.z + 0.06, 0.0, 0.0, 0.0, 0.0, 180.0, 0.0, 0.1, 0.1, 0.1, ra.r, ra.g, ra.b, 255, false, Stan_true, 2, kakamenuv3ss, kakamenuv3ss, false)

                                    end

                                end

                            end

                        end

                    end

                end

            end

        end



        if espadm then

            local maxDistance = 500

            local myPos = GetEntityCoords(PlayerPedId())



            for _, player in ipairs(GetActivePlayers()) do

                local myped = GetPlayerPed(player)

                if myped ~= -1 and myped ~= nil then

                    local playerPos = GetEntityCoords(myped)

                    local distance = #(myPos - playerPos)



                    if IsEntityVisibleToScript(myped) == false and distance <= maxDistance then

                        if distance < maxDistance then

                            if true and not IsEntityDead(myped) then

                                if HasEntityClearLosToEntity(PlayerPedId(), myped, 19) and IsEntityOnScreen(myped) then

                                    local ra = RGBRainbow(2.0)

                                    DrawLine(myPos.x, myPos.y, myPos.z, playerPos.x, playerPos.y, playerPos.z, ra.r, ra.g, ra.b, 255)

                                end

                            end

                        end

                    end

                end

            end

        end



        if espaurora1 then

            local maxDistance = 500

            local myPos = GetEntityCoords(PlayerPedId())



            for _, player in ipairs(GetActivePlayers()) do

                local myped = GetPlayerPed(player)

                if myped ~= -1 and myped ~= nil then

                    local playerPos = GetEntityCoords(myped)

                    local distance = #(myPos - playerPos)



                    if distance <= maxDistance and not IsEntityDead(myped) then

                        local playerName = GetPlayerName(player)

                        if playerName and playerName == "Ryomen" then

                            DrawLine(myPos.x, myPos.y, myPos.z, playerPos.x, playerPos.y, playerPos.z, 255, 0, 0, 255)

                        end

                    end

                end

            end

        end



        if espaurora2 then

            local maxDistance = 500

            local myPos = GetEntityCoords(PlayerPedId())



            for _, player in ipairs(GetActivePlayers()) do

                local myped = GetPlayerPed(player)

                if myped ~= -1 and myped ~= nil then

                    local playerPos = GetEntityCoords(myped)

                    local distance = #(myPos - playerPos)



                    if distance <= maxDistance and not IsEntityDead(myped) then

                        local playerName = GetPlayerName(player)

                        if playerName and playerName == "Aurorinha" then

                            DrawLine(myPos.x, myPos.y, myPos.z, playerPos.x, playerPos.y, playerPos.z, 255, 0, 0, 255)

                        end

                    end

                end

            end

        end



        if vidabarra then

            local localPlayer = PlayerId()

            local localPed = PlayerPedId()



            for _, player in ipairs(GetActivePlayers()) do

                if player ~= localPlayer then

                    local targetPed = GetPlayerPed(player)



                    if DoesEntityExist(targetPed) and IsEntityOnScreen(targetPed) then

                        local includeself = false

                        local er = includeself and nil or localPed



                        local distance = GetDistanceBetweenCoords(GetEntityCoords(er), GetEntityCoords(targetPed), true)



                        if distance < 500.0 then

                            local dist = GetDistanceBetweenCoords(GetFinalRenderedCamCoord(), GetEntityCoords(targetPed), true)

                            SetDrawOrigin(GetEntityCoords(targetPed))          

                            

                            DrawRect(-0.2745 / dist - (dist / 500) / dist, 0, 0.0020, 2.0 / dist, 0, 0, 0, 255)

                            DrawRect(-0.2745 / dist - (dist / 500) / dist, 2.05 / dist - GetEntityHealth(targetPed) / 195 / dist, 0.001, GetEntityHealth(targetPed) / 200 / dist, 30, 255, 30, 255)



                            ClearDrawOrigin()

                        end

                    end

                end

            end

        end



        if alertaadm then

            for an in EnumeratePeds() do

                local adm = IsEntityVisible(an)

                if not adm or administrador then

                    local cC = GetEntityCoords(an)

                    local me = an ~= PlayerPedId()

                    local mr = IsPedAPlayer(an)

                    local cD = GetDistanceBetweenCoords(GetEntityCoords(PlayerPedId()), cC.x, cC.y, cC.z, true) * (1.6 - 0.05) -- Tamanho

                    local c00rds = GetEntityCoords(PlayerPedId())

                    local dismax = 20

        

                    if me and cD < dismax then

                        



                        --print('Staff Observando')

                        interact.listBox(admobs, "Staff Observando", 0.2, 0.6, "StaffObservando")

                        --notifyrgbadm('Staff Observando')

                    end

                end

            end

        end



        function removeFromList(playerId)

            for i = #admlistpedID, 1, -1 do

                if admlistpedID[i] == playerId then

                    table.remove(admlistpedID, i)

                    table.remove(admlist, i)  -- Remover o nome correspondente também

                    return

                end

            end

        end

        

        if listaadm then

            interact.listBox(admlist, "Lista de Adm", 0.2, 0.2, "AdmList")

            local maxDistance = 500

            local myPos = GetEntityCoords(PlayerPedId())

            

            -- Adicionar jogadores à lista

            for _, player in ipairs(GetActivePlayers()) do

                local playerName = GetPlayerName(player)

                local myped = GetPlayerPed(player)

                if myped ~= -1 and myped ~= nil then

                    local playerPos = GetEntityCoords(myped)

                    local distance = #(myPos - playerPos)

                    

                    if IsEntityVisibleToScript(myped) == false and distance <= maxDistance then

                        if distance < maxDistance then

                            if true and not IsEntityDead(myped) then

                                if HasEntityClearLosToEntity(PlayerPedId(), myped, 19) and IsEntityOnScreen(myped) then

                                    -- Verificar se o jogador já está na lista

                                    local isPlayerInList = false

                                    for _, v in ipairs(admlistpedID) do

                                        if v == player then

                                            isPlayerInList = true

                                            break

                                        end

                                    end

                                    -- Se o jogador não estiver na lista, adicionamos

                                    if not isPlayerInList and PlayerId() ~= player then

                                        table.insert(admlistpedID, player)

                                        table.insert(admlist, playerName)  -- Adicionar nome correspondente

                                    end

                                end

                            end

                        end

                    end

                end

            end

            -- Remover jogadores da lista com distância maior que 500

            for i = #admlistpedID, 1, -1 do

                local playerId = admlistpedID[i]

                local playerPed = GetPlayerPed(playerId)

                if playerPed ~= nil then

                    local playerPos = GetEntityCoords(playerPed)

                    local distance = #(myPos - playerPos)

                    

                    if distance > maxDistance then

                        removeFromList(playerId)

                    end

                end

            end

        end

        



        if espbox then 

            local playerPed = PlayerPedId()

            

            for _, targetPlayer in ipairs(GetActivePlayers()) do

                local targetPed = GetPlayerPed(targetPlayer)

                

                if targetPed ~= playerPed then

                    local targetCoords = GetEntityCoords(targetPed)

        

                    local width = 0.3 

                    local height = 1.7 

        

                    local offsetX = 0.0 

                    local offsetY = 0.0 

                    local offsetZ = -1.0 

        

                    local leftTopFront = GetOffsetFromEntityInWorldCoords(targetPed, -width + offsetX, width + offsetY, offsetZ)

                    local rightTopFront = GetOffsetFromEntityInWorldCoords(targetPed, width + offsetX, width + offsetY, offsetZ)

                    local leftBottomFront = GetOffsetFromEntityInWorldCoords(targetPed, -width + offsetX, -width + offsetY, offsetZ)

                    local rightBottomFront = GetOffsetFromEntityInWorldCoords(targetPed, width + offsetX, -width + offsetY, offsetZ)

        

                    local leftTopBack = GetOffsetFromEntityInWorldCoords(targetPed, -width + offsetX, width + offsetY, height + offsetZ)

                    local rightTopBack = GetOffsetFromEntityInWorldCoords(targetPed, width + offsetX, width + offsetY, height + offsetZ)

                    local leftBottomBack = GetOffsetFromEntityInWorldCoords(targetPed, -width + offsetX, -width + offsetY, height + offsetZ)

                    local rightBottomBack = GetOffsetFromEntityInWorldCoords(targetPed, width + offsetX, -width + offsetY, height + offsetZ)

        

                    

                    local color = {255, 255, 255, 255}  

        

                    local playerInvisible = not IsEntityVisibleToScript(targetPed)  

        

                    if playerInvisible then

                        local rainbowColor = RGBRainbow(2.0)

                        color = {rainbowColor.r, rainbowColor.g, rainbowColor.b, 255}  

                    end

        

                    DrawLine(leftTopBack.x, leftTopBack.y, leftTopBack.z, rightTopBack.x, rightTopBack.y, rightTopBack.z, color[1], color[2], color[3], color[4])



                    DrawLine(leftTopFront.x, leftTopFront.y, leftTopFront.z, rightTopFront.x, rightTopFront.y, rightTopFront.z, color[1], color[2], color[3], color[4])

                    DrawLine(rightTopFront.x, rightTopFront.y, rightTopFront.z, rightTopBack.x, rightTopBack.y, rightTopBack.z, color[1], color[2], color[3], color[4])

                    DrawLine(rightTopBack.x, rightTopBack.y, rightTopBack.z, leftTopBack.x, leftTopBack.y, leftTopBack.z, color[1], color[2], color[3], color[4])

                    DrawLine(leftTopBack.x, leftTopBack.y, leftTopBack.z, leftTopFront.x, leftTopFront.y, leftTopFront.z, color[1], color[2], color[3], color[4])



                    DrawLine(leftBottomBack.x, leftBottomBack.y, leftBottomBack.z, rightBottomBack.x, rightBottomBack.y, rightBottomBack.z, color[1], color[2], color[3], color[4] - 0.05) -- Ajuste na posição vertical



                    DrawLine(leftBottomFront.x, leftBottomFront.y, leftBottomFront.z, rightBottomFront.x, rightBottomFront.y, rightBottomFront.z, color[1], color[2], color[3], color[4])

                    DrawLine(rightBottomFront.x, rightBottomFront.y, rightBottomFront.z, rightBottomBack.x, rightBottomBack.y, rightBottomBack.z, color[1], color[2], color[3], color[4])

                    DrawLine(rightBottomBack.x, rightBottomBack.y, rightBottomBack.z, leftBottomBack.x, leftBottomBack.y, leftBottomBack.z, color[1], color[2], color[3], color[4])

                    DrawLine(leftBottomBack.x, leftBottomBack.y, leftBottomBack.z, leftBottomFront.x, leftBottomFront.y, leftBottomFront.z, color[1], color[2], color[3], color[4])



                    DrawLine(leftTopFront.x, leftTopFront.y, leftTopFront.z, leftBottomFront.x, leftBottomFront.y, leftBottomFront.z, color[1], color[2], color[3], color[4])

                    DrawLine(rightTopFront.x, rightTopFront.y, rightTopFront.z, rightBottomFront.x, rightBottomFront.y, rightBottomFront.z, color[1], color[2], color[3], color[4])

                    DrawLine(leftTopBack.x, leftTopBack.y, leftTopBack.z, leftBottomBack.x, leftBottomBack.y, leftBottomBack.z, color[1], color[2], color[3], color[4])

                    DrawLine(rightTopBack.x, rightTopBack.y, rightTopBack.z, rightBottomBack.x, rightBottomBack.y, rightBottomBack.z, color[1], color[2], color[3], color[4])



                    DrawLine(leftTopBack.x, leftTopBack.y, leftTopBack.z, leftTopFront.x, leftTopFront.y, leftTopFront.z, color[1], color[2], color[3], color[4])

                    DrawLine(rightTopBack.x, rightTopBack.y, rightTopBack.z, rightTopFront.x, rightTopFront.y, rightTopFront.z, color[1], color[2], color[3], color[4])

                    DrawLine(rightBottomBack.x, rightBottomBack.y, rightBottomBack.z, rightBottomFront.x, rightBottomFront.y, rightBottomFront.z, color[1], color[2], color[3], color[4])

                    DrawLine(leftBottomBack.x, leftBottomBack.y, leftBottomBack.z, leftBottomFront.x, leftBottomFront.y, leftBottomFront.z, color[1], color[2], color[3], color[4])

                end

            end

        end



        if esp_vehs then

            for vehicle in EnumerateVehicles() do

                local x, y, z = table.unpack(GetEntityCoords(vehicle))

                local _, _x, _y = GetScreenCoordFromWorldCoord(x, y, z)

                local x1, y1, z1 = table.unpack(GetEntityCoords(PlayerPedId()))

                local dist = tonumber(string.format('%.1f', GetDistanceBetweenCoords(x1, y1, z1, x, y, z, true)))

                local string = '~r~' .. GetDisplayNameFromVehicleModel(GetEntityModel(vehicle)) .. ' ~w~[ ~s~' .. dist .. ' ~s~M ~w~]'

                if dist < 300 then --Sll1d3rs['par3d3_d1st'].valu333 then

                    local ra = RaaGddBee22(3.7)

                    SetTextColour(255, 255, 255, 255)

                DrawTextOutline(string,_x,_y,0.25,10,true,true,255, 255, 255)

                end

            end

        end



        if puxmirado and IsControlJustPressed(0, 38) then

            local playerID = PlayerId()

            local _, entity = GetEntityPlayerIsFreeAimingAt(playerID)

            if entity and IsEntityAVehicle(entity) and IsVehicleSeatFree(entity, -1) then

                local playerPed = PlayerPedId()

                local playerCoords = GetEntityCoords(playerPed)

                NetworkRequestControlOfEntity(entity)

                local startTime = GetGameTimer()

                while not NetworkHasControlOfEntity(entity) do

                    local elapsedTime = GetGameTimer() - startTime

                    if elapsedTime > 5000 then

                        break

                    end

                    NetworkRequestControlOfEntity(entity)

                    Wait(10)

                end

                SetEntityCoordsNoOffset(entity, playerCoords)

            end

        end





        if controlveh then

            local r1_141 = SelectedVeh

            --print('SelectedVeh: ' ..SelectedVeh)

            if DoesEntityExist(r1_141) and not NetworkHasControlOfEntity(r1_141) then

                --print('aaa')

                local r2_141 = GetEntityCoords(PlayerPedId())

                if r11_0.city.group == "FLUXO" then

                    SetEntityCoordsNoOffset(PlayerPedId(), GetEntityCoords(r1_141))

                    Wait(1000)

                end

                NetworkRequestControlOfEntity(SelectedVeh)

                SetPedIntoVehicle(PlayerPedId(), r1_141, -1)

                Wait(300)

                SetEntityCoordsNoOffset(PlayerPedId(), r2_141)

            end

        end



        -- AIMBOT



--[[         if A1mf00v3 then

            local F0v11 = (Sliders["circulo"].value / 200)

            DrawSprite('fov2', 'fov2', 0.5,0.5, F0v11, F0v11 * 1.8 ,0.0,255,255,255,255)

        end ]]

    

        

    

        if S1l3ntA1m then

            local F0v11 = (Sliders["circulo"].value / 200)

            local p333dd, a, b, c, d = getbixopuxePed()

            if b11xo00pux33P3ds then 

                aped = p333dd 

            else

                aped = IsPedAPlayer(p333dd)

            end

            if bixopuxeDeads then 

                deads = p333dd 

            else

                deads = not IsEntityDead(p333dd)

            end

            if A11mf03v_at74par3d3 then 

                vis = logged2

            else

                vis = HasEntityClearLosToEntity(PlayerPedId(), p333dd, 17) 

            end

            local hit = math.random(0, 100)

            local x, y, z = table.unpack(GetPedBoneCoords(p333dd, 31086))

            local _, _x, _y = GetScreenCoordFromWorldCoord(x, y, z)

            local c = GetPedBoneCoords(p333dd, 31086)

            local x1, y1, z1 = table.unpack(c)

            local selfpos, rot = GetFinalRenderedCamCoord(), GetEntityRotation(PlayerPedId(), 2)

            local angleX, angleY, angleZ = (c - selfpos).x, (c - selfpos).y, (c - selfpos).z

            local am1g02 = false

            local roll, pitch, yaw = -math.deg(math.atan2(angleX, angleY)) - rot.z, math.deg(math.atan2(angleZ, #vector3(angleX, angleY, 0.0))), 1.0

            local d1stanc3 = GetDistanceBetweenCoords(GetEntityCoords(PlayerPedId()), x1, y1, z1, true)

            roll = 0.0+(roll-0.0)

    

            if p333dd ~= PlayerPedId() and IsEntityOnScreen(p333dd) then 

                if (_x > 0.5 - ((F0v11 / 2)/0.5) and _x < 0.5 + ((F0v11 / 2)/0.5) and _y > 0.5 - ((F0v11 / 2)/0.5) and _y < 0.5 + ((F0v11 / 2)/0.5)) then

                    local unarmedhash = GetHashKey("weapon_unarmed")

                    local w3ap0n = GetSelectedPedWeapon(PlayerPedId())

                    if w3ap0n ~= unarmedhash then

                    if not IsEntityVisible(p333dd) then

                    else

                    if IsDisabledControlPressed(1, 25) then

                        if m0st7aralv0 and p333dd and d1stanc3 < 500 and d1stanc3 > 2 and GetEntityHealth(p333dd) > 101 and HasEntityClearLosToEntity(PlayerPedId(), p333dd, 19) then

                            D7aw3dT3xt(x1, y1, z1+0.45, 3, "•", 200, 0, 0)

                            DrawLine(GetEntityCoords(PlayerPedId()), x1, y1, z1, 255, 0, 0, 255)

                        end

                        if IsControlJustPressed(1, 24) then

                        if d1stanc3 < 400 and d1stanc3 > 3 then

                        if GetEntityHealth(p333dd) > 101 then

                            Citizen.CreateThread(function()

                        local pl2y3rP3d = PlayerPedId()

                        local pl3ay3rC00rds = GetEntityCoords(pl2y3rP3d)

                        local ta7g3tp3d = p333dd

                        if not DoesEntityExist(ta7g3tp3d) then

                            return 

                        end

                        local targ3tC00ds = GetEntityCoords(ta7g3tp3d)

                        local headme = GetPedBoneCoords(pl2y3rP3d, 31086)

                        local c = GetPedBoneCoords(p333dd, 31086)

                        local bulletSpeed = 100

                        local x1, y1, z1 = table.unpack(c)

                        local x2 , y2, z2 = table.unpack(headme)

        

                        SetPedShootsAtCoord(pl2y3rP3d, x1, y1, z1, true)

        

                        local ta7g3tH3adC000rdsd = GetPedBoneCoords(ta7g3tp3d, ta7g3tH3adB00n33)

        

                        ShootSingleBulletBetweenCoords(x2, y2, z2, x1, y1, z1, bulletSpeed, true, w3ap0n, pl2y3rP3d, true, false, -1.0, true)

                    end)

            end

            end

            end

                    end

                end

            end

                end

            end

         end

         

         if A11ml00ck3 then

            local F0v11 = (Sliders["circulo"].value / 200)

            local p333dd, a, b, c, d = getbixopuxePed()

            local v1da = GetEntityHealth(p333dd)

            if b11xo00pux33P3ds then 

                aped = p333dd 

            else

                aped = IsPedAPlayer(p333dd)

            end

            if bixopuxeDeads then 

                deads = p333dd 

            else

                deads = not IsEntityDead(p333dd)

            end

            if deads then

            if A11mf03v_at74par3d3 then 

                vis = logged2

            else

                vis = HasEntityClearLosToEntity(PlayerPedId(), p333dd, 17) 

            end

            local hit = math.random(0, 100)

            local x, y, z = table.unpack(GetPedBoneCoords(p333dd, 31086))

            local _, _x, _y = GetScreenCoordFromWorldCoord(x, y, z)

            local c = GetPedBoneCoords(p333dd, 31086)

            local x1, y1, z1 = table.unpack(c)

            local selfpos, rot = GetFinalRenderedCamCoord(), GetEntityRotation(PlayerPedId(), 2)

            local angleX, angleY, angleZ = (c - selfpos).x, (c - selfpos).y, (c - selfpos).z

            local am1g02 = false

            local roll, pitch, yaw = -math.deg(math.atan2(angleX, angleY)) - rot.z, math.deg(math.atan2(angleZ, #vector3(angleX, angleY, 0.0))), 1.0

            roll = 0.0+(roll-0.0)

    

            if v1da > 101 then

            if aped and deads and hit <= Sliders['Sm00th1ng'].value * 10 and p333dd ~= PlayerPedId() and IsEntityOnScreen(p333dd) then 

                if (_x > 0.5 - ((F0v11 / 2)/0.5) and _x < 0.5 + ((F0v11 / 2)/0.5) and _y > 0.5 - ((F0v11 / 2)/0.5) and _y < 0.5 + ((F0v11 / 2)/0.5)) then

                    if not IsEntityVisible(p333dd) then

        

                    else

                        if IsAimCamActive() then 

                            if a1111l0ck30nlyv1s1bl3 then

                                if HasEntityClearLosToEntity(PlayerPedId(), p333dd, 19) then

                                SetGameplayCamRelativeRotation(roll, pitch, yaw) 

                                end                     

                            else

                            SetGameplayCamRelativeRotation(roll, pitch, yaw)  

                            end            

                        end

                    end

                end

                end

            end

            end

         end



         if R44g3b00t then

            local F0v11 = (Sliders["circulo"].value / 200)

            local p333dd, a, b, c, d = getbixopuxePed()

            if b11xo00pux33P3ds then 

                aped = p333dd 

            else

                aped = IsPedAPlayer(p333dd)

            end

            if bixopuxeDeads then 

                deads = p333dd 

            else

                deads = not IsEntityDead(p333dd)

            end

            if A11mf03v_at74par3d3 then 

                vis = logged2

            else

                vis = HasEntityClearLosToEntity(PlayerPedId(), p333dd, 17) 

            end

            local hit = math.random(0, 100)

            local x, y, z = table.unpack(GetPedBoneCoords(p333dd, 31086))

            local _, _x, _y = GetScreenCoordFromWorldCoord(x, y, z)

            local c = GetPedBoneCoords(p333dd, 31086)

            local x1, y1, z1 = table.unpack(c)

            local selfpos, rot = GetFinalRenderedCamCoord(), GetEntityRotation(PlayerPedId(), 2)

            local angleX, angleY, angleZ = (c - selfpos).x, (c - selfpos).y, (c - selfpos).z

            local roll, pitch, yaw = -math.deg(math.atan2(angleX, angleY)) - rot.z, math.deg(math.atan2(angleZ, #vector3(angleX, angleY, 0.0))), 1.0

            local d1stanc3 = GetDistanceBetweenCoords(GetEntityCoords(PlayerPedId()), x1, y1, z1, true)

            local am1g02 = false

            roll = 0.0+(roll-0.0)

        



            if am1g02 == false then

            if p333dd ~= PlayerPedId() and IsEntityOnScreen(p333dd) then 

                if (_x > 0.5 - ((F0v11 / 2)/0.5) and _x < 0.5 + ((F0v11 / 2)/0.5) and _y > 0.5 - ((F0v11 / 2)/0.5) and _y < 0.5 + ((F0v11 / 2)/0.5)) then

                    if n30pux37c0rno and not IsEntityVisible(p333dd) then

                    else

                    if IsControlPressed(1, R9g3b0tK3i["Value"]) then

                        if d1stanc3 < 500 and d1stanc3 > 5 then

                        if IsEntityDead(p333dd) == false then

                            Citizen.CreateThread(function()

                        local pl2y3rP3d = PlayerPedId()

                        local pl3ay3rC00rds = GetEntityCoords(pl2y3rP3d)

                        local ta7g3tp3d = p333dd

                        if not DoesEntityExist(ta7g3tp3d) then

                            return 

                        end

                        local t47g3tc00rds = GetEntityCoords(ta7g3tp3d)

                        local c = GetPedBoneCoords(p333dd, 31086)

                        local bu113tsp31d = 500

                        local x1, y1, z1 = table.unpack(c)

        

                        SetPedShootsAtCoord(pl2y3rP3d, x1+0.2, y1+0.2, z1+0.2, true)

        

                        local ta7g3tH3adC000rdsd = GetPedBoneCoords(ta7g3tp3d, ta7g3tH3adB00n33)

                        Wait(100)

                        ShootSingleBulletBetweenCoords(x1+0.2, y1+0.2, z1+0.2, x1, y1, z1, bu113tsp31d, true, GetHashKey("WEAPON_PISTOL_MK2"), pl2y3rP3d, true, false, -1.0, true)

                    end)

                end

            end

                    end

                end

            end

                end

            end

         end





        Citizen.CreateThread(function() while ControleRemoto do

            FreezeEntityPosition(PlayerPedId(), true)

            SetVehicleEngineOn(SelectedVeh, true, true, true)

            Wait(0)

                if ControleRemoto then

                    local spectate_cam = spectate_cam

                    if not spectate_cam ~= nil then

                        spectate_cam = CreateCam('DEFAULT_SCRIPTED_Camera', 1)

                    end

                    RenderScriptCams(1, 0, 0, 1, 1)

                    SetCamActive(spectate_cam, true)

                    local coords = GetEntityCoords(SelectedVeh)



                    --print('SelectedVeh: ' ..coords)

                    SetCamCoord(spectate_cam, coords.x, coords.y, coords.z + 3)

                    local offsetRotX = 0.0

                    local offsetRotY = 0.0

                    local offsetRotZ = 0.0

                    local weapondelay = 0

                    while DoesCamExist(spectate_cam) do

                        Wait(0)

                        if not ControleRemoto then

                            DestroyCam(spectate_cam, false)

                            ClearTimecycleModifier()

                            RenderScriptCams(false, false, 0, 1, 0)

                            SetFocusEntity(PlayerPedId())

                            FreezeEntityPosition(PlayerPedId(), false)

                            break

                        end

                        local playerPed = GetPlayerPed(SelectedPlayer)

                        local playerRot = GetEntityRotation(playerPed, 2)

                        local rotX = playerRot.x

                        local rotY = playerRot.y

                        local rotZ = playerRot.z

                        offsetRotX = offsetRotX - (GetDisabledControlNormal(1, 2) * 8.0)

                        offsetRotZ = offsetRotZ - (GetDisabledControlNormal(1, 1) * 8.0)

                        if (offsetRotX > 90.0) then

                            offsetRotX = 90.0

                        elseif (offsetRotX < -90.0) then

                            offsetRotX = -90.0

                        end

                        if (offsetRotY > 90.0) then

                            offsetRotY = 90.0

                        elseif (offsetRotY < -90.0) then

                            offsetRotY = -90.0

                        end

                        if (offsetRotZ > 360.0) then

                            offsetRotZ = offsetRotZ - 360.0

                        elseif (offsetRotZ < -360.0) then

                            offsetRotZ = offsetRotZ + 360.0

                        end



                        if IsDisabledControlPressed(0, 129) and not IsDisabledControlPressed(0, 130) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 9, 1)

                        end

                        if IsDisabledControlJustReleased(0, 129) or IsDisabledControlJustReleased(0, 130) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 6, 2500)

                        end

                        if IsDisabledControlPressed(0, 130) and not IsDisabledControlPressed(0, 129) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 22, 1)

                        end

                        if IsDisabledControlPressed(0, 89) and IsDisabledControlPressed(0, 130) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 13, 1)

                        end

                        if IsDisabledControlPressed(0, 90) and IsDisabledControlPressed(0, 130) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 14, 1)

                        end

                        if IsDisabledControlPressed(0, 129) and IsDisabledControlPressed(0, 130) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 30, 100)

                        end

                        if IsDisabledControlPressed(0, 89) and IsDisabledControlPressed(0, 129) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 7, 1)

                        end

                        if IsDisabledControlPressed(0, 90) and IsDisabledControlPressed(0, 129) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 8, 1)

                        end

                        if IsDisabledControlPressed(0, 89) and not IsDisabledControlPressed(0, 129) and not IsDisabledControlPressed(0, 130) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 4, 1)

                        end

                        if IsDisabledControlPressed(0, 90) and not IsDisabledControlPressed(0, 129) and not IsDisabledControlPressed(0, 130) then

                            TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 5, 1)

                        end





                        local x, y, z = table.unpack(GetCamCoord(spectate_cam))

                        local coords_ES = GetEntityCoords(SelectedVeh) + (RotationToDirection(GetCamRot(spectate_cam, 2)) * (0.5 * 1.5))

                        SetCamCoord(spectate_cam, coords_ES.x-3.0, coords_ES.y, coords_ES.z + 2.0)

                        if not Displayed then

                            SetFocusArea(GetCamCoord(spectate_cam).x, GetCamCoord(spectate_cam).y, GetCamCoord(spectate_cam).z,0.0,0.0,0.0)

                            SetCamRot(spectate_cam, offsetRotX, offsetRotY, offsetRotZ, 2)

                        end

                    end

                end

            end

        end)



--[[         if tptosky then

            local ped = GetPlayerPed(SelectedPlayer) 

            RequestModel(GetHashKey('ch_prop_ch_top_panel02'))

            fok1 = CreateObject(GetHashKey('ch_prop_ch_top_panel02'), GetEntityCoords(ped),1,1,1) 

            SetEntityVisible(fok1, false, 0)

            NetworkSetEntityInvisibleToNetwork(fok1,true) 

            AttachEntityToEntityPhysically(fok1, ped, 0,0, 0.0,-150.0,0.0, 0.0, 0.0, 0.0, 99999999999, 1, false, false, 1, 2)

        else

            NetworkRequestControlOfEntity(fok1)

            DeleteEntity(fok1)

        end ]]



--[[         if ControleRemoto and SelectedVeh then

            FreezeEntityPosition(PlayerPedId(), true)

            SetVehicleEngineOn(SelectedVeh, true, true, true)

            while ControleRemoto and SelectedVeh do

                Citizen.Wait(0)

                if not ControleRemoto then

                    SetVehicleEngineOn(SelectedVeh, false, false, false)

                    DestroyCam(camrc, false)

                    RenderScriptCams(false, false, 0, 1, 0)

                    FreezeEntityPosition(PlayerPedId(), false)

                    SetFocusEntity(PlayerPedId())

                    break

                end

                if IsDisabledControlPressed(0, 129) and not IsDisabledControlPressed(0, 130) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 9, 1)

                end

                if IsDisabledControlJustReleased(0, 129) or IsDisabledControlJustReleased(0, 130) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 6, 2500)

                end

                if IsDisabledControlPressed(0, 130) and not IsDisabledControlPressed(0, 129) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 22, 1)

                end

                if IsDisabledControlPressed(0, 89) and IsDisabledControlPressed(0, 130) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 13, 1)

                end

                if IsDisabledControlPressed(0, 90) and IsDisabledControlPressed(0, 130) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 14, 1)

                end

                if IsDisabledControlPressed(0, 129) and IsDisabledControlPressed(0, 130) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 30, 100)

                end

                if IsDisabledControlPressed(0, 89) and IsDisabledControlPressed(0, 129) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 7, 1)

                end

                if IsDisabledControlPressed(0, 90) and IsDisabledControlPressed(0, 129) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 8, 1)

                end

                if IsDisabledControlPressed(0, 89) and not IsDisabledControlPressed(0, 129) and not IsDisabledControlPressed(0, 130) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 4, 1)

                end

                if IsDisabledControlPressed(0, 90) and not IsDisabledControlPressed(0, 129) and not IsDisabledControlPressed(0, 130) then

                    TaskVehicleTempAction(PlayerPedId(), SelectedVeh, 5, 1)

                end

                if hornboost2 then

                    local Vehicle = SelectedVeh

                    if IsDisabledControlPressed(0, 38) then

                        SetVehicleBoostActive(Vehicle, true)

                        SetVehicleForwardSpeed(Vehicle,GetEntitySpeed(Vehicle) + 2)

                        Timer = GetGameTimer() + 1000

                    end

                end

                local x, y, z = table.unpack(GetCamCoord(Camera))

                AttachCamToEntity(Camera, SelectedVeh, 0.0, -9.5, 1.8, true)

                SetFocusArea(GetCamCoord(Camera).x, GetCamCoord(Camera).y, GetCamCoord(Camera).z, 0.0, 0.0, 0.0)

                SetCamRot(Camera, GetEntityRotation(SelectedVeh), 2)

            end

        end ]]

        

        



        function RaaGddBee22(frequency)

            local result = {}

            local curtime = GetGameTimer() / 1000

         

            result.r = math.floor(math.sin(curtime * frequency + 0) * 127 + 128)

            result.g = math.floor(math.sin(curtime * frequency + 2) * 127 + 128)

            result.b = math.floor(math.sin(curtime * frequency + 4) * 127 + 128)

         

            return result

        end



        function RGBRainbow(frequency)

            local result = {}

            local curtime = GetGameTimer() / 1000



            result.r = math.floor(math.sin(curtime * frequency + 0) * 127 + 128)

            result.g = math.floor(math.sin(curtime * frequency + 2) * 127 + 128)

            result.b = math.floor(math.sin(curtime * frequency + 4) * 127 + 128)



            return result

        end



        if esp_linhas then

            if 1 == 1 then --if e3sp3s then

            for an in EnumeratePeds() do

                local cC = GetEntityCoords(an)

                local c00rds = GetEntityCoords(PlayerPedId())

                local me = an ~= PlayerPedId()

                local mr = IsPedAPlayer(aR)

                local cD = GetDistanceBetweenCoords(GetFinalRenderedCamCoord(), cC.x, cC.y, cC.z, true) * (1.6 - 0.05) -- Tamanho

                local dismax = 400 --Sll1d3rs["par3d3_d1st"].valu333 * 3

                if IsEntityOnScreen(an) then

                    if cD < dismax then

                            if me then

                            if HasEntityClearLosToEntity(PlayerPedId(), an, 19) then

                                DrawLine(c00rds, cC, 255, 16, 150, 232)

                            else

                                if false == false then

                                    DrawLine(c00rds, cC, 255, 16, 150, 232)

                                end

                            end

                            end

                        end

                            ClearDrawOrigin()

                        end

                end

            end

        end

        

        if l1n23sc0rn0 then

            for an in EnumeratePeds() do

                local adm = IsEntityVisible(an)

                for _, admin in ipairs(C0rn0s) do

                    if admin == an then

                        local admnistrador = true

                    end

                 end

                if adm == false or admnistrador then

                local cC = GetEntityCoords(an)

                local c00rds = GetEntityCoords(PlayerPedId())

                local me = an ~= PlayerPedId()

                local mr = IsPedAPlayer(aR)

                local cD = GetDistanceBetweenCoords(GetFinalRenderedCamCoord(), cC.x, cC.y, cC.z, true) * (1.6 - 0.05) -- Tamanho

                local dismax = 160

                    if cD < dismax and GozaDentroFalcon == false then

                            if me then

                                ra = RaaGddBee22(2.0)

                                DrawLine(c00rds, cC, ra.r, ra.g, ra.b, 255)

                                for _, admin in ipairs(C0rn0s) do

                                    if admin == an then

                                        jaeadm = true

                                        end

                                    end

                                if jaeadm ~= true then

                                table.insert(C0rn0s, an)

                                end

                            end

                        end

                            ClearDrawOrigin()

                        end

                end

        end



        if espesq then

            local visualsskeletons_peds = true

            for ped in EnumeratePeds() do

                local d = GetDistanceBetweenCoords(GetFinalRenderedCamCoord(), GetEntityCoords(ped), false) 

                if visualsskeletons_peds then 

                    mr = ped

                else

                    mr = IsPedAPlayer(ped)

                end

                if visuals_skeletons_self then 

                    me = ped

                else

                    me = ped ~= PlayerPedId() 

                end

                dead = IsEntityDead(ped)

                    

                    if d < 400 then --Sliders['esp_distancia'].value + 0.0 then

                        if mr and not dead and IsEntityOnScreen(ped) then

                            if ped ~= PlayerPedId() then

                                print('3')

                                if HasEntityClearLosToEntity(PlayerPedId(), ped, 19) then 

                                local r, g, b = dasihbudsauihdsahuidsuh2.r, dasihbudsauihdsahuidsuh2.g, dasihbudsauihdsahuidsuh2.b			

                                DrawLine(GetPedBoneCoordsF(ped, 31086, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x9995, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x9995, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xE0FD, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x5C57, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xE0FD, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x192A, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xE0FD, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x3FCF, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x192A, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xCC4D, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x3FCF, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xB3FE, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x5C57, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xB3FE, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x3779, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x9995, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xB1C5, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xB1C5, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xEEEB, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xEEEB, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x49D9, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x9995, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x9D4D, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x9D4D, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x6E5C, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x6E5C, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xDEAD, 0.0, 0.0, 0.0),r, g, b, 255)

                            else

                                local r, g, b = dasihbudsauihdsahuidsuh2.r, dasihbudsauihdsahuidsuh2.g, dasihbudsauihdsahuidsuh2.b				

                                DrawLine(GetPedBoneCoordsF(ped, 31086, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x9995, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x9995, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xE0FD, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x5C57, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xE0FD, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x192A, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xE0FD, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x3FCF, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x192A, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xCC4D, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x3FCF, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xB3FE, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x5C57, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xB3FE, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x3779, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x9995, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xB1C5, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xB1C5, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xEEEB, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0xEEEB, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x49D9, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x9995, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x9D4D, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x9D4D, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0x6E5C, 0.0, 0.0, 0.0),r, g, b, 255)

                                DrawLine(GetPedBoneCoordsF(ped, 0x6E5C, 0.0, 0.0, 0.0),GetPedBoneCoordsF(ped, 0xDEAD, 0.0, 0.0, 0.0),r, g, b, 255)

                            end

                        end

                    end

                end

            end

        end



        if l1n23sc0rn02 then

            local maxDistance = 500

            local myPlayerId = PlayerId()

            local myPos = GetEntityCoords(PlayerPedId())

        

            for _, player in ipairs(GetActivePlayers()) do

                if player ~= myPlayerId then

                    local myped = GetPlayerPed(player)

                    if myped ~= -1 and myped ~= nil then

                        local playerPos = GetEntityCoords(myped)

                        local distance = #(myPos - playerPos)

        

                        if IsEntityVisibleToScript(myped) == false and distance <= maxDistance then

                            if distance < maxDistance then

                                if true and not IsEntityDead(myped) then

                                    if HasEntityClearLosToEntity(PlayerPedId(), myped, 19) and IsEntityOnScreen(myped) then

                                        local ra = RaaGddBee22(2.0)

        

                                        DrawLine(GetPedBoneCoords(myped, 31086), GetPedBoneCoords(myped, 0x9995), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x9995), GetEntityCoords(myped), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x5C57), GetEntityCoords(myped), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x192A), GetEntityCoords(myped), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x3FCF), GetPedBoneCoords(myped, 0x192A), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xCC4D), GetPedBoneCoords(myped, 0x3FCF), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xB3FE), GetPedBoneCoords(myped, 0x5C57), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xB3FE), GetPedBoneCoords(myped, 0x3779), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x9995), GetPedBoneCoords(myped, 0xB1C5), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xB1C5), GetPedBoneCoords(myped, 0xEEEB), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0xEEEB), GetPedBoneCoords(myped, 0x49D9), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x9995), GetPedBoneCoords(myped, 0x9D4D), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x9D4D), GetPedBoneCoords(myped, 0x6E5C), ra.r, ra.g, ra.b, 255)

                                        DrawLine(GetPedBoneCoords(myped, 0x6E5C), GetPedBoneCoords(myped, 0xDEAD), ra.r, ra.g, ra.b, 255)

        

                                        local myPos = GetPedBoneCoords(myped, 31086)

                                        DrawMarker(28, myPos.x, myPos.y, myPos.z + 0.06, 0.0, 0.0, 0.0, 0.0, 180.0, 0.0, 0.1, 0.1, 0.1, ra.r, ra.g, ra.b, 255, Stan_false, Stan_true, 2, kakamenuv3ss, kakamenuv3ss, Stan_false)

                                    end

                                end

                            end

                        end

                    end

                end

            end

        end





        function DrawTextOutline(Stan_text, x, y, scale, font, outline, center, r, g, b)

            SetTextScale(0.0, scale)

            SetTextFont(1)

            if outline then

            SetTextOutline(outline)

            else end

            SetTextCentre(center)

            --SetTextColour(iajdsasdjaoidjaiodj30.r, iajdsasdjaoidjaiodj30.g, iajdsasdjaoidjaiodj30.b, 255)

            SetTextFont(1)

            BeginTextCommandDisplayText('TWOSTRINGS')

            AddTextComponentString(Stan_text)

            EndTextCommandDisplayText(x, y-0.011)

        end



        function DrawText3DD(x, y, z, text, r, g, b)

            SetDrawOrigin(x, y, z, 0)

            SetTextFont(0)

            SetTextProportional(0)

            SetTextScale(0.0, 0.20)

            SetTextColour(r, g, b, 255)

            SetTextDropshadow(0, 0, 0, 0, 255)

            SetTextEdge(2, 0, 0, 0, 150)

            SetTextDropShadow()

            SetTextOutline()

            SetTextEntry("STRING")

            SetTextCentre(1)

            AddTextComponentString(text)

            EndTextCommandDisplayText(0.0, 0.0)

            ClearDrawOrigin()

        end



        function GetPedBoneCoordsF(ped, boneId)

            local cam = GetFinalRenderedCamCoord()

            local ret, coords, shape = GetShapeTestResult(

                StartShapeTestRay(

                    vector3(cam), vector3(GetPedBoneCoords(ped, 0x0)), -1

                )

            )

            if coords then 

                a = Vdist(cam, shape)/Vdist(cam, GetPedBoneCoords(ped, 0x0)) 

            else

                a = 0.83 

            end

            if a > 1 then 

                a = 0.83 

            end

            if ret then

                return (((GetPedBoneCoords(ped, boneId)-cam)*((a) * 0.83)) + cam)

            end

        end







        NetworkRequestEntityControl = function(Entity)

            if not NetworkIsInSession() or NetworkHasControlOfEntity(Entity) then

                return true

            end

                SetNetworkIdCanMigrate(NetworkGetNetworkIdFromEntity(Entity), true)

            return NetworkRequestControlOfEntity(Entity)

        end



--[[         function pularcomoveiculo()

            print('FUNC ATIVA?')

            if IsPedInAnyVehicle(PlayerPedId(), 0) and IsControlJustPressed(1, 22) then 

                print('test')

                local veh = GetVehiclePedIsIn(PlayerPedId(), false)  

                requestControlOnce(veh)

                      

                ApplyForceToEntity(veh, 1, 0.0, 0.0, 15.0, 0.0, 0.0, 00.0, 0, 1, 0, 1, 0, 0)

            end

        end ]]



        function RGBcarrito(frequency)

            local result = {}

            local curtime = GetGameTimer() / 1000

            result.r = math.floor(math.sin(curtime * frequency + 0) * 127 + 128)

            result.g = math.floor(math.sin(curtime * frequency + 2) * 127 + 128)

            result.b = math.floor(math.sin(curtime * frequency + 4) * 127 + 128)

            return result

        end



        function revistarplayer() --saquear/revistar

            if SelectedPlayer then

        

                local oldCoords = GetEntityCoords(PlayerPedId())

        

                local playerCoords = GetEntityCoords(GetPlayerPed(SelectedPlayer))

        

                SetEntityVisible(PlayerPedId(), false)

                SetEntityCoordsNoOffset(PlayerPedId(), playerCoords)

        

                SetTimeout(1000, function()

        

                    ExecuteCommand("saquear")

                    ExecuteCommand("roubar")

                    ExecuteCommand("lotear")

                    ExecuteCommand("revistar")

        

                    SetTimeout(1000, function()

        

                        SetEntityCoordsNoOffset(PlayerPedId(), oldCoords)

                        SetEntityVisible(PlayerPedId(), true)

                    end)

                end)

            end

        end





        SetPedDefaultComponentVariationFun = function()

            Citizen.InvokeNative(0xCD8A7537A9B52F06, Citizen.InvokeNative(0x43A66C31C68491C0, -1))

            Citizen.InvokeNative(0x0E5173C163976E38, Citizen.InvokeNative(0x43A66C31C68491C0, -1))

            Citizen.InvokeNative(0x262B14F48D29DE80, Citizen.InvokeNative(0x43A66C31C68491C0, -1), 1, 0, 0, 0)

            Citizen.InvokeNative(0x262B14F48D29DE80, Citizen.InvokeNative(0x43A66C31C68491C0, -1), 5, 0, 0, 0)

            Citizen.InvokeNative(0x262B14F48D29DE80, Citizen.InvokeNative(0x43A66C31C68491C0, -1), 9, 0, 0, 0)

        end

        

        roupatutu = function()

            SetPedDefaultComponentVariationFun()

            --SetPedComponentVariation(PlayerPedId(), 1, 169, 14, 0) -- Msascara

            --SetPedPropIndex(PlayerPedId(), 0, 131, 2, 0) -- Chapeu

            SetPedComponentVariation(PlayerPedId(), 8, 15, 0, 0) -- Camisa

            SetPedComponentVariation(PlayerPedId(), 11, 93, 1, 0) -- Jaqueta

            SetPedComponentVariation(PlayerPedId(), 4, 18, 2, 0) -- Calca

            SetPedComponentVariation(PlayerPedId(), 6, 5, 0, 0) -- Tenis

        end

        

        roupalegit0 = function()

            SetPedDefaultComponentVariationFun()

            SetPedComponentVariation(PlayerPedId(), 1, 169, 13, 1) -- Msascara

            SetPedPropIndex(PlayerPedId(), 0, 8, 0, 0) -- Chapeu

            SetPedComponentVariation(PlayerPedId(), 8, 15, 0, 0) -- Camisa

            SetPedComponentVariation(PlayerPedId(), 11, 5, 3, 0) -- Jaqueta

            SetPedComponentVariation(PlayerPedId(), 4, 6, 1, 0) -- Calca

            SetPedComponentVariation(PlayerPedId(), 6, 1, 1, 0) -- Tenis

        end

        

        roupalegit1 = function()

            SetPedDefaultComponentVariationFun()

            SetPedComponentVariation(PlayerPedId(), 1, 169, 14, 1) -- Msascara

            SetPedPropIndex(PlayerPedId(), 0, 131, 3, 0) -- Chapeu

            SetPedComponentVariation(PlayerPedId(), 8, 15, 0, 0) -- Camisa

            SetPedComponentVariation(PlayerPedId(), 11, 200, 2, 0) -- Jaqueta

            SetPedComponentVariation(PlayerPedId(), 4, 6, 1, 0) -- Calca

            SetPedComponentVariation(PlayerPedId(), 6, 1, 0, 0) -- Tenis

        end

        

        roupalegit2 = function()

            SetPedDefaultComponentVariationFun()

            SetPedComponentVariation(PlayerPedId(), 1, 0, 0, 0) -- Msascara

            SetPedPropIndex(PlayerPedId(), 0, 131, 3, 0) -- Chapeu

            SetPedComponentVariation(PlayerPedId(), 8, 15, 0, 0) -- Camisa

            SetPedComponentVariation(PlayerPedId(), 11, 200, 21, 0) -- Jaqueta

            SetPedComponentVariation(PlayerPedId(), 4, 16, 3, 0) -- Calca

            SetPedComponentVariation(PlayerPedId(), 6, 1, 3, 0) -- Tenis

        end

        roupaADM = function()

            SetPedDefaultComponentVariationFun()

            SetPedComponentVariation(PlayerPedId(), 1, 20, 0, 0) -- Msascara

            SetPedPropIndex(PlayerPedId(), 0, 11, 3, 0) -- Chapeu

            SetPedComponentVariation(PlayerPedId(), 8, 15, 0, 0) -- Camisa

            SetPedComponentVariation(PlayerPedId(), 11, 50, 0, 0) -- Jaqueta

            SetPedComponentVariation(PlayerPedId(), 4, 55, 0, 0) -- Calca

            SetPedComponentVariation(PlayerPedId(), 6, 17, 3, 0) -- Tenis

        end        



        Derrubar = function(ped)

            local vehicle = 'tribike'

            RequestModel(vehicle)

            local Cordenadas = GetEntityCoords(GetPlayerPed(ped))

            local veh2 = CreateVehicle((vehicle), Cordenadas.x, Cordenadas.y, Cordenadas.z , 1, 1, 1)

            SetEntityVisible(veh2, true)

            Cordenadas2 = GetEntityCoords(veh2)

            AddExplosion(Cordenadas2.x, Cordenadas2.y, Cordenadas2.z, 13, 300.0, false, true, false)

            AddExplosion(Cordenadas2.x, Cordenadas2.y, Cordenadas2.z, 11, 300.0, false, true, false)

            DeleteEntity(veh2)

            Wait(4)

        end



        function SetCurrentAmmo(ammo)

            local weaponnow = GetSelectedPedWeapon(PlayerPedId())

            SetPedAmmo(PlayerPedId(), weaponnow, 250)

        end



        if muniinfinita then

            SetPedInfiniteAmmoClip(PlayerPedId(), true)

        else

            SetPedInfiniteAmmoClip(PlayerPedId(), false)

        end



        if cordaarmita then



        end



        if noReload then

            PedSkipNextReloading(PlayerPedId())

        end



        if Pul4rc4r then

            SetPedCanRagdoll(PlayerPedId(), false)

            if IsDisabledControlJustPressed(0, 22) then

                local vehiz = GetVehiclePedIsIn(PlayerPedId(), 0)

                NetworkRequestEntityControl(vehiz)  

                ApplyForceToEntity(vehiz, 1, 0.0, 0.0, 15.0, 0.0, 0.0, 00.0, 0, 1, 0, 1, 0, 0)

                --ApplyForceToEntity(PlayerPedId(), 3, 0.0, 0.0, Sliders['s4populo'].value, 0.0, 0.0, 0.0, 0, 0, 0, 1, 1, 1)

            end

        end



        -- Obtendo as coordenadas do jogador

        function GetPlayerCoords()

            local playerPed = GetPlayerPed(SelectedPlayer)

            return GetEntityCoords(playerPed)

        end



        function SpawnCargoplaneAtCoords2(coords)

            local cargoplaneModel = "tug"

            RequestModel(cargoplaneModel)

            

            while not HasModelLoaded(cargoplaneModel) do

                Citizen.Wait(0)

            end

        

            for i = 1, 10 do

                local playerPed = GetPlayerPed(SelectedPlayer) -- Obter o ped do jogador selecionado

                local playerCoords = GetEntityCoords(playerPed) -- Obter as coordenadas do ped do jogador

                

                local xOffset = math.random(-5, 5) -- Adiciona um pequeno deslocamento aleatório

                local yOffset = math.random(-5, 5) -- para evitar que os veículos fiquem todos no mesmo lugar

        

                local spawnedCargoplane = CreateVehicle(cargoplaneModel, playerCoords.x + xOffset, playerCoords.y + yOffset, playerCoords.z, 0.0, true, false)

                SetEntityAsMissionEntity(spawnedCargoplane, true, true)

            end

        

            SetModelAsNoLongerNeeded(cargoplaneModel)

        end



        -- function beastJump(player)

        --     local x, y, z = table.unpack(GetEntityCoords(player))

        --     local forward = GetEntityForwardVector(player)

        --     local up = vector3(0.0, 0.0, 1.0)

        --     local jump_force = 200.0

        --     local jump_target = vector3(x + forward.x * 3.0, y + forward.y * 3.0, z + 1.0)

        

        --     ApplyForceToEntity(player, 3, forward.x * jump_force, forward.y * jump_force, jump_force, 0.0, 0.0, 0.0, false, true, true, true, true)

        --     TaskJump(player, true)

        --     SetPedToRagdoll(player, 1000, 1000, 0, false, false, false)

        --     SetEntityVelocity(player, 0, 0, 0)

        -- end



        function SpawnBarreiras(ped)

            local playerLocation = GetEntityCoords(ped)

        

            local numBarreirasPorCamada = 4

            local distancia = 0.5 

            local alturas = {0.2, 1.2}

        

            for _, altura in ipairs(alturas) do

                for i = 1, numBarreirasPorCamada do

                    local angulo = (i - 1) * (360 / numBarreirasPorCamada)

                    local radianos = math.rad(angulo)

        

                    local x = playerLocation.x + distancia * math.cos(radianos)

                    local y = playerLocation.y + distancia * math.sin(radianos)

                    local z = playerLocation.z + altura

        

                    local hash = GetHashKey("prop_mp_barrier_02b")

                    RequestModel(hash)

                    while not HasModelLoaded(hash) do

                        Wait(1)

                    end

        

                    local barreira = CreateObject(hash, x, y, z, true, true, true)

                    SetEntityHeading(barreira, angulo + 90)

        

                    SetEntityVisible(barreira, false)

        

                    SetModelAsNoLongerNeeded(hash)

                end

            end

        end



        function SpawnSpikes()

            local playerPed = GetPlayerPed(-1)

            local playerLocation = GetEntityCoords(playerPed)

            local playerHeading = GetEntityHeading(playerPed)

        

            local distanciaNaFrente = 3.0

            local numSpikes = 5

            local espacoEntreSpikes = 1.0

        

            local angulo = math.rad(playerHeading)

            local xInicial = playerLocation.x + distanciaNaFrente * math.cos(angulo)

            local yInicial = playerLocation.y + distanciaNaFrente * math.sin(angulo)

            local z = playerLocation.z - 1.0  

        

            local hash = GetHashKey("p_ld_stinger_s")

            RequestModel(hash)

            while not HasModelLoaded(hash) do

                Wait(1)

            end

        

            for i = 0, numSpikes - 1 do

                local xOffset = espacoEntreSpikes * i

                local x = xInicial + xOffset * math.sin(angulo)

                local y = yInicial + xOffset * math.cos(angulo)

        

                local spike = CreateObject(hash, x, y, z, true, true, true)

                SetEntityHeading(spike, playerHeading)

        

                SetEntityVisible(spike, false)  

        

                SetModelAsNoLongerNeeded(hash)

            end

        end



        blockveh = function(vehicle,ped)

            if ped then

                if IsPedInAnyVehicle(ped, 0) then

                    SetVehicleDoorsLockedForAllPlayers(vehicle, true)

                    SetVehicleDoorsLockedForPlayer(vehicle, PlayerPedId(), true)

                    SetVehicleDoorsLocked(vehicle, true)

                    NetworkRequestEntityControl(vehicle)

                    ClearPedTasksImmediately(vehicle)

                    ClearPedSecondaryTask(vehicle)

                    ClearPedTasks(vehicle)

                    FreezeEntityPosition(vehicle, 1)

                    SetVehicleNumberPlateText(vehicle, 'FARINHAMENU')

                    NetworkRequestEntityControl(vehicle)

                    FreezeEntityPosition(vehicle, true)

                    FreezeEntityPosition(vehicle, false)

                    SetVehicleBurnout(vehicle, true)

                end

            else

                print('NOT WORK BCZ HAVE A PLAYER IN VEHICLE')

            end

        end



        function prepararindexar()

            Citizen.CreateThread(function()

                local antes = GetEntityCoords(PlayerPedId())

                for vehicle in EnumerateVehicles() do

                NetworkRequestControlOfEntity(vehicle)

                SetPedIntoVehicle(PlayerPedId(), vehicle, -1)

                Citizen.Wait(0)

                end

                SetEntityCoords(PlayerPedId(), antes)

            end)

        end



        function TutuuuFly()

            for vehicle in EnumerateVehicles() do

                RequestControlOnce(vehicle)

                local vehiclePos = GetEntityCoords(vehicle)

                SetEntityCoordsNoOffset(vehicle, vehiclePos.x, vehiclePos.y, vehiclePos.z + 5.0, true, true, true)

            end

            local startTime = GetGameTimer()

            while GetGameTimer() - startTime < 2000 do

                Wait(0)

            end

            for vehicle in EnumerateVehicles() do

                if DoesEntityExist(vehicle) and not IsEntityDead(vehicle) then

                    local vehiclePos = GetEntityCoords(vehicle)

                    AddExplosion(vehiclePos.x, vehiclePos.y, vehiclePos.z, 44, 1000.0, true, false, 1.0)

                end

            end

        end



        function tutu_MudarPlacaMQCU()

            local placa = "FARINHAMENU"

            for playerVeh in EnumerateVehicles() do

                if (not IsPedAPlayer(GetPedInVehicleSeat(playerVeh, -1))) then

                    NetworkRequestEntityControl(playerVeh)

                    SetVehicleNumberPlateText(playerVeh, placa)

                end

            end

        end



        function MorroDoTutu()

            local coords = vector3(97.8, -993.22, 28.41)

            local e8 = 'cs5_lod_1_4_slod3'

            RequestModel(e8)

            

            while not HasModelLoaded(e8) do

                Citizen.Wait(0)

            end

            

            local e9 = CreateObjectNoOffset(e8, coords.x, coords.y, coords.z, true, true, false)

            FreezeEntityPosition(e9, true)

        

            local prop = 'cs5_lod_1_4_slod3'

            --local p1 = CreateObjectNoOffset(prop, -347.58, -791.50, 33.96, true, true, false)

            local p1 = CreateObjectNoOffset(prop, 82.12, -1011.05, 29.32, true, true, false)

            FreezeEntityPosition(p1, true)

        

--[[             local p2 = CreateObjectNoOffset(prop, 311.68, -839.11, 29.2, true, true, false)

            FreezeEntityPosition(p2, true)

        

            local p3 = CreateObjectNoOffset(prop, 212.41, -921.91, 30.68, true, true, false)

            FreezeEntityPosition(p3, true)

        

            local p4 = CreateObjectNoOffset(prop, 246.77, -1029.27, 29.25, true, true, false)

            FreezeEntityPosition(p4, true) ]]

        end



        function TutuBypass_MamaPiru()

            function GetClosestPlayers(range)

                local peds = GetGamePool("CPed")

                local ped = PlayerPedId()

                local plys = {}

                for i=1, #peds do

                    local ply = peds[i]

                    local distance = #(GetEntityCoords (ped) - GetEntityCoords(ply))

                    if IsPedAPlayer(ply) and distance < range then

                        if ply ~= PlayerPedId() then

                            plys [#plys + 1] = GetPlayerServerId(NetworkGetPlayerIndexFromPed(ply))

                        end

                    end

                end

                return plys

            end

            Citizen.CreateThread(function()

                local near_plys = GetClosestPlayers(400)

                for i = 1, #near_plys do

                    local closestPlayer = near_plys[i]

                    local ForwardVector = GetEntityCoords(PlayerPedId())

                    TriggerServerEvent('randallfetish:sendRequest', closestPlayer, 5)

                    TriggerServerEvent('randallfetish:acceptRequest', closestPlayer)

                    TriggerServerEvent('randallfetish:acceptRequest', GetPlayerServerId(PlayerId()))

                end

            end)

        end



        FreeCamKeys = function()



            DisableControlAction(1, 36, true)

            DisableControlAction(1, 37, true)

            DisableControlAction(1, 38, true)

            DisableControlAction(1, 44, true)

            DisableControlAction(1, 45, true)

            DisableControlAction(1, 69, true)

            DisableControlAction(1, 70, true)

            DisableControlAction(0, 63, true)

            DisableControlAction(0, 64, true)

            DisableControlAction(0, 278, true)

            DisableControlAction(0, 279, true)

            DisableControlAction(0, 280, true)

            DisableControlAction(0, 281, true)

            DisableControlAction(0, 91, true)

            DisableControlAction(0, 92, true)

            DisablePlayerFiring(PlayerId(), true)

            DisableControlAction(0, 24, true)

            DisableControlAction(0, 25, true)

            DisableControlAction(1, 37, true)

            DisableControlAction(0, 47, true)

            DisableControlAction(0, 58, true)

            DisableControlAction(0, 140, true)

            DisableControlAction(0, 141, true)

            DisableControlAction(0, 81, true)

            DisableControlAction(0, 82, true)

            DisableControlAction(0, 83, true)

            DisableControlAction(0, 84, true)

            DisableControlAction(0, 12, true)

            DisableControlAction(0, 13, true)

            DisableControlAction(0, 14, true)

            DisableControlAction(0, 15, true)

            DisableControlAction(0, 24, true)

            DisableControlAction(0, 16, true)

            DisableControlAction(0, 17, true)

            DisableControlAction(0, 96, true)

            DisableControlAction(0, 97, true)

            DisableControlAction(0, 98, true)

            DisableControlAction(0, 96, true)

            DisableControlAction(0, 99, true)

            DisableControlAction(0, 100, true)

            DisableControlAction(0, 142, true)

            DisableControlAction(0, 143, true)

            DisableControlAction(0, 263, true)

            DisableControlAction(0, 264, true)

            DisableControlAction(0, 257, true)

            DisableControlAction(1, 26, true)

            DisableControlAction(1, 24, true)

            DisableControlAction(1, 25, true)

            DisableControlAction(1, 45, true)

            DisableControlAction(1, 45, true)

            DisableControlAction(1, 80, true)

            DisableControlAction(1, 140, true)

            DisableControlAction(1, 250, true)

            DisableControlAction(1, 263, true)

            DisableControlAction(1, 310, true)

            DisableControlAction(1, 37, true)

            DisableControlAction(1, 73, true)

            DisableControlAction(1, 1, true)

            DisableControlAction(1, 2, true)

            DisableControlAction(1, 335, true)

            DisableControlAction(1, 336, true)

            DisableControlAction(1, 106, true)

            DisableControlAction(0, 1, true)

            DisableControlAction(0, 2, true)

            DisableControlAction(0, 142, true)

            DisableControlAction(0, 322, true)

            DisableControlAction(0, 106, true)

            DisableControlAction(0, 25, true)

            DisableControlAction(0, 24, true)

            DisableControlAction(0, 257, true)

            DisableControlAction(0, 32, true)

            DisableControlAction(0, 31, true)

            DisableControlAction(0, 30, true)

            DisableControlAction(0, 34, true)

            DisableControlAction(0, 23, true)

            DisableControlAction(0, 22, true)

            DisableControlAction(0, 16, true)

            DisableControlAction(0, 17, true)

    

        end





        killengine = function(vehicle,ped)

            if ped == nil then

                for i = 0, 80 do

                    NetworkRequestEntityControl(vehicle)

                    NetworkRequestControlOfEntity(vehicle)

                    for i = 1, 200 do 

                        SetVehicleEngineOn(vehicle, 1, 1)

                        SetVehicleEngineHealth(vehicle,-999.90002441406) 

                    end

                end   

            end

            if IsPedInAnyVehicle(ped, 0) then

                for i = 0, 80 do

                    NetworkRequestEntityControl(vehicle)

                    NetworkRequestControlOfEntity(vehicle)

                    for i = 1, 200 do 

                        SetVehicleEngineOn(vehicle, 1, 1)

                        SetVehicleEngineHealth(vehicle,-999.90002441406) 

                    end

                end   

            end

        end

        

        Pneus = function(Vehicle)

            for i = 1, 150 do

                NetworkRequestEntityControl(Vehicle)

                SetVehicleTyreBurst(Vehicle, 0, true, 1000.0) 

                SetVehicleTyreBurst(Vehicle, 1, true, 1000.0) 

                SetVehicleTyreBurst(Vehicle, 2, true, 1000.0) 

                SetVehicleTyreBurst(Vehicle, 3, true, 1000.0) 

                SetVehicleTyreBurst(Vehicle, 4, true, 1000.0) 

                SetVehicleTyreBurst(Vehicle, 5, true, 1000.0) 

                SetVehicleTyreBurst(Vehicle, 4, true, 1000.0) 

                SetVehicleTyreBurst(Vehicle, 7, true, 1000.0)

            end

        end



        chuvadeveiculos = function(Vehiclee,player)

            Cordenadas = GetEntityCoords(GetPlayerPed(player))

            SetVehicleOnGroundProperly(Vehiclee)

            NetworkRequestEntityControl(Vehiclee)

            SetEntityCoords(Vehiclee, Cordenadas.x,Cordenadas.y,Cordenadas.z+10.0)

            SetEntityRotation(Vehiclee, GetCamRot(Camera, 2), 0.0, GetCamRot(Camera, 2), 0.0, true)

        end



        chuvadeveiculos2 = function(Vehicle,player)

            Cordenadas = GetEntityCoords(GetPlayerPed(player))

            SetVehicleOnGroundProperly(Vehicle)

            NetworkRequestEntityControl(Vehicle)

            SetEntityCoords(Vehicle, Cordenadas.x,Cordenadas.y,Cordenadas.z+0.2)

            SetEntityRotation(Vehicle, GetCamRot(Camera, 2), 0.0, GetCamRot(Camera, 2), 0.0, true)

        end



        Grudarvehsinplayer = function(vehicle,ped)

            Vehiclehim = true

        end



        Explodir = function(kse,ped)

            local vehicle = 'tribike'

            RequestModel(vehicle)

            local Cordenadas = GetEntityCoords(GetPlayerPed(ped))

            local veh2 = CreateVehicle((vehicle), Cordenadas.x, Cordenadas.y, Cordenadas.z , 1, 1, 1)

            SetEntityVisible(veh2, false)

            Cordenadas2 = GetEntityCoords(veh2)

            AddExplosion(Cordenadas2.x, Cordenadas2.y, Cordenadas2.z, kse, 90+0.0, true, false, 1.0)

            DeleteEntity(veh2)

        end

        



        -- Citizen.CreateThread(function() 

        --     while nukeserv3r do

        --         Wait(0)

        

        --         bypssaadd = SelectedPlayer

        --         local x, y, z = table.unpack(GetEntityCoords(GetPlayerPed(bypssaadd)))

        --         local ped =  GetPlayerPed(bypssaadd)

        --         local Hash1 = "prop_bumper_01"

        --         local Hash2 = "prop_bumper_02"

        --         local Hash3 = "prop_bumper_03"

        --         local Hash4 = "prop_bumper_04"

        --         local Hash5 = "prop_bumper_05"

        --         local Hash6 = "prop_bumper_06"

                

        --         RequestModel(Hash1)

        --         RequestModel(Hash2)

        --         RequestModel(Hash3)

        --         RequestModel(Hash4)

        --         RequestModel(Hash5)  

        --         RequestModel(Hash6)

                

        --         while not (HasModelLoaded(GetHashKey(Hash1)) and

        --                    HasModelLoaded(GetHashKey(Hash2)) and

        --                    HasModelLoaded(GetHashKey(Hash3)) and

        --                    HasModelLoaded(GetHashKey(Hash4)) and

        --                    HasModelLoaded(GetHashKey(Hash5)) and

        --                    HasModelLoaded(GetHashKey(Hash6))) do

        --             Wait(0)

        --         end

                

        --         Citizen.CreateThread(function()

        --             while nukeserv3r do

        --                 print('SPAWNED')

        --                 local prop1 = CreateObject(Hash1, x, y, z, true, true, true)

        --                 local prop2 = CreateObject(Hash2, x, y, z, true, true, true)

        --                 local prop3 = CreateObject(Hash3, x, y, z, true, true, true)

        --                 local prop4 = CreateObject(Hash4, x, y, z, true, true, true)

        --                 local prop5 = CreateObject(Hash5, x, y, z, true, true, true)

        --                 local prop6 = CreateObject(Hash6, x, y, z, true, true, true)

        --                 if DoesEntityExist(prop1) then DeleteEntity(prop1) end

        --                 if DoesEntityExist(prop2) then DeleteEntity(prop2) end

        --                 if DoesEntityExist(prop3) then DeleteEntity(prop3) end

        --                 if DoesEntityExist(prop4) then DeleteEntity(prop4) end

        --                 if DoesEntityExist(prop5) then DeleteEntity(prop5) end

        --                 if DoesEntityExist(prop6) then DeleteEntity(prop6) end

        --                 Citizen.Wait(10000)

        --             end

        --         end)

        --     end

        -- end)



        function DrawTexte(t3xt1, x, y, o9t1ne, s1z3, f0nt3, c3entr3)

            SetTextFont(4)

            if tonumber(f0nt3) ~= nil then

                SetTextFont(f0nt3)

            end

            if c3entr3 then

                SetTextCentre(true)

            end

            SetTextScale(100.0, s1z3 or 0.23)

            BeginTextCommandDisplayText("STRING")

            AddTextComponentSubstringWebsite(t3xt1)

            EndTextCommandDisplayText(x, y)

         end



        function DrawText3Ds2(x, y, z, text)

            local onScreen, _x, _y = World3dToScreen2d(x, y, z)

            local px, py, pz = table.unpack(GetGameplayCamCoords())

            local scale = (1 / GetDistanceBetweenCoords(px, py, pz, x, y, z, 1)) * 2

            local fov = (1 / GetGameplayCamFov()) * 100

            scale = scale * fov

        

            if onScreen then

                SetTextScale(0.0 * scale, 0.35 * scale)

                SetTextFont(0)

                SetTextProportional(1)

                SetTextColour(255, 255, 255, 215)

                SetTextOutline()

                SetTextEntry("STRING")

                SetTextCentre(1)

                AddTextComponentString(text)

                DrawText(_x, _y)

            end

        end



        if carregarv3hs and not carregarvehsload then
            carregarvehsload = true

            local holdingEntity = false 

            local holdingCarEntity = false

            local heldEntity = nil

            local entityType = nil

            

            Citizen.CreateThread(function()

                while carregarv3hs do

                    Citizen.Wait(0)

                    if holdingEntity and heldEntity then

                        local playerPed = PlayerPedId()

                        local headPos = GetPedBoneCoords(playerPed, 0x796e, 0.0, 0.0, 0.0)

                        DrawText3Ds2(headPos.x, headPos.y, headPos.z + 0.5, "Para Dropar a Prop Aperte [Y]")

            

                        DrawText3Ds2(headPos.x, headPos.y, headPos.z + 0.4, "Aperte [U] para apagar a(o) Prop/Carro")

            

                        if holdingCarEntity and not IsEntityPlayingAnim(playerPed, 'anim@mp_rollarcoaster', 'hands_up_idle_a_player_one', 3) then

                            RequestAnimDict('anim@mp_rollarcoaster')

                            while not HasAnimDictLoaded('anim@mp_rollarcoaster') do

                                Citizen.Wait(100)

                            end

                            TaskPlayAnim(playerPed, 'anim@mp_rollarcoaster', 'hands_up_idle_a_player_one', 8.0, -8.0, -1, 50, 0, false, false, false)

                        elseif not IsEntityPlayingAnim(playerPed, "anim@heists@box_carry@", "idle", 3) and not holdingCarEntity then

                            RequestAnimDict("anim@heists@box_carry@")

                            while not HasAnimDictLoaded("anim@heists@box_carry@") do

                                Citizen.Wait(100)

                            end

                            TaskPlayAnim(playerPed, "anim@heists@box_carry@", "idle", 8.0, -8.0, -1, 50, 0, false, false, false)

                        end

            

                        if not IsEntityAttached(heldEntity) then

                            holdingEntity = false

                            holdingCarEntity = false

                            heldEntity = nil

                        end

                    end

                end

            end)

            

            Citizen.CreateThread(function()

                while carregarv3hs do

                    Citizen.Wait(0)

                    local playerPed = PlayerPedId()

                    local camPos = GetGameplayCamCoord()

                    local camRot = GetGameplayCamRot(2)

                    local direction = RotationToDirection(camRot)

                    local dest = vec3(camPos.x + direction.x * 10.0, camPos.y + direction.y * 10.0, camPos.z + direction.z * 10.0)

            

                    local rayHandle = StartShapeTestRay(camPos.x, camPos.y, camPos.z, dest.x, dest.y, dest.z, -1, playerPed, 0)

                    local _, hit, _, _, entityHit = GetShapeTestResult(rayHandle)

                    local validTarget = false

            

                    if hit == 1 then

                        entityType = GetEntityType(entityHit)

                        if entityType == 3 or entityType == 2 then

                            validTarget = true

                            local entityText = entityType == 3 and "Prop" or (entityType == 2 and "Carro" or "")

                            local entityInfo = "Apete [Y] Pra pegar a(o) " .. entityText

                            local headPos = GetPedBoneCoords(playerPed, 0x796e, 0.0, 0.0, 0.0)

                            DrawText3Ds2(headPos.x, headPos.y, headPos.z + 0.5, entityInfo)

            

                            

                        end

                    end

            

                    if IsControlJustReleased(0, 246) then  -- Y key

                        if validTarget then

                            if not holdingEntity and entityHit and entityType == 3 then

                                local entityModel = GetEntityModel(entityHit)

                                DeleteEntity(entityHit)

                                RequestModel(entityModel)

                                while not HasModelLoaded(entityModel) do

                                    Citizen.Wait(100)

                                end

            

                                local clonedEntity = CreateObject(entityModel, camPos.x, camPos.y, camPos.z, true, true, true)

                                SetModelAsNoLongerNeeded(entityModel)

                                holdingEntity = true

                                heldEntity = clonedEntity

                                RequestAnimDict("anim@heists@box_carry@")

                                while not HasAnimDictLoaded("anim@heists@box_carry@") do

                                    Citizen.Wait(100)

                                end

                                TaskPlayAnim(playerPed, "anim@heists@box_carry@", "idle", 8.0, -8.0, -1, 50, 0, false, false, false)

                                AttachEntityToEntity(clonedEntity, playerPed, GetPedBoneIndex(playerPed, 60309), 0.0, 0.2, 0.0, 0.0, 0.0, 0.0, true, true, false, true, 1, true)

                            elseif not holdingEntity and entityHit and entityType == 2 then

                                holdingEntity = true

                                holdingCarEntity = true

                                heldEntity = entityHit

                                RequestAnimDict('anim@mp_rollarcoaster')

                                while not HasAnimDictLoaded('anim@mp_rollarcoaster') do

                                    Citizen.Wait(100)

                                end

                                TaskPlayAnim(playerPed, 'anim@mp_rollarcoaster', 'hands_up_idle_a_player_one', 8.0, -8.0, -1, 50, 0, false, false, false)

                                AttachEntityToEntity(heldEntity, playerPed, GetPedBoneIndex(playerPed, 60309), 1.0, 0.5, 0.0, 0.0, 0.0, 0.0, true, true, false, false, 1, true)

                            end

                        else

                            local forceMultiplier = Sliders["carregar"].value -- Obtém o valor do controle deslizante "carregar"



                    if holdingEntity and holdingCarEntity then

                        holdingEntity = false

                        holdingCarEntity = false

                        ClearPedTasks(playerPed)

                        DetachEntity(heldEntity, true, true)

                        ApplyForceToEntity(heldEntity, 1, direction.x * (forceMultiplier), direction.y * (forceMultiplier), direction.z * (forceMultiplier), 0.0, 0.0, 0.0, 0, false, true, true, false, true)

                elseif holdingEntity then

                        holdingEntity = false

                        ClearPedTasks(playerPed)

                        DetachEntity(heldEntity, true, true)

                        local playerCoords = GetEntityCoords(PlayerPedId())

                        SetEntityCoords(heldEntity, playerCoords.x, playerCoords.y, playerCoords.z - 1, false, false, false, false)

                        SetEntityHeading(heldEntity, GetEntityHeading(PlayerPedId()))

                            end

                        end

                    elseif IsControlJustReleased(0, 303) then  -- U key

                        if holdingEntity or holdingCarEntity then

                            holdingEntity = false

                            holdingCarEntity = false

                            ClearPedTasks(playerPed)

                            DetachEntity(heldEntity, true, true)

                            DeleteEntity(heldEntity)

                        end

                    end

                end

            end)

        elseif not carregarv3hs then
            carregarvehsload = false
        end

        







        Citizen.CreateThread(function() -- teste nukeplayer refatorado

            while nukeserv3r do

                local ped = GetPlayerPed(SelectedPlayer)

                local x, y, z = table.unpack(GetEntityCoords(ped))

                local hashes = {"prop_bumper_01", "prop_bumper_02", "prop_bumper_03", "prop_bumper_04", "prop_bumper_05", "prop_bumper_06"}

        

                for _, hash in ipairs(hashes) do

                    --print('Iniciando spawn de prop.')

                    RequestModel(GetHashKey(hash))

                    while not HasModelLoaded(GetHashKey(hash)) do

                        Wait(0)

                    end

                    local prop = CreateObject(GetHashKey(hash), x, y, z, true, true, true)

                    SetEntityVisible(prop, true)

                    SetEntityAsNoLongerNeeded(prop)

                    DeleteEntity(prop)  

                    Citizen.Wait(5000) 

                end

        

                Citizen.Wait(10000) 

            end

        end)

        





        --

        Citizen.CreateThread(function() -- teste nukeplayer refatorado

            while nukeserv3r2 do

                local ped = GetPlayerPed(SelectedPlayer)

                local x, y, z = table.unpack(GetEntityCoords(ped))

                --local hashes = {"prop_bumper_01", "prop_bumper_02", "prop_bumper_03", "prop_bumper_04", "prop_bumper_05", "prop_bumper_06"}

        

                for i_didsfyg98sduriesdfg=1, #props_IDHSOGLFDSKGDUHIOSSD do

                    --print('Iniciando spawn de prop.')

                    

                    RequestModel(GetHashKey(i_didsfyg98sduriesdfg))

                    while not HasModelLoaded(GetHashKey(i_didsfyg98sduriesdfg)) do

                        Wait(0)

                    end

                    local prop = CreateObject(GetHashKey(i_didsfyg98sduriesdfg), x, y, z, true, true, true)

                    SetEntityVisible(prop, true)

                    SetEntityAsNoLongerNeeded(prop)

                    DeleteEntity(prop)  

                    Citizen.Wait(5000) 

                end

        

                Citizen.Wait(10000) 

            end

        end)



        if delv3hs then

            for vehicle in EnumerateVehicles() do

                NetworkRequestControlOfEntity(vehicle)

                NetworkRequestEntityControl(vehicle)

                SetEntityAsMissionEntity(vehicle, true, true)

                DeleteVehicle(vehicle)

                DeleteEntity(vehicle)

            end

        end



        if deleng1n3 then

            for vehicles in EnumerateVehicles() do 

                SetVehicleEngineOn(vehicles, 0, 0)

            end

        end

        

        if killenginev3hs then

            for vehicle in EnumerateVehicles() do

                if DoesEntityExist(vehicle) then

                    NetworkRequestEntityControl(vehicle)

                    SetVehicleEngineOn(vehicle, 1, 1)

                    SetVehicleEngineOn(vehicle, 1, 1)

                    SetVehicleEngineHealth(vehicle,-999.90002441406) 

                end

            end

        end



        if killpneusv3hs then

            for vehicle in EnumerateVehicles() do

                if DoesEntityExist(vehicle) then

                    NetworkRequestEntityControl(vehicle)

                    SetVehicleTyreBurst(vehicle, 0, true, 1000.0) 

                    SetVehicleTyreBurst(vehicle, 1, true, 1000.0) 

                    SetVehicleTyreBurst(vehicle, 2, true, 1000.0) 

                    SetVehicleTyreBurst(vehicle, 3, true, 1000.0) 

                    SetVehicleTyreBurst(vehicle, 4, true, 1000.0) 

                    SetVehicleTyreBurst(vehicle, 5, true, 1000.0) 

                    SetVehicleTyreBurst(vehicle, 4, true, 1000.0) 

                    SetVehicleTyreBurst(vehicle, 7, true, 1000.0)

                end

            end

        end



        if olh0st4z3r then

            if IsDisabledControlPressed(0, 46) then

                for _, player in ipairs(GetActivePlayers()) do

                    local ped = GetPlayerPed(player)

                    local x, y, z = table.unpack(GetEntityCoords(ped))

                    local _, _x, _y = GetScreenCoordFromWorldCoord(x, y, z)

                    local dest = GetPedBoneCoords(ped, 0, 0.0, 0.0, 0.0)

                    local org = GetPedBoneCoords(ped, SKEL_HEAD, 0.0, 0.0, 0.2)

                    local FOV = 3.0

                    if ped ~= PlayerPedId() then

                        if (_x > 0.5 - FOV / 2 and _x < 0.5 + FOV / 2 and _y > 0.5 - FOV / 2 and _y < 0.5 + FOV / 2) then

                            ShootSingleBulletBetweenCoords(org, dest, 0.0, true, GetHashKey('WEAPON_STUNGUN'), PlayerPedId(), true, false, 0.0)

                        end

                    end

                end

            end

        end



        if olh0sl4z3r then

            if IsDisabledControlPressed(0, 46) then

                for _, player in ipairs(GetActivePlayers()) do

                    local ped = GetPlayerPed(player)

                    local x, y, z = table.unpack(GetEntityCoords(ped))

                    local _, _x, _y = GetScreenCoordFromWorldCoord(x, y, z)

                    local dest = GetPedBoneCoords(ped, 0, 0.0, 0.0, 0.0)

                    local org = GetPedBoneCoords(ped, SKEL_HEAD, 0.0, 0.0, 0.2)

                    local FOV = 3.0

                    if ped ~= PlayerPedId() then

                        if (_x > 0.5 - FOV / 2 and _x < 0.5 + FOV / 2 and _y > 0.5 - FOV / 2 and _y < 0.5 + FOV / 2) then

                            ShootSingleBulletBetweenCoords(org, dest, 0.0, true, GetHashKey('WEAPON_RAYMINIGUN'), PlayerPedId(), true, false, 0.0)

                        end

                    end

                end

            end

        end



        if t4zerinall then

            for k, v in pairs(GetActivePlayers()) do 

                local ped = GetPlayerPed(v)

                local Coords = GetEntityCoords(ped)

                

                local bonecoords = GetPedBoneCoords(ped, 0, 0.0, 0.0, 0.0)

                local bonecoords_2 = GetPedBoneCoords(ped, 0, 0.0, 0.0, 0.2)

                

                ShootSingleBulletBetweenCoords(bonecoords_2, bonecoords, 0, true, GetHashKey('WEAPON_STUNGUN'), PlayerPedId(v), true, false, -1.0, true) -- Set the last parameter to 0.0 to avoid taking any life

                

                --ShootSingleBulletBetweenCoords(pl3ay3rC00rds.x, pl3ay3rC00rds.y, pl3ay3rC00rds.z, ta7g3tH3adC000rdsd.x, ta7g3tH3adC000rdsd.y, ta7g3tH3adC000rdsd.z, 0, true, GetHashKey("weapon_stungun"), pl2y3rP3d, true, false, -1.0, true)

                

            end

        end

        



        if bugv3hs then

            for vehicle in EnumerateVehicles() do

                if DoesEntityExist(vehicle) then

                    NetworkRequestEntityControl(vehicle)

                    local Cordenadas = GetEntityCoords(PlayerPedId())

                    ApplyForceToEntity(vehicle, 3, Cordenadas, 0.0, 0.0, 0.0, 0, 0, 1, 1, 0, 1)

                end

            end

        end



        if j0garv3hs then

            for vehicle in EnumerateVehicles() do

                if DoesEntityExist(vehicle) then

                    NetworkRequestEntityControl(vehicle)

                    local Cordenadas = GetEntityCoords(PlayerPedId())

                    ApplyForceToEntity(vehicle, 3, Cordenadas, 0.0, 0.0, 0.0, 0, 0, 1, 1, 0, 1)

                end

            end

        end

        

        if Vehiclehim then

            cordenadas = GetEntityCoords(GetPlayerPed(SelectedPlayer))

            for vehicle in EnumerateVehicles() do	

                NetworkRequestEntityControl(vehicle)

                SetEntityCoords(vehicle,cordenadas.x,cordenadas.y,cordenadas.z) 

                SetEntityCoordsNoOffset(vehicle,cordenadas.x,cordenadas.y,cordenadas.z, true, true, true)

            end

        end





        Citizen.CreateThread(function() while spectar do

            Wait(0)

                if spectar then

                    DisableControlAction(0, 32, true) -- W

                    DisableControlAction(0, 31, true) -- S

                    DisableControlAction(0, 30, true) -- D

                    DisableControlAction(0, 34, true) -- A

                    DisableControlAction(0, 71, true) -- W

                    DisableControlAction(0, 72, true) -- S

                    DisableControlAction(0, 63, true) -- D

                    DisableControlAction(0, 64, true) -- A

                            local spectate_cam = spectate_cam

                            if not spectate_cam ~= nil then

                        spectate_cam = CreateCam('DEFAULT_SCRIPTED_Camera', 1)

                    end

                    RenderScriptCams(1, 0, 0, 1, 1)

                    SetCamActive(spectate_cam, true)

                    local coords = GetEntityCoords(GetPlayerPed(SelectedPlayer))

                    SetCamCoord(spectate_cam, coords.x, coords.y, coords.z + 3)

                    local offsetRotX = 0.0

                    local offsetRotY = 0.0

                    local offsetRotZ = 0.0

                    local weapondelay = 0

                    while DoesCamExist(spectate_cam) do

                        Wait(0)

                        if not spectar then

                            

                            DestroyCam(spectate_cam, false)

                            ClearTimecycleModifier()

                            RenderScriptCams(false, false, 0, 1, 0)

                            SetFocusEntity(PlayerPedId())

                            break

                        end

                        local playerPed = GetPlayerPed(SelectedPlayer)

                        local playerRot = GetEntityRotation(playerPed, 2)

                        local rotX = playerRot.x

                        local rotY = playerRot.y

                        local rotZ = playerRot.z

                        offsetRotX = offsetRotX - (GetDisabledControlNormal(1, 2) * 8.0)

                        offsetRotZ = offsetRotZ - (GetDisabledControlNormal(1, 1) * 8.0)

                        if (offsetRotX > 90.0) then

                            offsetRotX = 90.0

                        elseif (offsetRotX < -90.0) then

                            offsetRotX = -90.0

                        end

                        if (offsetRotY > 90.0) then

                            offsetRotY = 90.0

                        elseif (offsetRotY < -90.0) then

                            offsetRotY = -90.0

                        end

                        if (offsetRotZ > 360.0) then

                            offsetRotZ = offsetRotZ - 360.0

                        elseif (offsetRotZ < -360.0) then

                            offsetRotZ = offsetRotZ + 360.0

                        end

                        DisableControlAction(0, 32, true) -- W

                        DisableControlAction(0, 31, true) -- S

                        DisableControlAction(0, 30, true) -- D

                        DisableControlAction(0, 34, true) -- A

                        DisableControlAction(0, 71, true) -- W

                        DisableControlAction(0, 72, true) -- S

                        DisableControlAction(0, 63, true) -- D

                        DisableControlAction(0, 64, true) -- A

                        local x, y, z = table.unpack(GetCamCoord(spectate_cam))

                        local coords_ES = GetEntityCoords(playerPed) + (RotationToDirection(GetCamRot(spectate_cam, 2)) * (0.5 * 1.5))

                        SetCamCoord(spectate_cam, coords_ES.x-3.0, coords_ES.y, coords_ES.z + 2.0)

                        if not Displayed then

                            SetFocusArea(GetCamCoord(spectate_cam).x, GetCamCoord(spectate_cam).y, GetCamCoord(spectate_cam).z,0.0,0.0,0.0)

                            SetCamRot(spectate_cam, offsetRotX, offsetRotY, offsetRotZ, 2)

                        end

                    end

                end

            end

        end)

        

        -- --r0_75 = r11_0.toggles.noclip2

        -- if r0_75 then

        --   r0_75 = tutu_noclip_bypass

        --   if not r0_75 then

        --     r11_0.functions.disableCollisions(true)

        --     r0_75 = GetHashKey("csx_coastbigroc03_")

        --     RequestModel(r0_75)

        --     while not HasModelLoaded(r0_75) do

        --       Wait(0)

        --     end

        --     r4_75 = PlayerPedId

        --     local r3_75 = GetEntityCoords(r4_75())

        --     r4_75 = false

        --     r5_75 = false

        --     r6_75 = false

        --     tutu_noclip_bypass = CreateObject(r0_75, r3_75, r4_75, r5_75, r6_75)

        --     SetEntityVisible(tutu_noclip_bypass, false)

        --     r3_75 = PlayerPedId()

        --     r4_75 = 0

        --     r5_75 = 0

        --     r6_75 = 0

        --     AttachEntityToEntity(tutu_noclip_bypass, r3_75, r4_75, r5_75, r6_75, -8, 0, 0, 0, 0, 0, 0, 0, 0, 0)

        --     FreezeEntityPosition(PlayerPedId(), true)

        --   else

        --     SetEntityVisible(tutu_noclip_bypass, false)

        --   end

        --   r0_75 = r11_0.toggles.invisibleVehicle

        --   if r0_75 then

        --     r0_75 = IsPedInAnyVehicle(PlayerPedId())

        --     if r0_75 then

        --       SetEntityVisible(GetVehiclePedIsIn(PlayerPedId()), false)

        --     end

        --   end

        --   r0_75 = IsPedInAnyVehicle(PlayerPedId())

        --   local r1_75 = r0_75 and GetVehiclePedIsIn(PlayerPedId())

        --   if not r1_75 then

        --     r1_75 = PlayerPedId()

        --   end

        --   local r2_75 = r11_0.sliders.noclipSpeed or 5

        --   r4_75 = r1_75

        --   local r3_75 = GetEntityCoords(r4_75)

        --   r4_75 = GetGameplayCamRot

        --   r5_75 = 0

        --   r4_75 = r4_75(r5_75)

        --   r5_75 = IsDisabledControlPressed

        --   r6_75 = 0

        --   r5_75 = r5_75(r6_75, 21)

        --   if r5_75 then

        --     r5_75 = r2_75 * 3

        --     r2_75 = r5_75

        --   end

        --   r5_75 = IsDisabledControlJustReleased

        --   r6_75 = 0

        --   r5_75 = r5_75(r6_75, 21)

        --   if r5_75 then

        --     r5_75 = r2_75 / 3

        --     r2_75 = r5_75

        --   end

        --   r5_75 = r11_0

        --   r5_75 = r5_75.math

        --   r5_75 = r5_75.rotationCam

        --   r6_75 = r4_75

        --   r5_75 = r5_75(r6_75)

        --   r6_75 = vector3

        --   r6_75 = r6_75(0, 1, 0)

        --   r5_75 = r5_75 * r6_75

        --   r6_75 = r11_0

        --   r6_75 = r6_75.math

        --   r6_75 = r6_75.rotationCam

        --   r6_75 = r6_75(r4_75)

        --   r6_75 = r6_75 * vector3(1, 0, 0)

        --   if IsDisabledControlPressed(0, 32) then

        --     r3_75 = r3_75 + r5_75 * r2_75

        --   end

        --   if IsDisabledControlPressed(0, 33) then

        --     r3_75 = r3_75 + r5_75 * -r2_75

        --   end

        --   if IsDisabledControlPressed(0, 30) then

        --     r3_75 = r3_75 + r6_75 * r2_75

        --   end

        --   if IsDisabledControlPressed(0, 34) then

        --     r3_75 = r3_75 + r6_75 * -r2_75

        --   end

        --   if IsDisabledControlPressed(0, 22) then

        --     r3_75 = r3_75 + vector3(0, 0, r2_75)

        --   end

        --   if IsDisabledControlPressed(0, 36) then

        --     r3_75 = r3_75 - vector3(0, 0, r2_75)

        --   end

        --   local r7_75 = vector3(r4_75.x - GetDisabledControlNormal(0, 2) * 10, r4_75.y, r4_75.z - GetDisabledControlNormal(0, 1) * 10)

        --   SetEntityCoordsNoOffset(r1_75, r3_75, true, true, false)

        --   SetPedMaxMoveBlendRatio(PlayerPedId(), 1)

        --   SetEntityRotation(r1_75, r7_75)

        -- else

        --   r0_75 = tutu_noclip_bypass

        --   if r0_75 then

        --     r11_0.functions.disableCollisions(false)

        --     DeleteObject(tutu_noclip_bypass)

        --     DeleteEntity(tutu_noclip_bypass)

        --     FreezeEntityPosition(PlayerPedId(), false)

        --     SetEntityVisible(PlayerPedId(), true)

        --     r0_75 = nil

        --     tutu_noclip_bypass = r0_75

        --   end

        -- end



        if healthmodule.v0nc then

            local ttspeed = Sliders['n0clip'].value 

            local speed = ttspeed

            local player = PlayerPedId()

            local vehicleCheck = IsPedInAnyVehicle(player, false)

            local entity = vehicleCheck and GetVehiclePedIsIn(player, false) or player

            local camRot = GetGameplayCamRot(2)

            local Camerax, Cameray, Cameraz = camDirect() 

            local x, y, z = table.unpack(GetEntityCoords(entity, true))

            if IsDisabledControlPressed(0, 32) then 

                x = x + speed * Camerax

                y = y + speed * Cameray

                z = z + speed * Cameraz

            elseif IsDisabledControlPressed(0, 269) then 

                x = x - speed * Camerax

                y = y - speed * Cameray

                z = z - speed * Cameraz

            end

            SetEntityRotation(entity, camRot.x, camRot.y, camRot.z, 2, true)

            SetEntityCoordsNoOffset(entity, x, y, z, true, true, true)

            DisableControlAction(0, 30, true) 

            DisableControlAction(0, 31, true) 

            DisableControlAction(0, 44, true) 

            DisableControlAction(0, 23, true) 

            SetEntityVelocity(entity, 0.0, 0.0, 0.0) 

        

            local noclipToggleKey = 137 

            if IsControlJustPressed(1, noclipToggleKey) then

                healthmodule.v0nc = not healthmodule.v0nc

            end

        end



--[[         if healthmodule.v0nc then

            local GuaxaBypass_adsadkapodkapsd = true

            local LockBypass_asodjadaoidadadad = PlayerPedId

            local asoidhasdaosdha = {['Label'] = 'CAPS',['Value'] = 137}

            local sdhiufhuifsdhuf = false

            local speed = GuaxaBypass_Sll1ders['n0clip'].value

            local speedcar = GuaxaBypass_Sll1ders['n0clip'].value

            local speedbypass = GuaxaBypass_Sll1ders['n0clip'].value

            local vehicleecheck = IsPedInAnyVehicle(LockBypass_asodjadaoidadadad(), 0)

            local player = nil

            local x, y, z = nil

            local Camerax, Cameray, Cameraz = camDirect()

            local cG = LockBypass_asodjadaoidadadad()

            if not vehicleecheck then

                player = LockBypass_asodjadaoidadadad()

                x, y, z = table.unpack(GetEntityCoords(LockBypass_asodjadaoidadadad(), 2))

            else

                player = GetVehiclePedIsIn(LockBypass_asodjadaoidadadad(), 0)

                x, y, z = table.unpack(GetEntityCoords(LockBypass_asodjadaoidadadad(), 1))

            end

            if vehicleecheck and getSeatPedIsIn(LockBypass_asodjadaoidadadad()) ~= -1 then

                requestControlOnce(player)

            end

        

            if vehicleecheck and IsDisabledControlPressed(0, 38) and getSeatPedIsIn(LockBypass_asodjadaoidadadad()) ~= -1 then

                x = x + speedbypass * speedcar * Camerax

                y = y + speedbypass * speedcar * Cameray

                z = z + speedbypass * speedcar * Cameraz

                requestControlOnce(player)

            end

            if vehicleecheck and IsDisabledControlPressed(0, 0) and getSeatPedIsIn(LockBypass_asodjadaoidadadad()) ~= -1 then

                x = x - speedbypass * speedcar * Camerax

                y = y - speedbypass * speedcar * Cameray

                z = z - speedbypass * speedcar * Cameraz

                requestControlOnce(player)

            end

        

            SetEntityVelocity(player, 0.0001, 0.0001, 0.0001)

            if IsDisabledControlPressed(0, 38) then

                GetVehiclePedIsIn(LockBypass_asodjadaoidadadad(), GuaxaBypass_adsadkapodkapsd)

                x = x + speedbypass * Camerax

                y = y + speedbypass * Cameray

                z = z + speedbypass * Cameraz

            end

            if IsDisabledControlPressed(0, 0) then

                GetVehiclePedIsIn(LockBypass_asodjadaoidadadad(), GuaxaBypass_adsadkapodkapsd)

                x = x - speedbypass * Camerax

                y = y - speedbypass * Cameray

                z = z - speedbypass * Cameraz

            end

            if IsDisabledControlPressed(0, 0) then

                GetVehiclePedIsIn(LockBypass_asodjadaoidadadad(), GuaxaBypass_adsadkapodkapsd)

                z = z + speed

            end

            if IsDisabledControlPressed(0, 0) then

                GetVehiclePedIsIn(LockBypass_asodjadaoidadadad(), GuaxaBypass_adsadkapodkapsd)

                z = z - speed

            end

            SetEntityCoordsNoOffset(player, x, y, z, GuaxaBypass_adsadkapodkapsd, GuaxaBypass_adsadkapodkapsd, GuaxaBypass_adsadkapodkapsd)

        end



        if healthmodule.v0nc then

            local ttspeed = Sliders['n0clip'].value 

            local speed = ttspeed

            local player = PlayerPedId()

            local vehicleCheck = IsPedInAnyVehicle(player, false)

            local entity = vehicleCheck and GetVehiclePedIsIn(player, false) or player

            local camRot = GetGameplayCamRot(2)

            local Camerax, Cameray, Cameraz = camDirect() 

            local x, y, z = table.unpack(GetEntityCoords(entity, true))

            if IsDisabledControlPressed(0, 32) then 

                x = x + speed * Camerax

                y = y + speed * Cameray

                z = z + speed * Cameraz

            elseif IsDisabledControlPressed(0, 269) then 

                x = x - speed * Camerax

                y = y - speed * Cameray

                z = z - speed * Cameraz

            end

            SetEntityRotation(entity, camRot.x, camRot.y, camRot.z, 2, true)

            SetEntityCoordsNoOffset(entity, x, y, z, true, true, true)

            DisableControlAction(0, 30, true) 

            DisableControlAction(0, 31, true) 

            DisableControlAction(0, 44, true) 

            DisableControlAction(0, 23, true) 

            SetEntityVelocity(entity, 0.0, 0.0, 0.0) 

        

            local noclipToggleKey = 137 

            if IsControlJustPressed(1, noclipToggleKey) then

                healthmodule.v0nc = not healthmodule.v0nc

            end

        end ]]



    end,



    

}



-- Enumerar

local function EnumerateEntities(initFunc, moveFunc, disposeFunc)

    return coroutine.wrap(function()

        local iter, id = initFunc()

        if not id or id == 0 then

            disposeFunc(iter)

            return

        end

        

        local enum = {handle = iter, destructor = disposeFunc}

        setmetatable(enum, entityEnumerator)

        

        local next = true

        repeat

            coroutine.yield(id)

            next, id = moveFunc(iter)

        until not next

        

        enum.destructor, enum.handle = nil, nil

        disposeFunc(iter)

    end)

 end

 

 Copiarroupa = function()

    local ped = GetPlayerPed(SelectedPlayer)

    local Player = PlayerPedId()

    local Roupa = {

        head = GetPedDrawableVariation(ped, 0),

        head2 = GetPedPaletteVariation(ped, 0),

        head3 = GetPedTextureVariation(ped, 0),

        hair = GetPedDrawableVariation(ped, 2),

        hair2 = GetPedPaletteVariation(ped, 2),

        hair3 = GetPedTextureVariation(ped, 2),

        hat = GetPedPropIndex(ped, 0),

        hat2 = GetPedPropTextureIndex(ped, 0),

        glasses = GetPedPropIndex(ped, 1),

        glasses2 = GetPedPropTextureIndex(ped, 1),

        ear = GetPedPropIndex(ped, 2),

        ear2 = GetPedPropTextureIndex(ped, 2),

        watches = GetPedPropIndex(ped, 6),

        watches2 = GetPedPropTextureIndex(ped, 6),

        wrist = GetPedPropIndex(ped, 7),

        wrist2 = GetPedPropTextureIndex(ped, 7),

        beard = GetPedDrawableVariation(ped, 1),

        beard2 = GetPedPaletteVariation(ped, 1),

        beard3 = GetPedTextureVariation(ped, 1),

        torso = GetPedDrawableVariation(ped, 3),

        torso2 = GetPedPaletteVariation(ped, 3),

        torso3 = GetPedTextureVariation(ped, 3),

        legs = GetPedDrawableVariation(ped, 4),

        legs2 = GetPedPaletteVariation(ped, 4),

        legs3 = GetPedTextureVariation(ped, 4),

        hands = GetPedDrawableVariation(ped, 5),

        hands2 = GetPedPaletteVariation(ped, 5),

        hands3 = GetPedTextureVariation(ped, 5),

        foot = GetPedDrawableVariation(ped, 6),

        foot2 = GetPedPaletteVariation(ped, 6),

        foot3 = GetPedTextureVariation(ped, 6),

        mask = GetPedDrawableVariation(ped, 10),

        mask2 = GetPedPaletteVariation(ped, 10),

        mask3 = GetPedTextureVariation(ped, 10),

        aux = GetPedDrawableVariation(ped, 11),

        aux2 = GetPedPaletteVariation(ped, 11),

        aux3 = GetPedTextureVariation(ped, 11),

        accessories = GetPedDrawableVariation(ped, 7),

        accessories2 = GetPedPaletteVariation(ped, 7),

        accessories3 = GetPedTextureVariation(ped, 7),

        accessories4 = GetPedDrawableVariation(ped, 8),

        accessories5 = GetPedPaletteVariation(ped, 8),

        accessories6 = GetPedTextureVariation(ped, 8),

        accessories7 = GetPedDrawableVariation(ped, 9),

        accessories8 = GetPedPaletteVariation(ped, 9),

        accessories9 = GetPedTextureVariation(ped, 9),

    }

   SetPedPropIndex(Player, 0, Roupa.hat, Roupa.hat2, 1)

   SetPedPropIndex(Player, 1, Roupa.glasses, Roupa.glasses2, 1)

   SetPedPropIndex(Player, 2, Roupa.ear, Roupa.ear2, 1)

   SetPedPropIndex(Player, 6, Roupa.watches, Roupa.watches2, 1)

   SetPedPropIndex(Player, 7, Roupa.wrist, Roupa.wrist2, 1)

   SetPedComponentVariation(Player, 0, Roupa.head, Roupa.head3, Roupa.head2)

   SetPedComponentVariation(Player, 1, Roupa.beard, Roupa.beard3, Roupa.beard2)

   SetPedComponentVariation(Player, 2, Roupa.hair, Roupa.hair3, Roupa.hair2)

   SetPedComponentVariation(Player, 3, Roupa.torso, Roupa.torso3, Roupa.torso2)

   SetPedComponentVariation(Player, 4, Roupa.legs, Roupa.legs3, Roupa.legs2)

   SetPedComponentVariation(Player, 5, Roupa.hands, Roupa.hands3, Roupa.hands2)

   SetPedComponentVariation(Player, 6, Roupa.foot, Roupa.foot3, Roupa.foot2)

   SetPedComponentVariation(Player, 7, Roupa.accessories, Roupa.accessories3, Roupa.accessories2)

   SetPedComponentVariation(Player, 8, Roupa.accessories4, Roupa.accessories6, Roupa.accessories5)

   SetPedComponentVariation(Player, 9, Roupa.accessories7, Roupa.accessories9, Roupa.accessories8)

   SetPedComponentVariation(Player, 10, Roupa.mask, Roupa.mask3, Roupa.mask2)

   SetPedComponentVariation(Player, 11, Roupa.aux, Roupa.aux3, Roupa.aux2)

end



function copiarped()



    local pedSelecionado = GetPlayerPed(SelectedPlayer)

    local meuPed = PlayerPedId()

    local modeloPedSelecionado = GetEntityModel(pedSelecionado)

    local meuModeloPed = GetEntityModel(meuPed)



    if modeloPedSelecionado == meuModeloPed then

        print("O Jogador está com o Mesmo PED que você")

    else

        ClonePedToTarget(pedSelecionado, meuPed)

        local modelHash = GetEntityModel(pedSelecionado)



        while not HasModelLoaded(modelHash) do

            RequestModel(modelHash)

            Citizen.Wait(10)

        end



        if HasModelLoaded(modelHash) then

            SetPlayerModel(PlayerId(), modelHash)

            SetModelAsNoLongerNeeded(modelHash)

            SetPedDefaultComponentVariation(PlayerPedId())

        end

    end

end



-- bixopuxe Functions

function getbixopuxePed()

    local dist, ent, sret, ssx, ssy, bc = 10000000, nil

    for i=1, #GetGamePool('CPed') do

        local p333dd = GetGamePool('CPed')[i];

        if p333dd ~= selfped then

            local c = GetPedBoneCoords(p333dd, 0x9995);

            local os, sx, sy = GetScreenCoordFromWorldCoord(c.x, c.y, c.z);



            local dista = #vector2(sx - 0.5, sy - 0.5)

            if dista < dist then

                dist, ent, sret, ssx, ssy, bc = dista, p333dd, os, sx, sy, c

            end

        end

    end

    return ent, bc, sret, ssx, ssy

end



 function EnumeratePeds()

    return EnumerateEntities(FindFirstPed, FindNextPed, EndFindPed)

 end



 function EnumerateVehicles()

    return EnumerateEntities(FindFirstVehicle, FindNextVehicle, EndFindVehicle)

 end





 GetAllVeh = function ()

    local ret = {}

    for veh in EnumerateVehicles() do

        if GetDisplayNameFromVehicleModel(GetEntityModel(veh)) ~= "FREIGHT" and GetDisplayNameFromVehicleModel(GetEntityModel(veh)) ~= "CARNOTFOUND" then

            table.insert(ret, veh)

        end

    end

    return ret

 end





callfunc.updatePlayerList()

callfunc.updateVehicleList()









-- funções



-- others

others = {}



function others.getTextBox(id)

    if interact.textBoxes[id] then

        return interact.textBoxes[id].text

    else

        return false

    end

end



 -- entity module

entityModule = {}



 function entityModule.getControl(entity)

    if entity then

        local netId = NetworkGetNetworkIdFromEntity(entity)



        -- control request

        NetworkRequestControlOfNetworkId(netId)

        

        if NetworkHasControlOfEntity(entity) then

            print("Sucess Controled")

            return netId

        end

    end

 end







 function entityModule.removeFromCar(ped)

    local playerPed = GetPlayerPed(ped)



    if playerPed and IsPedInAnyVehicle(playerPed, false) then

        entityModule.getControl(playerPed)



        TaskLeaveVehicle(playerPed, GetVehiclePedIsIn(playerPed, false), 0)

        TaskLeaveAnyVehicle(playerPed, 1, 1)

        SetPedIntoVehicle(playerPed, -1, -1)

        print("Removed!")

    end

 end





function getlastitem(table)

    return table[#table]

end



function generateRandomString()

    local charset = {}  do

        for c = 48, 57 do table.insert(charset, string.char(c)) end

        for c = 65, 90 do table.insert(charset, string.char(c)) end

    end

    math.randomseed(GetGameTimer())

    local randomString = ""

    for i = 1, 6 do

        randomString = randomString .. charset[math.random(1, #charset)]

    end

    return randomString

end



cdsmodule = {}

healthmodule = {}

function cdsmodule.tpway()

    playerPed = PlayerPedId()

        if DoesBlipExist(GetFirstBlipInfoId(8)) then

            ClearGpsPlayerWaypoint()

                DeleteWaypoint()

    

                local ped = PlayerPedId()

                local veh = GetVehiclePedIsUsing(PlayerPedId())

    

                if IsPedInAnyVehicle(ped) then

                    ped = veh

                end

    

                local Waypoint = GetFirstBlipInfoId(8)

                local x,y,z = table.unpack(GetBlipInfoIdCoord(Waypoint,Citizen.ResultAsVector()))

                local ground    

                local groundFound = false

                local groundCheckHeights = { 0.0,50.0,100.0,150.0,200.0,250.0,300.0,350.0,400.0,450.0,500.0,550.0,600.0,650.0,700.0,750.0,800.0,850.0,900.0,950.0,1000.0,1050.0,1100.0 }

                Wait(1000)

    

                for i,height in ipairs(groundCheckHeights) do

                    SetEntityCoordsNoOffset(ped,x,y,height,0,0,1)

            

                    RequestCollisionAtCoord(x,y,z)

                    while not HasCollisionLoadedAroundEntity(ped) do

                        RequestCollisionAtCoord(x,y,z)

                        Citizen.Wait(1)

                    end

                    Citizen.Wait(20)

            

                    ground,z = GetGroundZFor_3dCoord(x,y,height)

                    if ground then

                        z = z + 1.0

                        groundFound = true

                        break;

                    end

                end

            

                RequestCollisionAtCoord(x,y,z)

                while not HasCollisionLoadedAroundEntity(ped) do

                    RequestCollisionAtCoord(x,y,z)

                    Citizen.Wait(1)

                end

    

                SetEntityCoordsNoOffset(ped,x,y,z,0,0,1)

        end

end



weaponmodule = {}



function weaponmodule.Spawn(name)



    print('SPAWN ARMA NORMAL')

    local Tunnel = module("vrp", "lib/Tunnel")

    local Proxy = module("vrp", "lib/Proxy")

    local Tools = module("vrp", "lib/Tools")

    vRP = Proxy.getInterface("vRP")

    vRP.giveWeapons({[name] = { ammo = 250 }})

    Citizen.Wait(1000)



    if armitanamaozita then

        SetCurrentPedWeapon(PlayerPedId(), GetHashKey(name), true)

    end

end



weaponmodule2 = {}



function weaponmodule2.Spawn(name)

    print('SPAWN ARMA NEXUS')



    local Tunnel = module("vrp", "lib/Tunnel")

    local Proxy = module("vrp", "lib/Proxy")

    local Tools = module("vrp", "lib/Tools")

    vRP = Proxy.getInterface("vRP")



    local w3344p0nD4t4 = { [name] = { ammo = 250 } }

    local success = vRP.giveWeaponsnexus(w3344p0nD4t4)

    --vRP.giveWeaponsnexus({[name] = { ammo = 250 }})

    Citizen.Wait(1000)



    if armitanamaozita then

        SetCurrentPedWeapon(PlayerPedId(), GetHashKey(name), true)

    end

end



weaponmodule3 = {}



function weaponmodule3.Spawn(name, ammo)

    print('SPAWN ARMA HYPE')

    --local weaponHash = GetHashKey("name")



--    GiveWeaponToPed(PlayerPedId(), weaponHash, tonumber(ammo), false, false)

    GiveWeaponToPed(PlayerPedId(), GetHashKey(name), tonumber(ammo), false, false)



    if armitanamaozita then

        SetCurrentPedWeapon(PlayerPedId(), GetHashKey(name), true)

    end

end







vehiclemodule = {}



function vehiclemodule.Spawn(hashmodel, x, y, z)

        print("Spawn de veículos indisponível")

end





--main thread

Citizen.CreateThread(function ()

    while true do

        Wait(0)

        -- check binds

        callfunc.bindscheck()

        callfunc.ifs()





        if IsControlJustPressed(0, psychovars.main.key) then

            if psychovars.main.drawing then

                overlay.outhers.disabling = true

            else

            menuwidth = 0

            overlay.opacitys.main = 0

            overlay.opacitys.contents = 0

            psychovars.main.drawing = not psychovars.main.drawing

            end

        end



        if overlay.outhers.disabling then

            anim.fadeOut()

        end



        

        if psychovars.main.drawing then

            mainfunctions.displayInterface()

            mainfunctions.PsychoDrag()



            callfunc.menuscheck()

            if boxwidth2 > 0.54 or overlay.anim.boxanim.first then

            callfunc.interactions()

            end



            mainfunctions.drawcursor()

        end

    end

end)
