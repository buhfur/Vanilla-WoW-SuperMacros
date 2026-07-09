## Spammable Drain Mana

**Add in extended lua**
```lua
function DrainMana() 
    if CleveRoids.CheckCondition("checkchanneled:Drain Mana") then 
        CleveRoids.DoCast("Drain Mana")
        return
    end
end

```
**call from macro**

```lua
/script DrainMana()
```
