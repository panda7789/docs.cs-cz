---
ms.openlocfilehash: bb163d5a6eb3d926a44a83ea79572c3a497bbe8d
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181833"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy v oboru názvů Microsoft. VisualBasic. Devices není k dispozici.

Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů nejsou k dispozici.

#### <a name="version-introduced"></a>Představená verze

.NET Core 3,0 Preview 8

#### <a name="details"></a>Podrobnosti

Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3,0 Preview,. Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.

Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.
 
#### <a name="recommended-action"></a>Doporučená akce

Pokud váš kód závisí na použití <xref:Microsoft.VisualBasic.Devices> typů a jejich členů, může být možné použít odpovídající typ nebo člen v knihovně tříd .NET. <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> Například ekvivalentní funkce třídy jsou poskytovány <xref:System.Environment?displayProperty=nameWithType> <xref:System.DateTime?displayProperty=nameWithType> typy a a ekvivalentní funkce <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> třídy jsou poskytovány typy v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů.

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

