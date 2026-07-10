## Curse of Tongues if target got mana, else Curse of Weakness
```
/run if (UnitMana("target")>0) then CastSpellByName("Curse of Tongues") else CastSpellByName("Curse of Weakness") end
```
**In extended lua** 
```lua
function cot() 
    if CleveRoids.CheckCondition("exists,harm,powertype:mana") then 
        CleveRoids.DoCast("Curse of Tongues")
        return
    else
        CleveRoids.DoCast("Curse of Weakness") 
        return
    end
end
    
```

**In macro**
```lua
/script cot() 
```
