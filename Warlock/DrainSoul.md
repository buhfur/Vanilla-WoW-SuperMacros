
## Soul Drain until 10% mana , Drain life if health is lower than 20% 

```lua
function SoulDrain() 
    BANDAGE_NAME = "Heavy Runecloth Bandage"
    if CleveRoids.CheckCondition("mypower:<10") then
        SpellStopCasting()
        if CleveRoids.CheckCondition("myhp:>20") then
            CleveRoids.DoCast("Life Tap")
            return 
        end

        if CleveRoids.CheckCondition("usable:Drain Life") then
            CleveRoids.DoCast("Drain Life")
            return
        end
        CleveRoids.DoUse(BANDAGE_NAME)
        return
    end

    if CleveRoids.CheckCondition("checkchanneled:Drain Soul") then 
        CleveRoids.DoCast("Drain Soul")
        return
    end
end

```
