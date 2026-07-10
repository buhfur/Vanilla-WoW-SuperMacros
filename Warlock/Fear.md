## Spammable fear with stopcasting (# being the id of the action bar where you put Fear)
```
/script if GetUnitName("target")==nil then TargetNearestEnemy() end
/script if not IsCurrentAction(#) then SpellStopCasting() end;
/cast Fear(Rank 3)
```

```lua
function CastFear()
    if CleveRoids.CheckCondition("casting:Fear") then 
        SpellStopCasting()
        return
    else
        CleveRoids.DoCast("Fear")
    end

```

```lua
/script CastFear()
```

 

