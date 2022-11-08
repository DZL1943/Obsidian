---
title: hammerspoons
created: "2022-11-08 09:19"
modified: "2022-11-08 09:59"
---

## 文档

- [Getting Started](https://www.hammerspoon.org/go/) 
- [Hammerspoon Docs](http://www.hammerspoon.org/docs/)

## 配置

```lua
-- hammerspoon config example
-- date: 2022-11-08

local obj = {}
obj._metadata = {
    name = 'hammerspoon config example',
    version = '1.0',
    author = '',
    homepage = '',
    license = 'MIT - https://opensource.org/licenses/MIT',
}

obj.cfg = {}
obj.map = {
    reloadConfig = { { 'ctrl', 'cmd' }, 'r' },
    toggleHelp = { { 'ctrl', 'alt' }, '/' },
    windowManager = { { 'alt', 'cmd' }, 'w' },
}
obj.spoons = {}

----
function obj:init()
    for k, v in pairs(obj._metadata) do obj[k] = v end
    for _, v in ipairs(obj.spoons) do hs.loadSpoon(v) end
    -- daemons
    obj.d = {}
    -- objects
    obj.o = {}
    return self
end

function obj:start()
    obj:_setupReloadConfig()
    obj:_setupAppLauncher()
    obj:_setupWindowManager()
    return self
end

function obj:stop()
    return self
end

function obj:bindHotkeys(mapping)
    local def = {
        toggleHelp = function()
            obj:_toggleHelp()
        end
    }
    for k, v in pairs(mapping) do
        if def[k] then
            hs.hotkey.bind(v[1], v[2], def[k])
        end
    end
    return self
end

---
function obj:_setupReloadConfig()
    local function notifyAndReload()
        hs.notify.new({ title = "Hammerspoon", informativeText = "Config reloaded." }):send()
        hs.reload()
    end

    local cfgWatcher = obj.d['cfgWatcher']
    if not cfgWatcher or not cfgWatcher:running() then
        cfgWatcher = hs.pathwatcher.new(hs.configdir, notifyAndReload)
        obj.d['cfgWatcher'] = cfgWatcher
        cfgWatcher:start()
    end

    keys = obj.map['reloadConfig']
    hs.hotkey.bind(keys[1], keys[2], notifyAndReload)
end

function obj:_setupAppLauncher(keymap, modifiers)
    local modifiers = modifiers or 'ctrl+alt'
    local keymap = keymap or {
        a = 'App Store',
        b = 'Safari',
        c = 'Visual Studio Code',
        --d = 'TickTick',
        d = 'Eudic',
        e = 'Emacs',
        f = 'Finder',
        g = 'Google Chrome',
        h = 'Hammerspoon',
        --i = 'iTerm',
        --j = 'Activity Monitor',
        --k = 'Shortcuts',
        --l = 'Launchpad',
        m = 'QQMusic',
        n = 'Notion',
        --o = 'Microsoft Outlook',
        o = 'Obsidian',
        p = 'Photos',
        q = 'QQ',
        r = 'Reminders',
        s = 'System Preferences',
        t = 'iTerm',
        --u = 'Eudic',
        v = 'MacVim',
        w = 'WeChat',
        x = 'XMind',
        y = 'Mail',
        --z = 'System Preferences'
    }

    for k, v in pairs(keymap) do
        hs.hotkey.bind(modifiers, k, function()
            hs.application.launchOrFocus(v)
        end)
        -- update obj.map
        obj.map[v] = { modifiers, k }
    end
end

function obj:_setupWindowManager()
    local id = 'windowManager'
    local keys = obj.map[id]
    local cmodal = hs.hotkey.modal.new(keys[1], keys[2])

    function cmodal:entered() hs.alert(string.format('Entered %s mode', id)) end

    function cmodal:exited() hs.alert(string.format('Exited %s mode', id)) end

    cmodal:bind('', 'escape', function()
        cmodal:exit()
    end)

    local function move(direction, step)
        local step = step or 10
        local w = hs.window.focusedWindow()
        local f = w:frame()

        if direction == 'up' then
            f.y = f.y - step
        end
        if direction == 'down' then
            f.y = f.y + step
        end
        if direction == 'left' then
            f.x = f.x - step
        end
        if direction == 'right' then
            f.x = f.x + step
        end
        w:setFrame(f)
    end

    local mapping = {
        up = 'k',
        down = 'j',
        left = 'h',
        right = 'l',
    }
    cmodal:bind('ctrl+alt', '/', function()
        obj:_toggleHelp(mapping)
    end)

    for k, v in pairs(mapping) do
        cmodal:bind('', v, function()
            move(k)
        end)
    end
end

function obj:_toggleHelp(data)
    local helpCanvas = obj.o['helpCanvas']
    if helpCanvas and helpCanvas:isShowing() then
        helpCanvas:hide()
    else
        local mainRes = hs.screen.primaryScreen():fullFrame()
        local helpCanvas = hs.canvas.new({ x = (mainRes.w - 600) / 2, y = (mainRes.h - 700) / 2, w = 600, h = 700 }):
            appendElements(
                {
                    type = "rectangle",
                    action = "fill",
                    fillColor = { hex = "#EEEEEE", alpha = 0.95 },
                    roundedRectRadii = { xRadius = 10, yRadius = 10 },
                },
                {
                    type = 'text',
                    text = hs.inspect(data or obj.map) .. '\n\n 😄',
                    textSize = 20,
                    textColor = { hex = "#2390FF", alpha = 1 },
                    textAlignment = 'left',
                }
            )
        obj.o['helpCanvas'] = helpCanvas
        helpCanvas:show()
    end
end

---- main
obj:init():bindHotkeys(obj.map):start()
return obj](<-- hammerspoon config example
-- date: 2022-11-08

local obj = {}
obj._metadata = {
    name = 'hammerspoon config example',
    version = '1.0',
    author = '',
    homepage = '',
    license = 'MIT - https://opensource.org/licenses/MIT',
}

obj.cfg = {}
obj.map = {
    reloadConfig = { { 'ctrl', 'cmd' }, 'r' },
    toggleHelp = { { 'ctrl', 'alt' }, '/' },
    windowManager = { { 'alt', 'cmd' }, 'w' },
    toggleClock = {{'ctrl', 'cmd'}, 't'},
}
obj.spoons = {}

----
function obj:init()
    for k, v in pairs(obj._metadata) do obj[k] = v end
    for _, v in ipairs(obj.spoons) do hs.loadSpoon(v) end

    obj.watchers = {}
    obj.timers = {}
    obj.canvases = {}
    return self
end

function obj:start()
    obj:_setupReloadConfig()
    obj:_setupAppLauncher()
    obj:_setupWindowManager()
    obj:_toggleClock(true)
    return self
end

function obj:stop()
    return self
end

function obj:bindHotkeys(mapping)
    local def = {
        toggleHelp = function()
            obj:_toggleHelp()
        end,
        toggleClock = function ()
            obj:_toggleClock()
        end,
    }
    for k, v in pairs(mapping) do
        if def[k] then
            hs.hotkey.bind(v[1], v[2], def[k])
        end
    end
    return self
end

---
function obj:_setupReloadConfig()
    local function notifyAndReload()
        hs.notify.new({ title = "Hammerspoon", informativeText = "Config reloaded." }):send()
        hs.reload()
    end

    local cfgWatcher = obj.watchers['cfgWatcher']
    if not cfgWatcher or not cfgWatcher:running() then
        cfgWatcher = hs.pathwatcher.new(hs.configdir, notifyAndReload)
        obj.watchers['cfgWatcher'] = cfgWatcher
        cfgWatcher:start()
    end

    keys = obj.map['reloadConfig']
    hs.hotkey.bind(keys[1], keys[2], notifyAndReload)
end

function obj:_setupAppLauncher(keymap, modifiers)
    local modifiers = modifiers or 'ctrl+alt'
    local keymap = keymap or {
        a = 'App Store',
        b = 'Safari',
        c = 'Visual Studio Code',
        --d = 'TickTick',
        d = 'Eudic',
        e = 'Emacs',
        f = 'Finder',
        g = 'Google Chrome',
        h = 'Hammerspoon',
        --i = 'iTerm',
        --j = 'Activity Monitor',
        --k = 'Shortcuts',
        --l = 'Launchpad',
        m = 'QQMusic',
        n = 'Notion',
        --o = 'Microsoft Outlook',
        o = 'Obsidian',
        p = 'Photos',
        q = 'QQ',
        r = 'Reminders',
        s = 'System Preferences',
        t = 'iTerm',
        --u = 'Eudic',
        v = 'MacVim',
        w = 'WeChat',
        x = 'XMind',
        y = 'Mail',
        --z = 'System Preferences'
    }

    for k, v in pairs(keymap) do
        hs.hotkey.bind(modifiers, k, function()
            hs.application.launchOrFocus(v)
        end)
        -- update obj.map
        obj.map[v] = { modifiers, k }
    end
end

function obj:_setupWindowManager()
    local id = 'windowManager'
    local keys = obj.map[id]
    local cmodal = hs.hotkey.modal.new(keys[1], keys[2])

    function cmodal:entered() hs.alert(string.format('Entered %s mode', id)) end

    function cmodal:exited() hs.alert(string.format('Exited %s mode', id)) end

    cmodal:bind('', 'escape', function()
        cmodal:exit()
    end)

    local function move(direction, step)
        local step = step or 10
        local w = hs.window.focusedWindow()
        local f = w:frame()

        if direction == 'up' then
            f.y = f.y - step
        end
        if direction == 'down' then
            f.y = f.y + step
        end
        if direction == 'left' then
            f.x = f.x - step
        end
        if direction == 'right' then
            f.x = f.x + step
        end
        w:setFrame(f)
    end

    local mapping = {
        up = 'k',
        down = 'j',
        left = 'h',
        right = 'l',
    }
    cmodal:bind('ctrl+alt', '/', function()
        obj:_toggleHelp(mapping)
    end)

    for k, v in pairs(mapping) do
        cmodal:bind('', v, function()
            move(k)
        end)
    end
end

function obj:_toggleHelp(data)
    local function create()
        local mainRes = hs.screen.primaryScreen():fullFrame()
        local helpCanvas = hs.canvas.new({ x = (mainRes.w - 600) / 2, y = (mainRes.h - 700) / 2, w = 600, h = 700 }):
            appendElements(
                {
                    type = "rectangle",
                    action = "fill",
                    fillColor = { hex = "#EEEEEE", alpha = 0.95 },
                    roundedRectRadii = { xRadius = 10, yRadius = 10 },
                },
                {
                    type = 'text',
                    text = hs.inspect(data or obj.map) .. '\n\n 😄',
                    textSize = 20,
                    textColor = { hex = "#2390FF", alpha = 1 },
                    textAlignment = 'left',
                }
            )
        return helpCanvas
    end

    local helpCanvas = obj.canvases['helpCanvas']

    if not helpCanvas then
        helpCanvas = create()
        obj.canvases['helpCanvas'] = helpCanvas
    end
    if helpCanvas:isShowing() then
        helpCanvas:hide()
    else
        helpCanvas:show()
    end
end

function obj:_toggleClock(bool)
    local function create()
        local mainRes = hs.screen.primaryScreen():fullFrame()
        local clockCanvas = hs.canvas.new({x=0, y=mainRes.h - 60*2, w=200, h=60*2}):appendElements(
            {
                type = 'rectangle',
                action = 'fill',
                fillColor = {red=0, blue=0, green=0, alpha=0}
            },
            {
                type = 'text',
                text = os.date('%a %b %e'),
                textSize = 20,
                textColor = {hex='#1891C3'},
                textAlignment = 'left',
                frame = {x=10, y=30, w=200, h=60}
            },
            {
                type = 'text',
                text = os.date('%H:%M'),
                textSize = 40,
                textColor = {hex='#1891C3'},
                textAlignment = 'left',
                frame = {x=10, y=60, w=120, h=60}
            }
        )
        clockCanvas:bringToFront(true)
        clockCanvas:behavior(hs.canvas.windowBehaviors.canJoinAllSpaces)
        return clockCanvas
    end

    local clockCanvas = obj.canvases['clockCanvas']
    local clockTimer = obj.timers['clockTimer']

    if not clockCanvas then
        clockCanvas = create()
        obj.canvases['clockCanvas'] = clockCanvas
        clockTimer = hs.timer.doEvery(20, function()
            clockCanvas[2].text = os.date('%a %b %e')
            clockCanvas[3].text = os.date('%H:%M')
        end)
        obj.timers['clockTimer'] = clockTimer
    end
    if clockCanvas:isShowing() then
        if not bool then
            clockCanvas:hide()
        end
    else
        if bool ~= false then
            clockCanvas:show()
        end
    end
end

---- main
obj:init():bindHotkeys(obj.map):start()
return obj>)
```

## [插件](https://www.hammerspoon.org/Spoons/)