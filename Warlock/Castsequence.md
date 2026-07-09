## Siphon Life, CoA, Corruption
```
/run s={"Curse of Shadow","Corruption", "Siphon Life"} if not q then q=1 end CastSpellByName(s[q]) q=q+1 if q>table.getn(s) then q=1 end
```

This macro will do a castsequence and recast the last in the event it's resisted. Due to limitations I had to forgo the castsequence functionality due to conditional state tracking ( and my own laziness to write around it ) 

**Add this in Extended lua**

```lua

step = 1 
function SpellRotation()

    if step == 1 then 
        if CleveRoids.CheckCondition("nodebuff:Curse of Shadow,nodebuff:Curse of Agony") then
            CleveRoids.DoCast("Curse of Shadow")
        else
            step = 2 
        end 
    end 

    -- Checks for CoA and CoS before casting Corruption 
    if step == 2 then 
        if CleveRoids.CheckCondition("nodebuff:Curse of Shadow,nodebuff:Curse of Agony") then
            step = 1
        else
            if CleveRoids.CheckCondition("nodebuff:Corruption") then
                CleveRoids.DoCast("Corruption")
            else
                step = 3
            end
        end
    end

    if step == 3 then
        if CleveRoids.CheckCondition("nodebuff:Corruption") then
            step = 2 

        else
            if CleveRoids.CheckCondition("nodebuff:Siphon Life") then 
                CleveRoids.DoCast("Siphon Life")
            else
                step = 1 
            end
        end 
    end



end

```

### Pseudo code

```bash 
pseudo code : 

step = 1 

IF step == 1 THEN 
    IF NOT ( CoS AND CoA ) THEN 
        CAST CoS 
    ELSE
        step = 2
    END

END 


IF step == 2 THEN 

    IF NOT ( CoS AND CoA ) THEN 
        step = 1 
    ELSE
        IF NOT Corruption THEN 
            CAST Corruption
        ELSE
            step = 3 
        END
    END
END
        

IF step == 3 THEN 
    IF NOT Corruption THEN
        step = 2 


    ELSE
        IF NOT Siphon Life THEN
            CAST Siphon Life 
        ELSE
            step = 1 
        END
    END
END 

```
```lua
/castsequence reset=target [nodebuff:Curse of Shadow,nodebuff: Curse of Agony] Curse of Shadow, [nodebuff:]
```



## Castsequence Siphon Life, CoA, Corruption, Immolate
```
/run local _gspells = { "Siphon Life", "Curse of Agony", "Corruption", "Immolate"} if GetSpellCooldown(4,"BOOKTYPE_SPELL")==0 then _gi=_gi and _gi > 0 and _gi or 1 CastSpellByName(_gspells[_gi]) _gi = math.mod(1+_gi, 1+table.getn(_gspells))end
```


## Buff Detect Inivisibility, Unending Breath
```
/run local _gspells = { "Detect Invisibility", "Unending Breath"} if GetSpellCooldown(4,"BOOKTYPE_SPELL")==0 then _gi=_gi and _gi > 0 and _gi or 1 CastSpellByName(_gspells[_gi]) _gi = math.mod(1+_gi, 1+table.getn(_gspells))end
```
