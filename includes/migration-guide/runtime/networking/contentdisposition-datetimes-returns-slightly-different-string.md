---
ms.openlocfilehash: 705bbd0e0bf80e0726d41898685a5e166e039f99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "67858595"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition DateTimes vrátí mírně odlišný řetězec

|   |   |
|---|---|
|Podrobnosti|Řetězcové reprezentace <xref:System.Net.Mime.ContentDisposition?displayProperty=name>s byly aktualizovány, počínaje 4.6, aby vždy <xref:System.DateTime?displayProperty=name> představovaly hodinovou složku a se dvěma číslicemi. To je v souladu s [RFC822](https://www.ietf.org/rfc/rfc0822.txt) a [RFC2822](https://www.ietf.org/rfc/rfc2822.txt). To <xref:System.Net.Mime.ContentDisposition.ToString> způsobí, že vrátit mírně jiný řetězec v 4.6 ve scénářích, kde jeden z dispozičních časových prvků byl před 10:00. Všimněte si, že ContentDispositions jsou někdy serializovány <xref:System.Net.Mime.ContentDisposition.ToString> prostřednictvím jejich převodu na řetězce, takže všechny operace, serializace nebo GetHashCode volání by měly být přezkoumány.|
|Návrh|Neočekávejte, že řetězcové reprezentace ContentDispositions z různých verzí rozhraní .NET Framework budou správně porovnávány navzájem. Převeďte řetězce zpět na ContentDispositions, pokud je to možné, před provedením porovnání.|
|Rozsah|Vedlejší|
|Version|4.6|
|Typ|Modul runtime|
|Ovlivněná rozhraní API|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
