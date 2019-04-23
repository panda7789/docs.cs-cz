---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59981539"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad by neměl v souboru vlastní možnosti použít, protože je nyní schopnostech prohlížeče

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, iPad je identifikátor v výchozí prohlížeč možnosti souboru ASP.NET, proto by neměl být použít v souboru vlastní funkce|
|Doporučení|Pokud funkce specifické pro iPad, je potřeba změnit chování iPad nastavením možnosti na předem definované brány refID &quot;IPad&quot; místo generováním nového &quot;IPad&quot; ID podle uživatelského agenta porovnávání.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
