---
ms.openlocfilehash: acb5b467fc8f0692d8fa1b3b8263fd27308cc124
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617150"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>Správně WebUtility.HtmlEncode a WebUtility.HtmlDecode Round-Trip BMP

#### <a name="details"></a>Podrobnosti

Pro aplikace, které cílí na .NET Framework 4,5, jsou znaky, které se předávají do metod, v případě, že jsou předávány do metod,, které jsou mimo základní (standarded) (BMP) <xref:System.Net.WebUtility.HtmlDecode(System.String)>

#### <a name="suggestion"></a>Návrh

Tato změna by neměla mít žádný vliv na aktuální aplikace, ale chcete-li obnovit původní chování, nastavte `targetFramework` atribut `<httpRuntime>` prvku na jiný řetězec než "4,5". Můžete také nastavit `unicodeEncodingConformance` `unicodeDecodingConformance` atributy a `<webUtility>` elementu konfigurace pro řízení tohoto chování nezávisle na cílové verzi .NET Framework.

| Name    | Hodnota       |
|:--------|:------------|
| Rozsah   | Edge        |
| Verze | 4.5         |
| Typ    | Změna cílení |

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType>
- <xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType>
