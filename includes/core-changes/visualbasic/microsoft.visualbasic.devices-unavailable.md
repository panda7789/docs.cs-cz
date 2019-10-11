---
ms.openlocfilehash: dae4afa92b8833f326b4eacd00b36bb3e1199cc1
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/09/2019
ms.locfileid: "72237324"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy v oboru názvů Microsoft. VisualBasic. Devices není k dispozici.

Typy v oboru názvů <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> nejsou k dispozici.

#### <a name="version-introduced"></a>Představená verze

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Změnit popis

Typy v oboru názvů <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> byly k dispozici v některých verzích .NET Core 3,0 Preview,. Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.

Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.
 
#### <a name="recommended-action"></a>Doporučená akce

Pokud váš kód závisí na použití <xref:Microsoft.VisualBasic.Devices> a jejich členů, může být možné použít odpovídající typ nebo člen v knihovně tříd .NET. Například ekvivalentní funkce pro třídu <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> je poskytována typy <xref:System.DateTime?displayProperty=nameWithType> a <xref:System.Environment?displayProperty=nameWithType> a ekvivalentní funkce třídy <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> jsou poskytovány typy v oboru názvů <xref:System.IO.Ports?displayProperty=nameWithType>.

#### <a name="category"></a>Category

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-- >

