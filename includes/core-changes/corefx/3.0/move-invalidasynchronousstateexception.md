---
ms.openlocfilehash: ace0a4a60ad4d3f3a13cf4bdb2431e61d04ad8e7
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021555"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException přesunuta do jiného sestavení

Třída <xref:System.ComponentModel.InvalidAsynchronousStateException> byla přesunuta.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 2.2 <xref:System.ComponentModel.InvalidAsynchronousStateException> a starších verzích se třída nachází v sestavě *System.ComponentModel.TypeConverter.*

Počínaje rozhraním .NET Core 3.0 se nachází v sestavě *System.ComponentModel.Primitives.*

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna má vliv pouze na <xref:System.ComponentModel.InvalidAsynchronousStateException> aplikace, které <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> používají reflexe <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> načíst voláním metody, jako je například nebo přetížení, které předpokládá, že typ je v určitém sestavení. Pokud tomu tak je, sestavení sestavení odkazuje ve volání metody by měla být aktualizována tak, aby odrážely nové umístění sestavení typu.

#### <a name="category"></a>Kategorie

Základní knihovny .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné.

<!--

### Affected APIs

- Not detectable via API analysis

-->
