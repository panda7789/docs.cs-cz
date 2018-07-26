### <a name="managed-browser-hosting-controls-from-the-net-framework-11-and-20-are-blocked"></a>Hostitelské ovládací prvky spravovaného prohlížeče v rozhraní .NET Framework 1.1 a 2.0 jsou zablokované.

|   |   |
|---|---|
|Podrobnosti|Hostování těchto ovládacích prvků je blokováno v aplikaci Internet Explorer.|
|Návrh|Internet Explorer nespustí aplikaci, která používá hostovací ovládací prvky spravovaného prohlížeče. Předchozí chování lze obnovit nastavením hodnoty EnableIEHosting podklíče registru <code>HKLM/SOFTWARE/MICROSOFT/.NETFramework</code> k <code>1</code> pro x86 systémy a pro 32bitové procesy v x64 systémů a tím, že nastavíte <code>EnableIEHosting</code> podklíče registru <code>HKLM/SOFTWARE/Wow6432Node/Microsoft/.NETFramework</code>k <code>1</code> pro 64bitové procesy v x64 systémy.|
|Rozsah|Vedlejší|
|Version|4.5|
|Typ|Modul runtime|

