### <a name="no-longer-able-to-set-enableviewstatemac-to-false"></a>Už moct EnableViewStateMac nastavena na hodnotu false

|   |   |
|---|---|
|Podrobnosti|Technologie ASP.NET již umožňuje vývojářům zadejte <code>&lt;pages enableViewStateMac=&quot;false&quot;/&gt;</code> nebo <code>&lt;@Page EnableViewStateMac=&quot;false&quot; %&gt;</code>. V zobrazení stavu ověřovací kód zprávy (MAC) teď se vynucuje pro všechny požadavky s vložené zobrazení stavu. Jenom aplikace, které explicitně nastavit vlastnost EnableViewStateMac na <code>false</code> vliv.|
|Návrh|EnableViewStateMac musí předpokládat, že hodnota true a je třeba vyřešit případné chyby MAC (jak je popsáno v [v tomto návodu](https://support.microsoft.com/kb/2915218), která obsahuje více řešení v závislosti na tom, jaké jsou specifikace příčinu chyby MAC).|
|Rozsah|Hlavní|
|Version|4.5.2|
|Typ|Modul runtime|

