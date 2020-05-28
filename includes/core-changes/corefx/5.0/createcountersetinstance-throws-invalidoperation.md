---
ms.openlocfilehash: fabbc9a51f61a703ce97db50ab251e7a13ffe348
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144475"
---
### <a name="countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists"></a><span data-ttu-id="f1229-101">Sada CounterSet. provedení operace CreateCounterSetInstance nyní vyvolá chybu InvalidOperationException, pokud již instance existuje.</span><span class="sxs-lookup"><span data-stu-id="f1229-101">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exists</span></span>

<span data-ttu-id="f1229-102">Počínaje platformou .NET 5,0 <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> vyvolá výjimku <xref:System.InvalidOperationException> místo, <xref:System.ArgumentException> Pokud sada čítačů již existuje.</span><span class="sxs-lookup"><span data-stu-id="f1229-102">Starting in .NET 5.0, <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)?displayProperty=nameWithType> throws an <xref:System.InvalidOperationException> instead of an <xref:System.ArgumentException> if the counter set already exists.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f1229-103">Popis změny</span><span class="sxs-lookup"><span data-stu-id="f1229-103">Change description</span></span>

<span data-ttu-id="f1229-104">V .NET Framework a .NET Core 1,0 až 3,1 můžete vytvořit instanci sady čítačů voláním <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> .</span><span class="sxs-lookup"><span data-stu-id="f1229-104">In .NET Framework and .NET Core 1.0 to 3.1, you can create an instance of the counter set by calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>.</span></span> <span data-ttu-id="f1229-105">Nicméně pokud sada čítačů již existuje, metoda vyvolá <xref:System.ArgumentException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="f1229-105">However, if the counter set already exists, the method throws an <xref:System.ArgumentException> exception.</span></span>

<span data-ttu-id="f1229-106">V rozhraní .NET 5,0 a novějších verzích, pokud zavoláte <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> a sadu čítačů existují, <xref:System.InvalidOperationException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="f1229-106">In .NET 5.0 and later versions, when you call <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> and the counter set exists, an <xref:System.InvalidOperationException> exception is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f1229-107">Představená verze</span><span class="sxs-lookup"><span data-stu-id="f1229-107">Version introduced</span></span>

<span data-ttu-id="f1229-108">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="f1229-108">5.0 Preview 5</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f1229-109">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="f1229-109">Recommended action</span></span>

<span data-ttu-id="f1229-110">Pokud zachytíte <xref:System.ArgumentException> výjimky v aplikaci při volání <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A> , zvažte také zachycení <xref:System.InvalidOperationException> výjimek.</span><span class="sxs-lookup"><span data-stu-id="f1229-110">If you catch <xref:System.ArgumentException> exceptions in your app when calling <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A>, consider also catching <xref:System.InvalidOperationException> exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="f1229-111">Nedoporučuje <xref:System.ArgumentException> se zachytávání výjimek.</span><span class="sxs-lookup"><span data-stu-id="f1229-111">Catching <xref:System.ArgumentException> exceptions is not recommended.</span></span>

#### <a name="category"></a><span data-ttu-id="f1229-112">Kategorie</span><span class="sxs-lookup"><span data-stu-id="f1229-112">Category</span></span>

<span data-ttu-id="f1229-113">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="f1229-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f1229-114">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="f1229-114">Affected APIs</span></span>

- <xref:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.PerformanceData.CounterSet.CreateCounterSetInstance(System.String)`

-->
