---
ms.openlocfilehash: 950c69199219cca615e403c6515239de8864d35d
ms.sourcegitcommit: d3c09791297f0edc468a4849a5f11ef62e0e90fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88137476"
---
### <a name="complexity-of-linq-orderbyfirstordefault-increased"></a>Složitost LINQ OrderBy. First {OrDefault} se zvýšila.

Implementace <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> a <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> se změnila a výsledkem je vyšší složitost operace.

#### <a name="change-description"></a>Popis změny

V rozhraní .NET Core 1. x-3. x, volání <xref:System.Linq.Enumerable.OrderBy%2A> nebo <xref:System.Linq.Enumerable.OrderByDescending%2A> následování <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> nebo <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> pracuje se `O(N)` složitou složitostí. Vzhledem k tomu, že je vyžadován pouze první prvek (nebo výchozí), je pro jeho vyhledání vyžadován pouze jeden výčet. Ale predikát, který je zadán do <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> nebo, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> je vyvolán přesně `N` krát, `N` kde je délka sekvence.

V rozhraní .NET 5,0 a novějších verzích [byla provedena změna](https://github.com/dotnet/runtime/pull/36643) tak, aby bylo volání, nebo <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> následováno, <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> nebo <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> funguje se `O(N log N)` složitou složitostí namísto `O(N)` složitosti. Ale predikát, který je zadán do <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> nebo <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> může být vyvolán *méně* než `N` krát, což je důležitější pro celkový výkon.

> [!NOTE]
> Tato změna odpovídá implementaci a složitosti operace v .NET Framework.

#### <a name="reason-for-change"></a>Důvod změny

Výhoda vyvolání predikátu méně času převažuje o nižší celkové složitosti, takže implementace, která byla představena v rozhraní .NET Core 1,0, byla vrácena. Další informace najdete v [tomto problému dotnet/runtime](https://github.com/dotnet/runtime/issues/31554).

#### <a name="version-introduced"></a>Představená verze

5.0

#### <a name="recommended-action"></a>Doporučená akce

V části vývojáře se nevyžaduje žádná akce.

#### <a name="category"></a>Kategorie

Knihovny Core .NET

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->
