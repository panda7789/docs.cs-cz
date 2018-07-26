---
title: Časovače
description: Zjistěte, jaké časovače .NET pro použití v prostředí s více vlákny.
ms.date: 07/03/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], timers
- timers, about timers
ms.assetid: 7091500d-be18-499b-a942-95366ce185e5
author: pkulikov
ms.author: ronpet
ms.openlocfilehash: ae41c535d8bc1c0a05174b9051ba34f1a0a34638
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37875063"
---
# <a name="timers"></a><span data-ttu-id="89fd0-103">Časovače</span><span class="sxs-lookup"><span data-stu-id="89fd0-103">Timers</span></span>

<span data-ttu-id="89fd0-104">.NET poskytuje dvě časovače pro použití v prostředí s více vlákny:</span><span class="sxs-lookup"><span data-stu-id="89fd0-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="89fd0-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, která spustí metodu zpětného volání jednoho na <xref:System.Threading.ThreadPool> vlákna v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="89fd0-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="89fd0-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, který ve výchozím nastavení vyvolá událost, na <xref:System.Threading.ThreadPool> vlákna v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="89fd0-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="89fd0-107">Některé implementace .NET mohou zahrnovat další časovače:</span><span class="sxs-lookup"><span data-stu-id="89fd0-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="89fd0-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: komponenty Windows Forms, který se aktivuje událost v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="89fd0-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="89fd0-109">Komponenta nemá žádné uživatelské rozhraní a je určená pro použití v prostředí s jedním vláknem.</span><span class="sxs-lookup"><span data-stu-id="89fd0-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="89fd0-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: komponentu ASP.NET, která provede zpětné volání synchronní nebo asynchronní webové stránky v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="89fd0-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="89fd0-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: časovač, který je integrován do <xref:System.Windows.Threading.Dispatcher> fronty, která je zpracována v zadaném intervalu, času a na zadanou prioritou.</span><span class="sxs-lookup"><span data-stu-id="89fd0-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="89fd0-112">Třída System.Threading.Timer</span><span class="sxs-lookup"><span data-stu-id="89fd0-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="89fd0-113"><xref:System.Threading.Timer?displayProperty=nameWithType> Třída umožňuje nepřetržitě volání delegáta v zadaných časových intervalech.</span><span class="sxs-lookup"><span data-stu-id="89fd0-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="89fd0-114">Tato třída také můžete použít k naplánování jedním voláním metody delegáta v zadaném časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="89fd0-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="89fd0-115">Delegát se spouští podle <xref:System.Threading.ThreadPool> vlákna.</span><span class="sxs-lookup"><span data-stu-id="89fd0-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="89fd0-116">Při vytváření <xref:System.Threading.Timer?displayProperty=nameWithType> objektu, zadáte <xref:System.Threading.TimerCallback> delegáta, který definuje metodu zpětného volání, volitelné stavu objektu, který je předán do zpětného volání, dobu zpoždění před prvním vyvoláním služby zpětného volání a časový interval mezi vyvoláními zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="89fd0-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="89fd0-117">Chcete-li zrušit čekajícího časovače, zavolejte <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="89fd0-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="89fd0-118">Následující příklad vytvoří časovač, který volá uvedený delegát poprvé po jedné sekundě (1000 milisekund) a nazve je každé dvě sekundy.</span><span class="sxs-lookup"><span data-stu-id="89fd0-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="89fd0-119">Stav objektu v příkladu se používá ke zjištění počtu volání delegáta se nazývá.</span><span class="sxs-lookup"><span data-stu-id="89fd0-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="89fd0-120">Časovač je zastaven, když je delegát byla volána alespoň 10krát.</span><span class="sxs-lookup"><span data-stu-id="89fd0-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="89fd0-121">Další informace a příklady najdete v tématu <xref:System.Threading.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89fd0-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="89fd0-122">Třída System.Timers.Timer</span><span class="sxs-lookup"><span data-stu-id="89fd0-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="89fd0-123">Další časovač, který lze použít v prostředí s více vlákny je <xref:System.Timers.Timer?displayProperty=nameWithType> ve výchozím nastavení vyvolá událost, na <xref:System.Threading.ThreadPool> vlákna.</span><span class="sxs-lookup"><span data-stu-id="89fd0-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="89fd0-124">Když vytvoříte <xref:System.Timers.Timer?displayProperty=nameWithType> objektu, můžete zadat časový interval, ve který se má použít <xref:System.Timers.Timer.Elapsed> událostí.</span><span class="sxs-lookup"><span data-stu-id="89fd0-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="89fd0-125">Použití <xref:System.Timers.Timer.Enabled%2A> vlastnost umožňující označit, pokud by měla vyvolat časovač <xref:System.Timers.Timer.Elapsed> událostí.</span><span class="sxs-lookup"><span data-stu-id="89fd0-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="89fd0-126">Pokud potřebujete <xref:System.Timers.Timer.Elapsed> událost vyvolána pouze jednou po uplynutí zadaného intervalu, nastavte <xref:System.Timers.Timer.AutoReset%2A> k `false`.</span><span class="sxs-lookup"><span data-stu-id="89fd0-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="89fd0-127">Výchozí hodnota <xref:System.Timers.Timer.AutoReset%2A> vlastnost je `true`, to znamená, že <xref:System.Timers.Timer.Elapsed> událost se vyvolá, pravidelně v intervalu určeném v <xref:System.Timers.Timer.Interval%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="89fd0-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="89fd0-128">Další informace a příklady najdete v tématu <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="89fd0-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="89fd0-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89fd0-129">See also</span></span>

 <xref:System.Threading.Timer?displayProperty=nameWithType>  
 <xref:System.Timers.Timer?displayProperty=nameWithType>  
 [<span data-ttu-id="89fd0-130">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="89fd0-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
