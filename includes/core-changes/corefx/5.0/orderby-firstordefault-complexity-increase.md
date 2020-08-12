---
ms.openlocfilehash: 950c69199219cca615e403c6515239de8864d35d
ms.sourcegitcommit: d3c09791297f0edc468a4849a5f11ef62e0e90fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2020
ms.locfileid: "88137476"
---
### <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="8c46d-101">Složitost LINQ OrderBy. First {OrDefault} se zvýšila.</span><span class="sxs-lookup"><span data-stu-id="8c46d-101">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="8c46d-102">Implementace <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> a <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> se změnila a výsledkem je vyšší složitost operace.</span><span class="sxs-lookup"><span data-stu-id="8c46d-102">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8c46d-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="8c46d-103">Change description</span></span>

<span data-ttu-id="8c46d-104">V rozhraní .NET Core 1. x-3. x, volání <xref:System.Linq.Enumerable.OrderBy%2A> nebo <xref:System.Linq.Enumerable.OrderByDescending%2A> následování <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> nebo <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> pracuje se `O(N)` složitou složitostí.</span><span class="sxs-lookup"><span data-stu-id="8c46d-104">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="8c46d-105">Vzhledem k tomu, že je vyžadován pouze první prvek (nebo výchozí), je pro jeho vyhledání vyžadován pouze jeden výčet.</span><span class="sxs-lookup"><span data-stu-id="8c46d-105">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="8c46d-106">Ale predikát, který je zadán do <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> nebo, <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> je vyvolán přesně `N` krát, `N` kde je délka sekvence.</span><span class="sxs-lookup"><span data-stu-id="8c46d-106">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="8c46d-107">V rozhraní .NET 5,0 a novějších verzích [byla provedena změna](https://github.com/dotnet/runtime/pull/36643) tak, aby bylo volání, nebo <xref:System.Linq.Enumerable.OrderBy%2A> <xref:System.Linq.Enumerable.OrderByDescending%2A> následováno, <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> nebo <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> funguje se `O(N log N)` složitou složitostí namísto `O(N)` složitosti.</span><span class="sxs-lookup"><span data-stu-id="8c46d-107">In .NET 5.0 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="8c46d-108">Ale predikát, který je zadán do <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> nebo <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> může být vyvolán *méně* než `N` krát, což je důležitější pro celkový výkon.</span><span class="sxs-lookup"><span data-stu-id="8c46d-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="8c46d-109">Tato změna odpovídá implementaci a složitosti operace v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8c46d-109">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8c46d-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="8c46d-110">Reason for change</span></span>

<span data-ttu-id="8c46d-111">Výhoda vyvolání predikátu méně času převažuje o nižší celkové složitosti, takže implementace, která byla představena v rozhraní .NET Core 1,0, byla vrácena.</span><span class="sxs-lookup"><span data-stu-id="8c46d-111">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="8c46d-112">Další informace najdete v [tomto problému dotnet/runtime](https://github.com/dotnet/runtime/issues/31554).</span><span class="sxs-lookup"><span data-stu-id="8c46d-112">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8c46d-113">Představená verze</span><span class="sxs-lookup"><span data-stu-id="8c46d-113">Version introduced</span></span>

<span data-ttu-id="8c46d-114">5.0</span><span class="sxs-lookup"><span data-stu-id="8c46d-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8c46d-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="8c46d-115">Recommended action</span></span>

<span data-ttu-id="8c46d-116">V části vývojáře se nevyžaduje žádná akce.</span><span class="sxs-lookup"><span data-stu-id="8c46d-116">No action is required on the developer's part.</span></span>

#### <a name="category"></a><span data-ttu-id="8c46d-117">Kategorie</span><span class="sxs-lookup"><span data-stu-id="8c46d-117">Category</span></span>

<span data-ttu-id="8c46d-118">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="8c46d-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8c46d-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8c46d-119">Affected APIs</span></span>

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
