---
ms.openlocfilehash: 192873aa5069aa4f96a18716afb066c80b223e29
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002437"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Operace analýzy s plovoucí desetinnou čárkou již nejsou úspěšné nebo vyvolávají výjimku OverflowException

Metody analýzy s plovoucí desetinnou čárkou již nevyvolávají <xref:System.OverflowException> nebo vracet `false` při analýze řetězce, jehož číselná hodnota je mimo rozsah typu s plovoucí desetinnou čárkou <xref:System.Single> nebo <xref:System.Double>.

#### <a name="change-description"></a>Změnit popis

V .NET Core 2,2 a starších verzích metody <xref:System.Double.Parse%2A?displayProperty=nameWithType> a <xref:System.Single.Parse%2A?displayProperty=nameWithType> vyvolávají <xref:System.OverflowException> pro hodnoty, které jsou mimo rozsah jejich odpovídajícího typu. Metody <xref:System.Double.TryParse%2A?displayProperty=nameWithType> a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> vrátí `false` pro řetězcové reprezentace číselných hodnot mimo rozsah.

Počínaje rozhraním .NET Core 3,0 se metody <xref:System.Double.Parse%2A?displayProperty=nameWithType>, <xref:System.Double.TryParse%2A?displayProperty=nameWithType>, <xref:System.Single.Parse%2A?displayProperty=nameWithType> a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> při analýze číselných řetězců mimo rozsah nezdařily. Místo toho metody analýzy <xref:System.Double> vrátí <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> pro hodnoty větší než <xref:System.Double.MaxValue?displayProperty=nameWithType> a vrátí <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> pro hodnoty, které jsou menší než <xref:System.Double.MinValue?displayProperty=nameWithType>. Podobně metody analýzy <xref:System.Single> vrátí <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> pro hodnoty, které překračují <xref:System.Single.MaxValue?displayProperty=nameWithType>, a vrátí <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> pro hodnoty, které jsou menší než <xref:System.Single.MinValue?displayProperty=nameWithType>.

Tato změna byla provedena pro zlepšení dodržování standardů IEEE 754:2008. 

#### <a name="version-introduced"></a>Představená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna může mít vliv na váš kód některým ze dvou způsobů:

- Váš kód závisí na obslužné rutině <xref:System.OverflowException>, která se má provést, když dojde k přetečení. V takovém případě byste měli odebrat příkaz `catch` a umístit do příkazu `If` potřebný kód, který testuje, jestli je `true` <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> nebo <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType>.

- Váš kód předpokládá, že hodnoty s plovoucí desetinnou čárkou nejsou `Infinity`. V takovém případě byste měli přidat potřebný kód pro kontrolu hodnot s plovoucí desetinnou čárkou `PositiveInfinity` a `NegativeInfinity`.

#### <a name="category"></a>Kategorie

CoreFx

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Double.Parse%2A?displayProperty=nameWithType>
- <xref:System.Double.TryParse%2A?displayProperty=nameWithType>
- <xref:System.Single.Parse%2A?displayProperty=nameWithType>
- <xref:System.Single.TryParse%2A?displayProperty=nameWithType>

<!--

### Affected APIs

- `Overload:System.Double.Parse`
- `Overload:System.Double.TryParse`
- `Overload:System.Single.Parse`
- `Overload:System.Single.TryParse`

-->
