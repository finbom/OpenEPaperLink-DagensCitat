# OpenEPaperLink-DagensCitat
Dagens citat i en OEPL-display ("Open EPaperLink")


1. Följande måste finnas i Home Assistant configuration.yaml.
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

2. Texten som finns i filen HA-Automation är mall för att klistra om som Home Assistant automation.
OBS! Byt ut till rätt OEPL-tagg/Display.

3. Denna använder Google fria typsnitt: SourGummy-Black.ttf
Finns att hämta hem här: https://fonts.google.com/specimen/Sour+Gummy?categoryFilters=Feeling:%2FExpressive%2FCute&preview.script=Latn
Typsnittet ska ligga i Home Assistant mappen \config\media\SourGummy-Black.ttf

Exempel:
![DagensCitat-Exempel](https://github.com/user-attachments/assets/d4a3bd8c-7fe2-4c71-ba86-3bc9420e6873)

