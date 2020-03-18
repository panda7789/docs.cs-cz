---
ms.openlocfilehash: 30580b3fde5b8a99862896bb7d31c6c4024f97e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "74568136"
---
### <a name="floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception"></a>Operace analýzy s plovoucí desetinnou táhou již neselžou nebo nevyvolá vyzvučují výjimku Přetečení

Metody analýzy s plovoucí desetinnou <xref:System.OverflowException> desetinnou tázkou již nevyvolávají nebo vracejí, `false` když analyzují řetězec, jehož číselná hodnota je mimo rozsah typu <xref:System.Single> nebo <xref:System.Double> typu s plovoucí desetinnou tálkou.

#### <a name="change-description"></a>Popis změny

V .NET Core 2.2 a <xref:System.Double.Parse%2A?displayProperty=nameWithType> starší <xref:System.Single.Parse%2A?displayProperty=nameWithType> verze <xref:System.OverflowException> a metody throw pro hodnoty, které mimo rozsah jejich příslušného typu. Metody <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.TryParse%2A?displayProperty=nameWithType> a `false` vrátí pro řetězcové reprezentace číselných hodnot mimo rozsah.

Počínaje rozhraním .NET Core <xref:System.Double.Parse%2A?displayProperty=nameWithType>3.0 již neseselá <xref:System.Double.TryParse%2A?displayProperty=nameWithType> <xref:System.Single.Parse%2A?displayProperty=nameWithType>metoda , a <xref:System.Single.TryParse%2A?displayProperty=nameWithType> metody při analýzě číselných řetězců mimo rozsah. Místo toho <xref:System.Double> metody analýzy <xref:System.Double.PositiveInfinity?displayProperty=nameWithType> vrátí hodnoty, které <xref:System.Double.MaxValue?displayProperty=nameWithType> <xref:System.Double.NegativeInfinity?displayProperty=nameWithType> překračují , a <xref:System.Double.MinValue?displayProperty=nameWithType>vrátí pro hodnoty, které jsou menší než . Podobně <xref:System.Single> metody analýzy vrátí <xref:System.Single.PositiveInfinity?displayProperty=nameWithType> hodnoty, které <xref:System.Single.MaxValue?displayProperty=nameWithType>překračují , <xref:System.Single.NegativeInfinity?displayProperty=nameWithType> a vracejí hodnoty, které jsou menší než <xref:System.Single.MinValue?displayProperty=nameWithType>.

Tato změna byla provedena pro lepší dodržování předpisů IEEE 754:2008.

#### <a name="version-introduced"></a>Zavedená verze

3.0

#### <a name="recommended-action"></a>Doporučená akce

Tato změna může ovlivnit váš kód jedním ze dvou způsobů:

- Váš kód závisí na <xref:System.OverflowException> obslužné rutiny pro spuštění při přetečení dojde. V takovém případě byste `catch` měli příkaz odebrat a `If` umístit potřebný <xref:System.Double.IsInfinity%2A?displayProperty=nameWithType> <xref:System.Single.IsInfinity%2A?displayProperty=nameWithType> kód `true`do příkazu, který testuje, zda je nebo je .

- Váš kód předpokládá, že hodnoty `Infinity`s plovoucí desetinnou čárkou nejsou . V takovém případě byste měli přidat kód potřebný ke `PositiveInfinity` kontrole `NegativeInfinity`hodnot s plovoucí desetinnou čárky a .

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
