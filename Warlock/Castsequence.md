
# Castsequence, drain soul if all dots are up

For the Drain Soul function , please see the below 

[SoulDrain function](Drain Soul.md#Drain-Soul-with-life-tap-and-drain-life)

**Add in extended lua**
```lua

function SpellRotation()

    if CleveRoids.CheckCondition("nodebuff:Curse of Shadow,nodebuff:Curse of Agony") then
        CleveRoids.DoCast("Curse of Shadow")
        return 
    end

    if CleveRoids.CheckCondition("nodebuff:Corruption") then
        CleveRoids.DoCast("Corruption")
        return
    end

    if CleveRoids.CheckCondition("nodebuff:Siphon Life") then 
        CleveRoids.DoCast("Siphon Life")
        return 
    end
    
    if CleveRoids.CheckCondition("debuff:Curse of Shadow,debuff:Curse of Agony,debuff:Corruption,debuff:Siphon Life") then
        SoulDrain()
        return
    end

end
```

**Call in macro**
```lua
/script SpellRotation()
```

## Castsequence Siphon Life, CoA, Corruption, Immolate
```
/run local _gspells = { "Siphon Life", "Curse of Agony", "Corruption", "Immolate"} if GetSpellCooldown(4,"BOOKTYPE_SPELL")==0 then _gi=_gi and _gi > 0 and _gi or 1 CastSpellByName(_gspells[_gi]) _gi = math.mod(1+_gi, 1+table.getn(_gspells))end
```


## Buff Detect Inivisibility, Unending Breath
```
/run local _gspells = { "Detect Invisibility", "Unending Breath"} if GetSpellCooldown(4,"BOOKTYPE_SPELL")==0 then _gi=_gi and _gi > 0 and _gi or 1 CastSpellByName(_gspells[_gi]) _gi = math.mod(1+_gi, 1+table.getn(_gspells))end
```
