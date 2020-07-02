---
ms.openlocfilehash: af10716fe5f4c07091e8605cdf620e4a499fb1e8
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619942"
---
### <a name="ipad-should-not-be-used-in-custom-capabilities-file-because-it-is-now-a-browser-capability"></a>IPad by se neměl používat v souboru vlastních schopností, protože je teď funkcí prohlížeče.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5 je iPad identifikátorem ve výchozím souboru schopností prohlížeče ASP.NET, takže by se neměl používat ve vlastním souboru schopností.

#### <a name="suggestion"></a>Návrh

Pokud jsou nutné možnosti specifické pro iPad, je nutné upravit chování iPadu nastavením možností na předem definované bráně refID &quot; iPad, &quot; nikoli vygenerováním nového &quot; ID iPadu &quot; , které odpovídá uživatelskému agentu.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Edge|
|Verze|4.5|
|Typ|Modul runtime|
