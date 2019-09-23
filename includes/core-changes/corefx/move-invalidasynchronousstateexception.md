---
ms.openlocfilehash: 4b41e5fcb6da638457ca8029a635f391b6a7b8ec
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182010"
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