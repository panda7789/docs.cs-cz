---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217099"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException – přesunuté do jiného sestavení

<xref:System.ComponentModel.InvalidAsynchronousStateException> Třída byla přesunuta.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core 2,2 a starších verzích <xref:System.ComponentModel.InvalidAsynchronousStateException> se Třída nachází v sestavení *System. ComponentModel. TypeConverter* .

Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ComponentModel. primitivs* .

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna ovlivní pouze aplikace, které používají reflexe <xref:System.ComponentModel.InvalidAsynchronousStateException> k načtení voláním metody <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> , jako je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení. Pokud je to tento případ, sestavení, na které se odkazuje v volání metody, by mělo být aktualizováno tak, aby odráželo nové umístění sestavení typu.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!--

### Affected APIs

- Not detectable via API analysis

-->
