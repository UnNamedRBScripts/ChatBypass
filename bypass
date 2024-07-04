--[[
heartasian's bypass v2.0.1

► heartasians                   :   BYPASSES, CHAT HOOK, NOTIFICATIONS
► suno/headlined/hello-n-bye    :   MORE BYPASSES, HOST SCRIPT

🤑 https://discord.com/invite/FRsmP9knVc 🤑
]]

repeat task.wait() until game:IsLoaded()

local TCS = game:GetService("TextChatService")
local CoreGui = game:GetService("CoreGui")
local RStorage = game:GetService("ReplicatedStorage")
local Players = game:GetService("Players")
local TweenService = game:GetService("TweenService")
local HttpService = game:GetService("HttpService")
local UserInputService = game:GetService("UserInputService")

local LocalPlayer = Players.LocalPlayer
local PlayerGui = LocalPlayer.PlayerGui

local isLegacy = TCS.ChatVersion == Enum.ChatVersion.LegacyChatService
local ChatBar = CoreGui:FindFirstChild("TextBoxContainer", true) or PlayerGui:FindFirstChild("Chat"):FindFirstChild("ChatBar", true)
ChatBar = ChatBar:FindFirstChild("TextBox") or ChatBar

local Keywords = {
    --phrases
    {"lil nigga", "li⁥ӏn⁥і⁥ggа"},
    {"you fucking retard", "yo⁥⁥⁥⁥⁥⁥uf⁥⁥⁥⁥⁥⁥⁥⁥⁥u⁥⁥⁥⁥⁥⁥⁥⁥⁥c⁥⁥⁥⁥⁥⁥⁥⁥⁥k⁥⁥i⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥n⁥gr⁥⁥⁥⁥⁥⁥e⁥⁥t⁥⁥⁥⁥⁥⁥ar⁥⁥⁥⁥⁥⁥d"},
    {"you fucking nigger", "yоufu⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥сk⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥іn⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥gn⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥і⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥ggе⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥r"},
    {"fucking nigger", "fu⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥сk⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥іn⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥gn⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥і⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥ggе⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥r"},

    --only work in sentence (sometimes)
    {"fucking", "fu⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥сk⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥іn⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥g"},
    {"nigger", "n⁥⁥⁥⁥⁥і⁥⁥⁥⁥ɡ⁥⁥⁥⁥ɡ⁥⁥⁥⁥е⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥r"}, -- changed in v2.01
    {"faggot", "f⁥⁥⁥⁥⁥⁥⁥⁥а⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥ɡɡ⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥o⁥⁥⁥⁥⁥⁥⁥⁥t"},
    {"nigga", "n⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥і⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥ggа"},
    {"retard", "r⁥⁥⁥⁥⁥⁥e⁥⁥t⁥⁥⁥⁥⁥⁥ar⁥⁥⁥⁥⁥⁥d"},
    {"child porn", "ch⁥⁥⁥⁥⁥⁥⁥⁥⁥iӏdpо⁥⁥⁥⁥⁥⁥⁥⁥⁥rn"},
    {"snapchat", "ѕnарсһаt"},
    {"snap", "ѕnар"},
    {"instagram", "іnѕtаgrаm"},
    {"insta", "іnѕtа"},

    --yay
    {"fuck", "F⁥⁥⁥⁥⁥U⁥⁥⁥⁥⁥СΚ"}, -- changed in v2
    {"up", "u⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥p"},
    {"shut", "s⁥⁥⁥⁥⁥⁥⁥⁥һu⁥⁥⁥⁥⁥⁥⁥⁥t"},
    {"butt", "butt"},
    {"dirty", "dіrtу"},
    {"rape", "⁥⁥⁥⁥⁥r⁥⁥⁥⁥⁥а⁥⁥⁥⁥⁥р⁥⁥⁥⁥⁥е⁥⁥⁥⁥⁥"},
    {"sex", "⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥е⁥⁥⁥⁥⁥х"}, -- changed in v2
    {"whore", "⁥⁥⁥⁥⁥w⁥⁥⁥⁥⁥һ⁥⁥⁥⁥⁥o⁥⁥⁥⁥⁥r⁥⁥⁥⁥⁥e⁥⁥⁥⁥⁥"},
    {"slut", "⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥ӏ⁥⁥⁥⁥⁥u⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥"},
    {"pornhub", "⁥⁥⁥⁥⁥ро⁥⁥⁥⁥⁥r⁥⁥⁥⁥⁥n⁥⁥⁥⁥⁥һ⁥⁥⁥⁥⁥u⁥⁥⁥⁥⁥b⁥⁥⁥⁥⁥"},
    {"cock", "cо⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥сk"}, -- changed in v2
    {"pussy", "⁥⁥⁥⁥⁥р⁥⁥⁥⁥⁥u⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥у⁥⁥⁥⁥⁥"},
    {"naked", "⁥⁥⁥⁥⁥n⁥⁥⁥⁥⁥а⁥⁥⁥⁥⁥k⁥⁥⁥⁥⁥е⁥⁥⁥⁥⁥d⁥⁥⁥⁥⁥"},
    {"titties", "⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥і⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥і⁥⁥⁥⁥⁥е⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥"},
    {"titty", "⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥і⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥y⁥⁥⁥⁥⁥"},
    {"tits", "⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥і⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥s⁥⁥⁥⁥⁥"},
    {"cum", "⁥⁥⁥⁥⁥с⁥⁥⁥⁥⁥u⁥⁥⁥⁥⁥m⁥⁥⁥⁥⁥"},
    {"kkk", "⁥⁥⁥⁥⁥К⁥⁥⁥⁥⁥К⁥⁥⁥⁥⁥К⁥⁥⁥⁥⁥"},
    {"rizz", "r⁥⁥⁥⁥⁥i⁥⁥⁥⁥⁥z⁥⁥⁥⁥⁥z"},
    {"ass", "⁥⁥⁥⁥⁥а⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥"},
    {"vagina", "⁥⁥⁥⁥⁥v⁥⁥⁥⁥⁥а⁥⁥⁥⁥⁥g⁥⁥⁥⁥⁥і⁥⁥⁥⁥⁥n⁥⁥⁥⁥⁥а⁥⁥⁥⁥⁥"},
    {"nudes", "⁥⁥⁥⁥⁥n⁥⁥⁥⁥⁥u⁥⁥⁥⁥⁥d⁥⁥⁥⁥⁥е⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥"},
    {"hoe", "⁥⁥⁥⁥⁥һ⁥⁥⁥⁥⁥о⁥⁥⁥⁥⁥e"},
    {"blowjob", "⁥⁥⁥⁥b⁥⁥⁥⁥ӏ⁥⁥⁥⁥о⁥⁥⁥⁥w⁥⁥⁥⁥ј⁥⁥⁥⁥o⁥⁥⁥⁥b⁥⁥⁥⁥"},
    {"femboy", "fеmbоу"},
    {"love", "⁥⁥⁥⁥⁥ӏ⁥⁥⁥⁥⁥о⁥⁥⁥⁥⁥v⁥⁥⁥⁥⁥е⁥⁥⁥⁥⁥"},
    {"kiss", "⁥⁥⁥⁥⁥k⁥⁥⁥⁥⁥і⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥"},
    {"discord", "dіѕсоrd"},
    {"porn", "⁥⁥⁥⁥⁥ро⁥⁥⁥⁥⁥r⁥⁥⁥⁥⁥n⁥⁥⁥⁥⁥"},
    {"damn", "dаmn"},
    {"anal", "аnаl"},
    {"zoophile", "zоорһіӏе"},
    {"lmao", "LМАО"},
    {"lmfao", "LМFАО"},
    {"george", "gеоrgе"},
    {"floyd", "flоуd"},
    {"sexual", "⁥⁥⁥⁥⁥ѕ⁥⁥⁥⁥⁥е⁥⁥⁥⁥⁥х⁥⁥⁥⁥⁥ual"},
    {"tiktok", "tіktоk"},
    {"twerk", "twеrk"},
    {"gay", "⁥⁥⁥⁥⁥g⁥⁥⁥⁥⁥а⁥⁥⁥⁥⁥у⁥⁥⁥⁥⁥"},
    {"black", "bӏасk"},
    {"suck", "ѕuсk"},
    {"heil", "һеіӏ"},
    {"nazi", "n⁥⁥⁥⁥⁥a⁥⁥⁥⁥⁥z⁥⁥⁥⁥i"},
    {"sperm", "ѕре⁥⁥⁥⁥⁥⁥⁥⁥rm"}, -- changed in v2
    {"hate", "һаtе"},
    {"balls", "bаӏӏѕ"},
    {"shit", "s⁥⁥⁥⁥⁥⁥⁥⁥һit"},
    {"bitch", "bi⁥⁥⁥⁥⁥⁥⁥⁥tсһ"},
    {"kill", "kіll"},
    {"yourself", "уоurѕеlf"},
    {"%.com", ".⁥⁥⁥⁥⁥с⁥⁥⁥⁥о⁥⁥⁥⁥⁥⁥m"},
    {"bastard", "bаѕtаrd"},
    {"panties", "раntіеѕ"},
    {"meth", "mеth"},
    {"weed", "wееd"},
    {"cunt", "с⁥⁥⁥⁥⁥unt"},
    {"penis", "реnіѕ"},
    {"pedo", "ре⁥⁥⁥⁥⁥⁥⁥⁥d⁥⁥⁥⁥⁥⁥⁥⁥о"},
    {"masturbate", "mаѕturbаtе"},
    {"moan", "mоаn"},
    {"kink", "kіnk"},
    {"fetish", "fеtіѕh"},
    {"horny", "hоrnу"},
    {"booty", "b⁥⁥⁥оо⁥⁥⁥t⁥⁥⁥у"},
    {"horny", "h⁥⁥⁥⁥⁥⁥⁥⁥оrnу"},
    {"commit", "соmmіt"},

    --suno's credit
    {"fap", "fаp"},
    {"hentai", "һentаі"},
    {"rule34", "ruӏe34"},
    {"r34", "⁥⁥⁥⁥⁥r⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥3⁥⁥⁥⁥⁥4"},
    {"xxx", "⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥xx⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥x⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥"},
    {"suicide", "⁥ѕuі⁥сіdе"},
    {"pp", "рр"},
    {"dick", "⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥d⁥⁥⁥⁥⁥і⁥⁥⁥⁥с⁥⁥⁥⁥⁥⁥⁥⁥k⁥⁥⁥⁥⁥"},
    {"crack", "сrасk"},
    {"heroin", "hеrоin"},
    {"boob", "b⁥⁥⁥оо⁥⁥⁥b"},
    {"boobies", "b⁥⁥⁥оо⁥⁥⁥b⁥⁥⁥іеѕ"},
    {"rapist", "⁥⁥⁥⁥⁥⁥⁥⁥rа⁥⁥⁥⁥⁥⁥⁥⁥p⁥іѕt"},
    {"cocaine", "c⁥о⁥⁥⁥⁥⁥⁥⁥⁥⁥ca⁥іnе"},
    {"do you have", "dо yоu h⁥аv⁥⁥⁥⁥⁥е⁥⁥⁥⁥"},
    {"hole", "hоl⁥е⁥⁥⁥⁥"},
    {"cocksucker", "cо⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥сksuck⁥еr"},
    {"twat", "twаt"},
    {"wanker", "wаnk⁥еr"},
    {"anus", "аnu⁥ѕ⁥⁥⁥⁥"},
    {"beaner", "⁥⁥⁥b⁥е⁥⁥⁥⁥⁥⁥аn⁥еr⁥⁥⁥⁥⁥⁥"},
    {"coon", "cо⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥о⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥n"},
    {"dildo", "dіld⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥о⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥"},
    {"hump", "h⁥⁥⁥⁥⁥u⁥⁥⁥⁥⁥mp"},
    {"jizz", "⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥j⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥izz⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥"},
    {" ho ", " h⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥о⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥ "},
    {"pregnant", "р⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥rе⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥gnа⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥nt"},
    {"impregnat", "іmрrеgnаt"},
    {"kunt", "⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥kun⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥t⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥"},
    {"queef", "qu⁥е⁥⁥⁥⁥⁥⁥е⁥⁥⁥⁥⁥f"},
    {"tard", "tаrd"},
    {"sexy", "⁥⁥⁥⁥⁥⁥⁥⁥⁥sехy⁥"},
    {"slutty", "⁥ѕӏuttу"},
    {"dumbass", "d⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥um⁥⁥⁥⁥⁥b⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥а⁥ѕ⁥ѕ"},
    {"moron", "m⁥оr⁥оn"},
    {"xxx", "⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥xx⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥x⁥⁥⁥⁥⁥⁥⁥⁥⁥⁥"},
    {"fat", "fаt"},
    {"die", "⁥⁥⁥⁥⁥dі⁥⁥⁥⁥⁥е"},

    --new
    {"abortion", "аbоrtіоn"},
    {"jew", "јеw"},
    {"futa", "futа"},
    {"twink", "twіnk"},
    {"alcohol", "аlсоhоl"},
    {"schlong", "ѕсhlоng"},
    {"child predator", "ch⁥⁥⁥⁥⁥⁥⁥⁥⁥iӏdрrеdаtо⁥⁥⁥⁥⁥r"},
    {"fag", "f⁥⁥⁥⁥⁥⁥⁥⁥а⁥⁥⁥⁥⁥⁥⁥⁥ɡ"}, --rarely works
    {"molest", "mоlеѕt"},
    {"condom", "со⁥⁥⁥⁥⁥nd⁥⁥⁥⁥⁥о⁥⁥⁥⁥⁥m"},
    {"virgin", "νіrgіn"},
    {"torture", "tоrturе"},
    
    --custom
    {"example", "example"},

    --dont delete
    {" ", ""},
}

