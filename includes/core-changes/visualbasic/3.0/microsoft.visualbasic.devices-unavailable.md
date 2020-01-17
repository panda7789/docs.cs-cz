---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116319"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy v oboru názvů Microsoft. VisualBasic. Devices není k dispozici.

Typy v oboru názvů <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> nejsou k dispozici.

#### <a name="version-introduced"></a>Představená verze

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Popis změny

Typy v oboru názvů <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> byly k dispozici v některých verzích .NET Core 3,0 Preview,. Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.

Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.

#### <a name="recommended-action"></a>Doporučená akce

Pokud váš kód závisí na použití <xref:Microsoft.VisualBasic.Devices> typy a jejich členů, můžete použít odpovídající typ nebo člen v knihovně třídy .NET. Například ekvivalentní funkce pro třídu <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> poskytují typy <xref:System.DateTime?displayProperty=nameWithType> a <xref:System.Environment?displayProperty=nameWithType> a ekvivalentní funkce pro <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> třídy jsou poskytovány typy v oboru názvů <xref:System.IO.Ports?displayProperty=nameWithType>.

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
