# OpenEPaperLink-DagensCitat
Dagens citat i en OEPL-display ("Open EPaperLink")


Följande måste finnas i Home Assistant configuration.yaml.
Denna hämtar dagens citat och lagrar i en sensor.
q=Själva citatet
a=Författare av citatet

sensor:
  - platform: rest
    name: Daily Quote
    unique_id: daily_quote_zenquotes
    resource: https://zenquotes.io/api/today
    method: GET
    scan_interval: 86400
    value_template: "{{ value_json[0].q }}"
    json_attributes_path: "$[0]"
    json_attributes:
      - q
      - a

Texten som finns i filen HA-Automation är mall för att klistra om som Home Assistant automation.
OBS! Byt ut till rätt OEPL-tagg/Display.

Denna använder Google fria typsnitt: SourGummy-Black.ttf
Finns att hämta hem här: https://fonts.google.com/specimen/Sour+Gummy?categoryFilters=Feeling:%2FExpressive%2FCute&preview.script=Latn
Typsnitett ska ligga i Home Assistant mappen \config\media\SourGummy-Black.ttf

Lägg in innehållet i filen configuration-yaml i Home Assistant configurayion.yaml på rätt plats.
Detat för att skapa sensorer som automationen kan ansopa utan att själv behöva ha koll på vilka pollen som är mätbara.

Klista sedan in koden från automations-filen i en HA automation.
Glöm inte att ändra till korrekt OEPL-tagg/Display.


Exempel:
![DagensCitat-Exempel](https://github.com/user-attachments/assets/d4a3bd8c-7fe2-4c71-ba86-3bc9420e6873)

