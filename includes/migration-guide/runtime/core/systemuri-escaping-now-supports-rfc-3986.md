---
ms.openlocfilehash: 1654d58651bf14b0e7c21de2afa827634b7db858
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235330"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a>System.Uri uvozovacích znaků nyní podporuje RFC 3986

|   |   |
|---|---|
|Podrobnosti|Identifikátor URI uvození došlo ke změně v rozhraní .NET Framework 4.5 na podporu [RFC 3986](https://tools.ietf.org/html/rfc3986). Konkrétní změny patří:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> řídí vyhrazené znaky dle RFC 3986.</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> neuvozuje vyhrazené znaky.</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> nevyvolá výjimku, pokud nalezne neplatnou řídicí sekvenci.</li><li>Nerezervované řídicí znaky nejsou uvozeny řídicími znaky.</li></ul>|
|Doporučení|<ul><li>Aktualizace aplikace není závislý na <xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> vyvolá v případě neplatnou řídicí sekvenci. Tato sekvence musí být rozpoznány přímo nyní.</li><li>Podobně očekávají, že Escaped a znakem identifikátor URI a Data řetězce mohou se lišit od rozhraní .NET Framework 4.0 a rozhraní .NET Framework 4.5 a by neměl být porovnat se verze rozhraní .NET přímo. Místo toho jejich analyzovat a před všechny porovnávání normalized v jedné verzi rozhraní .NET.</li></ul>|
|Rozsah|Vedlejší|
|Version|4.5|
|Type|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
