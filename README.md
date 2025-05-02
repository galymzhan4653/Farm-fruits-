# Farm-fruits-
if game.PlaceId == 2753915549 or game.PlaceId == 4442272183 or game.PlaceId == 7449423635 then
    wait()  -- ждем, пока игра загрузится
    local playerGui = game:GetService("Players").LocalPlayer.PlayerGui
    local mainGui = playerGui:WaitForChild("Главная", 10)  -- проверяем наличие интерфейса "Главная"

    if mainGui then
        local chooseTeam = mainGui:FindFirstChild("ВыбратьКоманду")
        if chooseTeam then
            if getgenv().Team == "Pirate" then
                for _, connection in pairs(getconnections(chooseTeam.Container.Pirates.Frame.TextButton.Activated)) do
                    connection.Function()
                end
            elseif getgenv().Team == "Marine" then
                for _, connection in pairs(getconnections(chooseTeam.Container.Marines.Frame.TextButton.Activated)) do
                    connection.Function()
                end
            else
                for _, connection in pairs(getconnections(chooseTeam.Container.Pirates.Frame.TextButton.Activated)) do
                    connection.Function()
                end
            end
        else
            warn("Команда не найдена в интерфейсе!")
        end
    else
        warn("Интерфейс 'Главная' не загружен!")
    end

    -- Запуск внешнего скрипта
    local scriptUrl = 'https://raw.githubusercontent.com/VNT-UNIVERSAL/Panda-Hub/main/Release/fruit.lua'
    if syn and syn.queue_on_teleport then
        syn.queue_on_teleport("loadstring(game:HttpGet('" .. scriptUrl .. "'))()")
    elseif fluxus and fluxus.queue_on_teleport then
        fluxus.queue_on_teleport("loadstring(game:HttpGet('" .. scriptUrl .. "'))()")
    else
        loadstring(game:HttpGet(scriptUrl))()
    end
end
