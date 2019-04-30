---
ms.openlocfilehash: 7252936bd716752208abc54b4ae4bc9e23be092f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665591"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>Zprostředkovatel komunikace s objekty .NET bude nyní QueryInterface pro IAgileObject (rozhraní WinRT)

|   |   |
|---|---|
|Podrobnosti|Při použití WinRT události .NET delegátem, Windows se QI pro IAgileObject počínaje 4.8 rozhraní .NET Framework.  V předchozích verzích rozhraní .NET Framework modul runtime této QI selže a události nelze nejdřív přihlásit k odběru.<ul><li>[x] quirked</li></ul>|
|Doporučení|Pokud povolíte QI pro IAgileObject konce provádění, můžete zakázat tento kód tak, že nastavíte následující konfiguraci. <h4>Metoda 1: Proměnná prostředí</h4> Nastavte následující proměnné prostředí: COMPLUS_DisableCCWSupportIAgileObject = 1Pokud metoda ovlivňuje všechny prostředí, která dědí této proměnné prostředí. To může být jen jedné konzoly pro relaci nebo pokud jste nastavili proměnnou prostředí globálně by mohla ovlivnit celý počítač. Název proměnné prostředí není malá a velká písmena. <h4>Metoda 2: Registru</h4> Pomocí Editoru registru (regedit.exe), nalézt jednu z následujících subkeys:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkThen přidejte následující: Hodnota name: Typ DisableCCWSupportIAgileObject: Hodnota (také nazývané REG_WORD) hodnotu DWORD (32bitová verze): 1Objekty můžete použít Windows REG. Nástroj EXE přidáte tuto hodnotu z prostředí příkazového řádku nebo skriptu. Příklad:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>V takovém případě <code>HKLM</code> se použije namísto <code>HKEY_LOCAL_MACHINE</code>. Použití <code>reg add /?</code> zobrazíte nápovědu k této syntaxe. Název hodnoty registru není malá a velká písmena.|
|Rozsah|Edge|
|Version|4.8|
|Type|Modul runtime|
