## Spammable Drain Life
 
```lua
function LifeDrain() 
    if CleveRoids.CheckCondition("checkchanneled:Drain Life") then 
        CleveRoids.DoCast("Drain Life")
        return
    end
end
```

```lua
/script LifeDrain() 
```
