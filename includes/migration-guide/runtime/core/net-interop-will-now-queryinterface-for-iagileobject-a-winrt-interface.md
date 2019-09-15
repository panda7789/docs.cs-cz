---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997584"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>Zprostředkovatel komunikace s .NET se teď bude naqueryinterface pro IAgileObject (rozhraní WinRT).

|   |   |
|---|---|
|Podrobnosti|Při použití události WinRT s delegátem .NET se systém Windows QI pro IAgileObject počínaje .NET Framework 4,8.  V předchozích verzích .NET Framework modul runtime selhání QI a událost se nepovedlo přihlásit k odběru.<ul><li>[x] Quirked</li></ul>|
|Doporučení|Pokud povolíte QI pro provádění přerušení IAgileObject, můžete tento kód zakázat nastavením následující konfigurace. <h4>Metoda 1: Proměnná prostředí</h4> Nastavte následující proměnnou prostředí: COMPLUS_DisableCCWSupportIAgileObject = 1This metoda ovlivňuje všechna prostředí, která dědí tuto proměnnou prostředí. Může to být pouze jedna relace konzoly nebo může ovlivnit celý počítač, pokud nastavíte proměnnou prostředí globálně. V názvu proměnné prostředí se nerozlišují velká a malá písmena. <h4>Metoda 2: Registru</h4> Pomocí Editoru registru (Regedit. exe) Najděte některý z následujících podklíčů: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkThen přidejte následující: název hodnoty: Typ DisableCCWSupportIAgileObject: Hodnota DWORD (32) (označovaná také jako REG_WORD): 1You může používat Windows REG. Nástroj EXE pro přidání této hodnoty z příkazového řádku nebo skriptovacího prostředí. Příklad:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>V tomto případě <code>HKLM</code> se používá <code>HKEY_LOCAL_MACHINE</code>místo. Pomocí <code>reg add /?</code> zobrazíte v nápovědě k této syntaxi. V názvu hodnoty registru se nerozlišují malá a velká písmena.|
|Scope|Edge|
|Version|4.8|
|type|Modul runtime|
