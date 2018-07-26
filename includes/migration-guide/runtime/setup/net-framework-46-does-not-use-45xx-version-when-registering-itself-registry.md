### <a name="the-net-framework-46-does-not-use-a-45xx-version-when-registering-itself-in-the-registry"></a>Rozhraní .NET Framework 4.6 nepoužívá verzi 4.5.x.x při registraci v registru

|   |   |
|---|---|
|Podrobnosti|Jak očekávat, klíč verze nastaven v registru (na <code>HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\NET Framework Setup\NDP\v4\Full</code>) pro rozhraní .NET Framework 4.6 začíná řetězcem "4.6", ne "4.5". K tomu, že 4.6 je nová verze je to možné, a ten, který je kompatibilní s předchozím 4.5.x uvolní se musí aktualizovat aplikace, které závisí na těchto klíčů registru vědět, jaké verze rozhraní .NET Framework jsou nainstalovány v počítači.|
|Návrh|Aktualizace aplikace zjišťování pro rozhraní .NET Framework 4.5 nainstalujte tím, že hledají 4.5 klíčů registru také přijímat 4.6.|
|Rozsah|Edge|
|Version|4.6|
|Typ|Modul runtime|

