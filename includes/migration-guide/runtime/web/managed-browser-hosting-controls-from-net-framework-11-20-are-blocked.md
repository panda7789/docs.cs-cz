### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Hostování ovládacích prvků spravovaný prohlížeč z rozhraní .NET Framework 1.1 a 2.0 jsou zablokované.

|   |   |
|---|---|
|Podrobnosti|Hostování těchto ovládacích prvků je blokováno v aplikaci Internet Explorer.|
|Návrh|Internet Explorer nespustí aplikaci, která používá hostovací ovládací prvky spravovaného prohlížeče. Předchozí chování může být obnovena nastavením hodnoty EnableIEHosting podklíče registru <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> k <code>1</code> pro x86 systémy a pro 32-bit procesy ve x64 systémů a nastavením <code>EnableIEHosting</code> hodnoty podklíče registru <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>k <code>1</code> pro 64bitové procesy na x64 systémy.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|modul runtime|

