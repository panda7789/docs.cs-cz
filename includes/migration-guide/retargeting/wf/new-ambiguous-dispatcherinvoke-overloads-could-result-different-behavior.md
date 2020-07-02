---
ms.openlocfilehash: 80e61d4dd5b8d4754a39e95e37475fefff57fcbd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617170"
---
### <a name="new-ambiguous-dispatcherinvoke-overloads-could-result-in-different-behavior"></a><span data-ttu-id="bf8e4-101">New (dvojznačný) Dispatcher. Invoke přetížení může mít za následek odlišné chování.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-101">New (ambiguous) Dispatcher.Invoke overloads could result in different behavior</span></span>

#### <a name="details"></a><span data-ttu-id="bf8e4-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="bf8e4-102">Details</span></span>

<span data-ttu-id="bf8e4-103">.NET Framework 4,5 přidává nová přetížení <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> , která obsahují parametr typu <xref:System.Action> .</span><span class="sxs-lookup"><span data-stu-id="bf8e4-103">The .NET Framework 4.5 adds new overloads to <xref:System.Windows.Threading.Dispatcher.Invoke%2A?displayProperty=nameWithType> that include a parameter of type <xref:System.Action>.</span></span> <span data-ttu-id="bf8e4-104">Pokud je existující kód znovu zkompilován, kompilátory mohou vyřešit volání metody Dispatcher. Invoke metod, které mají <xref:System.Delegate> parametr jako volání metody Dispatcher. Invoke metod s <xref:System.Action> parametrem.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-104">When existing code is recompiled, compilers may resolve calls to Dispatcher.Invoke methods that have a <xref:System.Delegate> parameter as calls to Dispatcher.Invoke methods with an <xref:System.Action> parameter.</span></span> <span data-ttu-id="bf8e4-105">Pokud volání metody Dispatcher. Invoke přetížení s <xref:System.Delegate> parametrem je přeloženo jako volání metody Dispatcher. Invoke přetížení s <xref:System.Action> parametrem, mohou nastat následující rozdíly v chování:</span><span class="sxs-lookup"><span data-stu-id="bf8e4-105">If a call to a Dispatcher.Invoke overload with a  <xref:System.Delegate> parameter is resolved as a call to a Dispatcher.Invoke overload with an <xref:System.Action> parameter, the following differences in behavior may occur:</span></span>

- <span data-ttu-id="bf8e4-106">Pokud dojde k výjimce, <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> <xref:System.Windows.Threading.Dispatcher.UnhandledException> události a nejsou vyvolány.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-106">If an exception occurs, the <xref:System.Windows.Threading.Dispatcher.UnhandledExceptionFilter> and <xref:System.Windows.Threading.Dispatcher.UnhandledException> events are not raised.</span></span> <span data-ttu-id="bf8e4-107">Místo toho jsou výjimky zpracovávány <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> událostí.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-107">Instead, exceptions are handled by the <xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException?displayProperty=fullName> event.</span></span>
- <span data-ttu-id="bf8e4-108">Volání některých členů, například <xref:System.Windows.Threading.DispatcherOperation.Result> , zablokuje, dokud se operace nedokončí.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-108">Calls to some members, such as <xref:System.Windows.Threading.DispatcherOperation.Result>, block until the operation has completed.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="bf8e4-109">Návrh</span><span class="sxs-lookup"><span data-stu-id="bf8e4-109">Suggestion</span></span>

<span data-ttu-id="bf8e4-110">Aby nedocházelo k nejednoznačnosti (a potenciálním rozdílům v chování zpracování výjimek nebo blokování), kód volajícího metody Dispatcher. Invoke může předat prázdný objekt [] jako druhý parametr volání metody Invoke, aby bylo zajištěno překládání na přetížení metody .NET Framework 4,0.</span><span class="sxs-lookup"><span data-stu-id="bf8e4-110">To avoid ambiguity (and potential differences in exception handling or blocking behaviors), code calling Dispatcher.Invoke can pass an empty object[] as a second parameter to the Invoke call to be sure of resolving to the .NET Framework 4.0 method overload.</span></span>

| <span data-ttu-id="bf8e4-111">Name</span><span class="sxs-lookup"><span data-stu-id="bf8e4-111">Name</span></span>    | <span data-ttu-id="bf8e4-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="bf8e4-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="bf8e4-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="bf8e4-113">Scope</span></span>   | <span data-ttu-id="bf8e4-114">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="bf8e4-114">Minor</span></span>       |
| <span data-ttu-id="bf8e4-115">Verze</span><span class="sxs-lookup"><span data-stu-id="bf8e4-115">Version</span></span> | <span data-ttu-id="bf8e4-116">4.5</span><span class="sxs-lookup"><span data-stu-id="bf8e4-116">4.5</span></span>         |
| <span data-ttu-id="bf8e4-117">Typ</span><span class="sxs-lookup"><span data-stu-id="bf8e4-117">Type</span></span>    | <span data-ttu-id="bf8e4-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="bf8e4-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="bf8e4-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bf8e4-119">Affected APIs</span></span>

- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.TimeSpan,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
- <xref:System.Windows.Threading.Dispatcher.Invoke(System.Delegate,System.Windows.Threading.DispatcherPriority,System.Object[])?displayProperty=nameWithType>
