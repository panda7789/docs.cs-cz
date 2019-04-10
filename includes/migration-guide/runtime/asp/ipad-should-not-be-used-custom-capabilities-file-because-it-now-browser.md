---
ms.openlocfilehash: 84f570cbbd97be79426e117d4c97ec182a397fd4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235275"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad by neměl v souboru vlastní možnosti použít, protože je nyní schopnostech prohlížeče

|   |   |
|---|---|
|Podrobnosti|Počínaje .NET Framework 4.5, iPad je identifikátor v výchozí prohlížeč možnosti souboru ASP.NET, proto by neměl být použít v souboru vlastní funkce|
|Doporučení|Pokud funkce specifické pro iPad, je potřeba změnit chování iPad nastavením možnosti na předem definované brány refID &quot;IPad&quot; místo generováním nového &quot;IPad&quot; ID podle uživatelského agenta porovnávání.|
|Rozsah|Edge|
|Version|4.5|
|Type|Modul runtime|
