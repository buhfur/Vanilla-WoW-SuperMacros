
# Castsequence, drain soul if all dots are up

Does all dots , once all dots are up , runs soul drain
Once health is below 10% , use drain life 

**Call in macro**
```lua
/petattack
/cast [nodebuff:Curse_of_Shadow/Curse_of_Agony] Curse of Shadow
/cast [nodebuff:Corruption] Corruption
/cast [nodebuff:Siphon_Life] Siphon Life

/stopcasting [mypower:<10]

/cast [mypower:<10,myhp:>20] Life Tap
/cast [mypower:<10,myhp:<20,usable:Drain_Life] Drain Life

/cast [mypower:>=10,checkchanneled:Drain_Soul&Siphon_Life&Curse_of_Shadow&Curse_of_Agony&Corruption] Drain Soul
```

## Castsequence Siphon Life, CoA, Corruption, Immolate
```
/run local _gspells = { "Siphon Life", "Curse of Agony", "Corruption", "Immolate"} if GetSpellCooldown(4,"BOOKTYPE_SPELL")==0 then _gi=_gi and _gi > 0 and _gi or 1 CastSpellByName(_gspells[_gi]) _gi = math.mod(1+_gi, 1+table.getn(_gspells))end
```


## Buff Detect Inivisibility, Unending Breath
```
/run local _gspells = { "Detect Invisibility", "Unending Breath"} if GetSpellCooldown(4,"BOOKTYPE_SPELL")==0 then _gi=_gi and _gi > 0 and _gi or 1 CastSpellByName(_gspells[_gi]) _gi = math.mod(1+_gi, 1+table.getn(_gspells))end
```
