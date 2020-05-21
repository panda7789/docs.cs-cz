---
ms.openlocfilehash: a35de09b9a7bb9686433205359c3cc55954c29c3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721101"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy v oboru názvů Microsoft. VisualBasic. Devices není k dispozici.

Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů nejsou k dispozici.

#### <a name="version-introduced"></a>Představená verze

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Popis změny

Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3,0 Preview,. Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.

Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.

#### <a name="recommended-action"></a>Doporučená akce

Pokud váš kód závisí na použití <xref:Microsoft.VisualBasic.Devices> typů a jejich členů, může být možné použít odpovídající typ nebo člen v knihovně tříd .NET. Například ekvivalentní funkce <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> třídy jsou poskytovány <xref:System.DateTime?displayProperty=nameWithType> typy a a <xref:System.Environment?displayProperty=nameWithType> ekvivalentní funkce <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> třídy jsou poskytovány typy v <xref:System.IO.Ports?displayProperty=nameWithType> oboru názvů.

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

#### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
