---
ms.openlocfilehash: c103dff320ae30d02c12ea5c585a47b589da8237
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621133"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition DateTime vrátí mírně odlišný řetězec.

#### <a name="details"></a>Podrobnosti

Řetězcové reprezentace 's byly <xref:System.Net.Mime.ContentDisposition?displayProperty=fullName> aktualizovány, počínaje 4,6, aby vždy představovaly hodinovou komponentu <xref:System.DateTime?displayProperty=fullName> se dvěma číslicemi. To je v dodržování [RFC822](https://www.ietf.org/rfc/rfc0822.txt) a [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). To způsobí, <xref:System.Net.Mime.ContentDisposition.ToString> že v případě, že jeden z časových prvků dispozice byl před 10:00 dop., se v 4,6 ve scénářích vrátí trochu odlišný řetězec. Všimněte si, že ContentDispositions jsou někdy serializovány prostřednictvím převodu na řetězce, takže <xref:System.Net.Mime.ContentDisposition.ToString> by měly být přezkoumány všechny operace, serializace nebo volání GetHashCode.

#### <a name="suggestion"></a>Návrh

Neočekává se, že řetězcové reprezentace ContentDispositions z různých verzí .NET Framework budou správně porovnány. Pokud je to možné, převeďte řetězce zpět na ContentDispositions, než provedete porovnání.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   |Vedlejší|
|Verze|4.6|
|Typ|Modul runtime

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

-<xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
