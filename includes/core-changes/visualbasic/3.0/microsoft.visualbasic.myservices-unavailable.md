---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116362"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Typy v oboru názvů Microsoft. VisualBasic. MyServices nejsou k dispozici.

Typy v oboru názvů <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> nejsou k dispozici.

#### <a name="version-introduced"></a>Představená verze

.NET Core 3,0 Preview 8

#### <a name="change-description"></a>Popis změny

Typy v oboru názvů <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> byly k dispozici v některých verzích .NET Core 3,0 Preview. Již nejsou od verze .NET Core 3,0 Preview 9 k dispozici.

Typy byly odebrány, aby nedocházelo k zbytečným závislostem sestavení nebo k zásadním změnám v následujících verzích.

#### <a name="recommended-action"></a>Doporučená akce

Pokud váš kód závisí na použití typů **Microsoft. VisualBasic. MyServices** a jejich členů, existují odpovídající typy a členy v knihovně tříd .NET. Následuje mapování typů **Microsoft. VisualBasic. MyServices** na odpovídající typy knihoven tříd .NET:

|Microsoft. VisualBasic. MyServices – typ|Typ knihovny tříd .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType> pro aplikace WPF <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> pro model Windows Forms aplikace|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Typy v oboru názvů <xref:System.IO>|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Typy související s registrem v oboru názvů <xref:Microsoft.Win32>|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
