---
ms.openlocfilehash: f7dcf9c4c3dc7ea536ddc847769a1a30f1298bb2
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617211"
---
### <a name="systemuriiswellformeduristring-method-returns-false-for-relative-uris-with-a-colon-char-in-first-segment"></a>Metoda System. URI. IsWellFormedUriString vrátí hodnotu false pro relativní identifikátory URI s znakem dvojtečky v prvním segmentu.

#### <a name="details"></a>Podrobnosti

Počínaje .NET Framework 4,5, <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)> se budou považovat relativní identifikátory URI s `:` v prvním segmentu za nesprávný formát. Jedná se o změnu z <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> chování v .NET Framework 4,0, které bylo provedeno v souladu s RFC3986.

#### <a name="suggestion"></a>Návrh

Tato změna (například mnoho dalších změn identifikátorů URI) ovlivní pouze aplikace cílené na .NET Framework 4,5 (nebo novější). Chcete-li nadále používat staré chování, zaměřte aplikaci na .NET Framework 4,0. Případně můžete vyhledat identifikátor URI před voláním <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=fullName> hledání `:` znaků, které můžete chtít odebrat pro účely ověřování, pokud je staré chování žádoucí.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Vedlejší       |
| Verze | 4.5         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Uri.IsWellFormedUriString(System.String,System.UriKind)?displayProperty=nameWithType>
