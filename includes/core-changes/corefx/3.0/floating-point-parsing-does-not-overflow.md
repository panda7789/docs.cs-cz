---
ms.openlocfilehash: 935d9b2368ea4a0eeca7943dcbd584d24d2a6633
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721108"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException

Metody analýzy s plovoucí desetinnou čárkou již nejsou <xref:System.OverflowException> `false` při analýze řetězce, jehož číselná hodnota je mimo rozsah <xref:System.Single> nebo typ s plovoucí desetinnou čárkou, vyhozeny nebo vraceny <xref:System.Double> .

#### <a name="change-description"></a>Popis změny

V .NET Core 2,2 a starších verzích <xref:System.Double.Parse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> metody a vyvolávají výjimku <xref:System.OverflowException> pro hodnoty, které jsou mimo rozsah jejich příslušného typu. <xref:System.Double.TryParse%2A?displayProperty=nameWithType>Metody a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> vrátí `false` pro řetězcové reprezentace číselných hodnot mimo rozsah.

Počínaje rozhraním .NET Core 3,0, <xref:System.Double.Parse%2A?displayProperty=nameWithType> metody,, a se <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> již nedaří při analýze číselných řetězců mimo rozsah. Místo toho <xref:System.Double> metody analýzy vrátí <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> pro hodnoty, které překračují <xref:System.Double.MaxValue?displayProperty=nameWithType> , a vrátí <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> hodnotu, která je menší než <xref:System.Double.MinValue?displayProperty=nameWithType> . Podobně <xref:System.Single> metody analýzy vrátí <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> pro hodnoty, které překračují <xref:System.Single.MaxValue?displayProperty=nameWithType> , a vrátí <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> pro hodnoty, které jsou menší než <xref:System.Single.MinValue?displayProperty=nameWithType> .

Tato změna byla provedena pro zlepšení dodržování standardů IEEE 754:2008.

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna může mít vliv na váš kód některým ze dvou způsobů:

- Váš kód závisí na obslužné rutině, <xref:System.OverflowException> která se má provést, když dojde k přetečení. V takovém případě byste měli příkaz odebrat `catch` a umístit jakýkoli potřebný kód do `If` příkazu, který testuje, zda <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> nebo <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> je `true` .

- Váš kód předpokládá, že hodnoty s plovoucí desetinnou čárkou nejsou `Infinity` . V takovém případě byste měli přidat potřebný kód pro kontrolu hodnot s plovoucí desetinnou čárkou `PositiveInfinity` a `NegativeInfinity` .

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
