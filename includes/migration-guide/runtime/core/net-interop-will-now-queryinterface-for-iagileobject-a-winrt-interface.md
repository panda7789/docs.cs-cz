---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997584"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>Rozhraní .NET Interop bude nyní QueryInterface pro IAgileObject (rozhraní WinRT)

|   |   |
|---|---|
|Podrobnosti|Při použití události WinRT s delegátem .NET bude systém Windows QI pro IAgileObject počínaje rozhraním .NET Framework 4.8.  V předchozích verzích rozhraní .NET Framework by se selhání mj.<ul><li>[x] Nevychaný</li></ul>|
|Návrh|Pokud povolení QI pro IAgileObject přeruší spuštění, můžete zakázat tento kód nastavením následující konfigurace. <h4>Metoda 1: Proměnná prostředí</h4> Nastavte následující proměnnou prostředí:COMPLUS_DisableCCWSupportIAgileObject=1Tato metoda ovlivňuje jakékoli prostředí, které dědí tuto proměnnou prostředí. Může se jedná pouze o jednu relaci konzoly nebo může mít vliv na celý počítač, pokud nastavíte proměnnou prostředí globálně. Název proměnné prostředí není rozlišována malá a velká písmena. <h4>Metoda 2: Registr</h4> Pomocí editoru registru (regedit.exe) vyhledejte některý z následujících podklíčů:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkPak přidejte následující:Název hodnoty: DisableCCWSupportIAgileObject Typ: Hodnota DWORD (32bitová) Hodnota (také nazývaná REG_WORD) Hodnota: 1Můžete použít windows REG. EXE nástroj pro přidání této hodnoty z příkazového řádku nebo skriptovacího prostředí. Například:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>V tomto <code>HKLM</code> případě se <code>HKEY_LOCAL_MACHINE</code>používá místo . Slouží <code>reg add /?</code> k zobrazení nápovědy k této syntaxi. Název hodnoty registru není rozlišována malá a velká písmena.|
|Rozsah|Edge|
|Version|4.8|
|Typ|Modul runtime|
