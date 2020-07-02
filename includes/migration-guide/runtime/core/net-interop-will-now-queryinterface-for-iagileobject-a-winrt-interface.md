---
ms.openlocfilehash: 150b94b55fa8f2a29f1da7cf7ac7bf6dd06b9666
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621978"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>Zprostředkovatel komunikace s .NET se teď bude naqueryinterface pro IAgileObject (rozhraní WinRT).

#### <a name="details"></a>Podrobnosti

Při použití události WinRT s delegátem .NET se systém Windows QI pro IAgileObject počínaje .NET Framework 4,8.  V předchozích verzích .NET Framework modul runtime selhání QI a událost se nepovedlo přihlásit k odběru.<ul><li>[x] Quirked</li></ul>

#### <a name="suggestion"></a>Návrh

Pokud povolíte QI pro provádění přerušení IAgileObject, můžete tento kód zakázat nastavením následující konfigurace. <h4>Metoda 1: proměnná prostředí</h4> Nastavte následující proměnnou prostředí: COMPLUS_DisableCCWSupportIAgileObject = metoda 1This má vliv na jakékoli prostředí, které dědí tuto proměnnou prostředí. Může to být pouze jedna relace konzoly nebo může ovlivnit celý počítač, pokud nastavíte proměnnou prostředí globálně. V názvu proměnné prostředí se nerozlišují velká a malá písmena. <h4>Metoda 2: registr</h4> Pomocí Editoru registru (regedit.exe) Najděte některý z následujících podklíčů: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER \SOFTWARE\Microsoft.NETFrameworkThen přidejte následující: název hodnoty: DisableCCWSupportIAgileObject typ: DWORD (32-bit) hodnota (označovaná taky jako REG_WORD): 1You může pomocí nástroje Windows REG.EXE přidat tuto hodnotu z příkazového řádku nebo skriptovacího prostředí. Příklad:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>V tomto případě <code>HKLM</code> se používá místo <code>HKEY_LOCAL_MACHINE</code> . Pomocí <code>reg add /?</code> zobrazíte v nápovědě k této syntaxi. V názvu hodnoty registru se nerozlišují malá a velká písmena.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4,8|
|Typ|Modul runtime|