--[[
    need to fix:
    lmao, lmfao, discord

    need to add:
    damn, slave
]]

local Gen = function(Message)
    for _, info in Keywords do
        local real = info[1]
        local bypass = info[2]
        Message = Message:gsub(real, bypass)
    end
    return Message
end

local Chat = function(Message)
    if isLegacy then
        local ChatRemote = RStorage:FindFirstChild("SayMessageRequest", true)
        ChatRemote:FireServer(Message, "All")
    else
        local Channel = TCS.TextChannels.RBXGeneral
        Channel:SendAsync(Message)
    end
end

local Fake = function(Message)
    if isLegacy then
        Players:Chat(Message)
    else
        local Channel = TCS.TextChannels.RBXGeneral
        --Channel:SendAsync(("/e %s"):format(Message))
        -- ^^^ its too annoying
    end
end

local chars = {}
for i=97,122 do chars[#chars+1]=string.char(i) end
for i=65,90 do chars[#chars+1]=string.char(i) end

local RNG = function(length)
    local str = ""
    for i = 1, length do
        str = str .. chars[math.random(#chars)]
    end
    return str
end

local ResetFilter = function()
    for i = 1, 10 do
        local GUID = RNG(i)
        local Filler = "i love asians so much"
        local Reset = ("%s %s"):format(GUID, Filler)
        task.spawn(function()
            Fake(Reset)
        end)
    end
end

local Connection = Instance.new("BindableFunction")

for _, c in getconnections(ChatBar.FocusLost) do
    c:Disconnect()
end

ChatBar.FocusLost:Connect(function(enterPressed)
    if enterPressed then
        Connection:Invoke(ChatBar.Text)
        ChatBar.Text = ""
    end
end)

Connection.OnInvoke = function(Message)
    Message = Gen(Message)
    Chat(Message)
    ResetFilter()
end

local NotifyModule = loadstring(game:HttpGet("https://raw.githubusercontent.com/PeaPattern/notif-lib/main/main.lua"))()

UserInputService.InputBegan:Connect(function(Input, GPE)
    if GPE or Input.KeyCode ~= Enum.KeyCode.Zero then return end

    NotifyModule:Notify("copied invite link to clipboard", 1)
    setclipboard("https://discord.com/invite/FRsmP9knVc")
end)

NotifyModule:Notify("heartasian's bypass v2 loaded ► press 0 to join discord for more exclusive scripts", 5)
