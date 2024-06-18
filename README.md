```lua
loadstring:getgenv().HighlightKillers = function()
    local function highlightKiller(killer)
        local highlight = Instance.new("Highlight")
        highlight.Adornee = killer
        highlight.Parent = killer

        local nameTag = Instance.new("BillboardGui")
        nameTag.Size = UDim2.new(0, 200, 0, 50)
        nameTag.Adornee = killer
        nameTag.Parent = killer
        nameTag.StudsOffset = Vector3.new(0, 3, 0)

        local textLabel = Instance.new("TextLabel")
        textLabel.Size = UDim2.new(1, 0, 1, 0)
        textLabel.BackgroundTransparency = 1
        textLabel.Text = killer.Name
        textLabel.TextColor3 = Color3.new(1, 0, 0)
        textLabel.TextScaled = true
        textLabel.Parent = nameTag
    end

    local function searchAndHighlight()
        for _, obj in ipairs(workspace:GetDescendants()) do
            if obj.Name == "Killers" then
                highlightKiller(obj)
            end
        end
    end

    searchAndHighlight()
    workspace.DescendantAdded:Connect(function(obj)
        if obj.Name == "Killers" then
            highlightKiller(obj)
        end
    end)
end

getgenv().AutoDeleteDoors = function()
    local function deleteDoors()
        for _, obj in ipairs(workspace:GetChildren()) do
            if obj.Name == "doors" then
                obj:Destroy()
            end
        end
    end

    deleteDoors()
    workspace.ChildAdded:Connect(function(obj)
        if obj.Name == "doors" then
            obj:Destroy()
        end
    end)
end
```
