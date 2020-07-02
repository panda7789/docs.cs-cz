---
ms.openlocfilehash: 1d7dc808d5b514acc582675d6ccdbd5778314624
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619990"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a>Uvozovací znaky System. URI teď podporují RFC 3986.

#### <a name="details"></a>Podrobnosti

Uvozovací znaky URI se v .NET Framework 4,5 změnily na podporu [RFC 3986](https://tools.ietf.org/html/rfc3986). Mezi konkrétní změny patří:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=fullName>řídí vyhrazené znaky na základě RFC 3986.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=fullName>neřídí vyhrazené znaky.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName>nevyvolá výjimku, pokud nalezne neplatnou řídicí sekvenci.</li><li>Nerezervované řídicí znaky nejsou uvozeny řídicími znaky.</li></ul>

#### <a name="suggestion"></a>Návrh

<ul><li>Aktualizujte aplikace tak, aby se nespoléhaly na <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=fullName> vyvolání v případě neplatné řídicí sekvence. Tyto sekvence musí být zjišťovány přímo nyní.</li><li>Podobně lze očekávat, že řídicí a neřídící identifikátor URI a datové řetězce se mohou lišit od .NET Framework 4,0 a .NET Framework 4,5 a nesmí být porovnány přímo v různých verzích rozhraní .NET. Místo toho by se měly analyzovat a normalizovat v jedné verzi rozhraní .NET před provedením jakýchkoli porovnání.</li></ul>

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.5|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
