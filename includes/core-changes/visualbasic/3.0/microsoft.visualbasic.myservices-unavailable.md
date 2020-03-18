---
ms.openlocfilehash: d207a937917da78f6b902ad8ca4f02fa9a46c2e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116362"
---
### <a name="types-in-microsoftvisualbasicmyservices-namespace-not-available"></a>Typy v oboru názvů Microsoft.VisualBasic.MyServices nejsou k dispozici.

Typy v <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> oboru názvů nejsou k dispozici.

#### <a name="version-introduced"></a>Zavedená verze

.NET Core 3.0 Náhled 8

#### <a name="change-description"></a>Popis změny

Typy v <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3.0 Preview. Již nejsou k dispozici počínaje rozhraním .NET Core 3.0 Preview 9.

Typy byly odebrány, aby se zabránilo zbytečné závislosti sestavení nebo přerušení změny v následujících verzích.

#### <a name="recommended-action"></a>Doporučená akce

Pokud váš kód závisí na použití **Microsoft.VisualBasic.MyServices** typy a jejich členy, existují odpovídající typy a členy v knihovně tříd .NET. Následuje mapování typů **Microsoft.VisualBasic.MyServices** na jejich ekvivalentní typy knihovny tříd .NET:

|Typ Microsoft.VisualBasic.MyServices|Typ knihovny tříd .NET|
|--|--|
|<xref:Microsoft.VisualBasic.MyServices.ClipboardProxy>|<xref:System.Windows.Clipboard?displayProperty=nameWithType>pro aplikace WPF pro <xref:System.Windows.Forms.Clipboard?displayProperty=nameWithType> aplikace windows forms|
|<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy>|Typy v <xref:System.IO> oboru názvů|
|<xref:Microsoft.VisualBasic.MyServices.RegistryProxy>|Typy související s <xref:Microsoft.Win32> registrem v oboru názvů|
|<xref:Microsoft.VisualBasic.MyServices.SpecialDirectoriesProxy>|<xref:System.Environment.GetFolderPath%2A?displayProperty=nameWithType>|

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.MyServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.MyServices`

-->
