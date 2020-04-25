---
ms.openlocfilehash: d1562cb76f37b6cc2aeb6fe2f7c17c393e169e84
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158467"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException – přesunuté do jiného sestavení

<xref:System.ComponentModel.InvalidAsynchronousStateException> Třída byla přesunuta.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 2,2 a starších verzích se <xref:System.ComponentModel.InvalidAsynchronousStateException> Třída nachází v sestavení *System. ComponentModel. TypeConverter* .

Počínaje rozhraním .NET Core 3,0 se nachází v sestavení *System. ComponentModel. primitivs* .

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna ovlivní pouze aplikace, které používají reflexe <xref:System.ComponentModel.InvalidAsynchronousStateException> k načtení voláním metody, <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> jako je nebo přetížení <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , které předpokládá, že typ je v konkrétním sestavení. V takovém případě aktualizujte sestavení odkazované v volání metody, aby odráželo umístění nového sestavení typu.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné.

<!--

### Affected APIs

- Not detectable via API analysis

-->
