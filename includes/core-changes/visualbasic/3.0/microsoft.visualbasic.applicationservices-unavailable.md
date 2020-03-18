---
ms.openlocfilehash: d8cc506d60f3c24087ebde8ead345656fea0f484
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116330"
---
### <a name="types-in-microsoftvisualbasicapplicationservices-namespace-not-available"></a>Typy v oboru názvů Microsoft.VisualBasic.ApplicationServices nejsou k dispozici.

Typy v <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> oboru názvů nejsou k dispozici.

#### <a name="version-introduced"></a>Zavedená verze

.NET Core 3.0 Náhled 8

#### <a name="change-description"></a>Popis změny

Typy v <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3.0 Preview. Již nejsou k dispozici počínaje rozhraním .NET Core 3.0 Preview 9.

Typy byly odebrány, aby se zabránilo zbytečné závislosti sestavení nebo přerušení změny v následujících verzích.

#### <a name="recommended-action"></a>Doporučená akce

Pokud váš kód závisí <xref:Microsoft.VisualBasic.ApplicationServices> na použití typů a jejich členů, můžete použít odpovídající typ nebo člen v knihovně tříd .NET. Například některé <xref:System.Environment?displayProperty=nameWithType> <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> a členy poskytují ekvivalentní funkce <xref:Microsoft.VisualBasic.ApplicationServices.User?displayProperty=nameWithType> vlastnosti třídy.

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.ApplicationServices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.ApplicationServices`

-->
