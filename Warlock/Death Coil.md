## Death Coil + Fear

Macro will cast death coil if off CD , then cast fear. Else , just cast fear. 

**Add in extended lua** 
```lua
function dc() 
   if CleveRoids.CheckCondition("usable:Death Coil") then 
       CleveRoids.DoCast("Death Coil")
       CleveRoids.DoCast("Fear")
       return 

    else
       CleveRoids.DoCast("Fear")
    end
end
```

**In macro** 
```lua
/script dc()
```

