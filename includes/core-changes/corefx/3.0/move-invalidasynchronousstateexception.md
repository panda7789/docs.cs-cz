---
ms.openlocfilehash: 19359422f79f8240676b0057c7391f6b06f961ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147546"
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

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné.

<!--

### Affected APIs

- Not detectable via API analysis

-->
