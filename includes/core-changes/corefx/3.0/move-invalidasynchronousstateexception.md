---
ms.openlocfilehash: 82835915efa0e113e81bb09bd5062ee3252f2a64
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568103"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException – přesunuté do jiného sestavení

Třída <xref:System.ComponentModel.InvalidAsynchronousStateException> byla přesunuta.

#### <a name="change-description"></a>Změnit popis

V rozhraní .NET Core 2,2 a starších verzích se třída <xref:System.ComponentModel.InvalidAsynchronousStateException> nachází v sestavení *System. ComponentModel. TypeConverter* .

Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ComponentModel. primitivs* .

#### <a name="version-introduced"></a>Představená verze

3,0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna ovlivní pouze aplikace, které používají reflexe k načtení <xref:System.ComponentModel.InvalidAsynchronousStateException> voláním metody, jako je například <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType>, která předpokládá, že typ je v konkrétním sestavení. Pokud je to tento případ, sestavení, na které se odkazuje v volání metody, by mělo být aktualizováno tak, aby odráželo nové umístění sestavení typu.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- Žádné

<!--

### Affected APIs

- Not detectable via API analysis

-->
