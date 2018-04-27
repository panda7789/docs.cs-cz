### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>Rozhraní .NET Framework 4.6 nepoužívá verzi 4.5.x.x při registraci sám v registru

|   |   |
|---|---|
|Podrobnosti|Jeden by se dalo očekávat, klíč verze nastavit v registru (v <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) pro rozhraní .NET Framework 4.6 začíná '4.6', není 4.5. Aplikace, které jsou závislé na tyto klíče registru vědět, jaké verze rozhraní .NET Framework, které jsou nainstalovány na počítači, je třeba aktualizovat k tomu, že je možné nová verze 4.6 a jeden, který je kompatibilní s předchozím 4.5.x uvolní.|
|Návrh|Aktualizace aplikace zjišťování pro rozhraní .NET Framework 4.5 nainstalujte tak, že vyhledá 4.5 klíčů registru také přijímat 4.6.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|

