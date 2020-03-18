---
ms.openlocfilehash: 7f528510e4158dad71280a7b1f269a231b8c60f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116319"
---
### <a name="types-in-microsoftvisualbasicdevices-namespace-not-available"></a>Typy v oboru názvů Microsoft.VisualBasic.Devices nejsou k dispozici

Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů nejsou k dispozici.

#### <a name="version-introduced"></a>Zavedená verze

.NET Core 3.0 Náhled 8

#### <a name="change-description"></a>Popis změny

Typy v <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName> oboru názvů byly k dispozici v některých verzích .NET Core 3.0 Preview.. Již nejsou k dispozici počínaje rozhraním .NET Core 3.0 Preview 9.

Typy byly odebrány, aby se zabránilo zbytečné závislosti sestavení nebo přerušení změny v následujících verzích.

#### <a name="recommended-action"></a>Doporučená akce

Pokud váš kód závisí <xref:Microsoft.VisualBasic.Devices> na použití typů a jejich členů, můžete použít odpovídající typ nebo člen v knihovně tříd .NET. Například ekvivalentní funkce <xref:Microsoft.VisualBasic.Devices.Clock?displayProperty=nameWithType> třídy je poskytována <xref:System.DateTime?displayProperty=nameWithType> <xref:System.Environment?displayProperty=nameWithType> a typy a ekvivalentní <xref:Microsoft.VisualBasic.Devices.Ports?displayProperty=nameWithType> funkce třídy je poskytována typy v oboru <xref:System.IO.Ports?displayProperty=nameWithType> názvů.

#### <a name="category"></a>Kategorie

Visual Basic

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:Microsoft.VisualBasic.Devices?displayProperty=fullName>

<!--

### Affected APIs

- `N:Microsoft.VisualBasic.Devices`

-->
