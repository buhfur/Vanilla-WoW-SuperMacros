
# View spell ID's for all spells in spell book in separate window 

**Requires SuperMacro & SuperWoW** 

Put in extended lua 

Afterwards , save and do `/reload` then `/spelldump`

```lua
SLASH_SPELLDUMP1="/spelldump"
SlashCmdList["SPELLDUMP"]=function()
 local text=""
 local total=0
 for tab=1,GetNumSpellTabs() do
  local tabName,texture,offset,count=GetSpellTabInfo(tab)
  text=text.."\n["..(tabName or "Unknown").."]\n"
  for slot=offset+1,offset+count do
   local name,rank=GetSpellName(slot,"spell")
   if name then
    total=total+1
    text=text..slot.."  "..name
    if rank and rank~="" then text=text.."  "..rank end
    text=text.."\n"
   end
  end
 end
 text="Spellbook slots: "..total.."\n"..text
 if not SpellDumpFrame then
  SpellDumpFrame=CreateFrame("Frame","SpellDumpFrame",UIParent)
  SpellDumpFrame:SetWidth(600)
  SpellDumpFrame:SetHeight(500)
  SpellDumpFrame:SetPoint("CENTER",UIParent,"CENTER")
  SpellDumpFrame:SetFrameStrata("DIALOG")
  SpellDumpFrame:EnableMouse(true)
  SpellDumpFrame:SetMovable(true)
  SpellDumpFrame:RegisterForDrag("LeftButton")
  SpellDumpFrame:SetScript("OnDragStart",function() this:StartMoving() end)
  SpellDumpFrame:SetScript("OnDragStop",function() this:StopMovingOrSizing() end)

  local bg=SpellDumpFrame:CreateTexture(nil,"BACKGROUND")
  bg:SetAllPoints(SpellDumpFrame)
  bg:SetTexture(0,0,0,0.9)

  local close=CreateFrame("Button",nil,SpellDumpFrame,"UIPanelCloseButton")
  close:SetPoint("TOPRIGHT",SpellDumpFrame,"TOPRIGHT",0,0)

  SpellDumpScroll=CreateFrame("ScrollFrame","SpellDumpScroll",SpellDumpFrame,"UIPanelScrollFrameTemplate")
  SpellDumpScroll:SetPoint("TOPLEFT",SpellDumpFrame,"TOPLEFT",15,-35)
  SpellDumpScroll:SetPoint("BOTTOMRIGHT",SpellDumpFrame,"BOTTOMRIGHT",-35,15)

  SpellDumpEdit=CreateFrame("EditBox","SpellDumpEdit",SpellDumpScroll)
  SpellDumpEdit:SetWidth(535)
  SpellDumpEdit:SetMultiLine(true)
  SpellDumpEdit:SetAutoFocus(false)
  SpellDumpEdit:SetFontObject(ChatFontNormal)
  SpellDumpEdit:SetScript("OnEscapePressed",function() SpellDumpFrame:Hide() end)
  SpellDumpScroll:SetScrollChild(SpellDumpEdit)
 end
 SpellDumpEdit:SetText(text)
 SpellDumpEdit:SetHeight(total*15+200)
 SpellDumpFrame:Show()
end
```
