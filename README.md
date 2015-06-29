# lua-signal
基于lua的signal的发射器,方便类之间事件传递.

# 使用

```lua
local TestVO = class("TestVO")

function TestVO:ctor()
    print("testVO:Ctor")

    TestVO.super.ctor(self)x
    self:setproperty({"id", 1, didSet= function(v)
        end})

    self.testSignal = require("core.Signal").new()


end

function TestVO:fireSignal()
    self.testSignal:fire(".....test.....")
end


local vo = TestVO.new()

return vo
```

主类监听:

```lua
 local vo = require(“TestVO”)
  vo.testSignal:add(function(param)
      print("param:", param)
    end)


    vo:fireSignal()

    vo.testSignal:addOnce(function(param)
      print("once_param:", param)
    end)


    vo:fireSignal()

    vo:fireSignal()
```

打印了

```lua
[LUA-print] param:    .....test.....
[LUA-print] param:    .....test.....
[LUA-print] once_param:    .....test.....
[LUA-print] param:    .....test.....
```

## `TODO`
1. 事件优先级
2. cocos2dx-lua内置事件绑定
