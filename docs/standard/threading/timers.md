---
title: Časovače
description: Zjistěte, jaké časovače rozhraní .NET se mají použít ve vícevláknovém prostředí.
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
ms.openlocfilehash: d7d1fa13b02fe7425fa9b4cb81ba20297a23fe4b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128953"
---
# <a name="timers"></a><span data-ttu-id="63ddf-103">Časovače</span><span class="sxs-lookup"><span data-stu-id="63ddf-103">Timers</span></span>

<span data-ttu-id="63ddf-104">.NET poskytuje dva časovače pro použití v prostředí s více vlákny:</span><span class="sxs-lookup"><span data-stu-id="63ddf-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="63ddf-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, která spouští jednu metodu zpětného volání v <xref:System.Threading.ThreadPool> vlákně v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="63ddf-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="63ddf-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, který ve výchozím nastavení vyvolá událost v <xref:System.Threading.ThreadPool> vlákně v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="63ddf-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="63ddf-107">Některé implementace rozhraní .NET můžou zahrnovat další časovače:</span><span class="sxs-lookup"><span data-stu-id="63ddf-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="63ddf-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: model Windows Forms komponenta, která aktivuje událost v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="63ddf-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="63ddf-109">Komponenta nemá žádné uživatelské rozhraní a je určena pro použití v prostředí s jedním vláknem.</span><span class="sxs-lookup"><span data-stu-id="63ddf-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="63ddf-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: komponenta ASP.NET, která provádí asynchronní nebo synchronní zpětné volání webové stránky v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="63ddf-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="63ddf-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: časovač, který je integrovaný do fronty <xref:System.Windows.Threading.Dispatcher>, která se zpracovává v zadaném časovém intervalu a v zadané prioritě.</span><span class="sxs-lookup"><span data-stu-id="63ddf-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="63ddf-112">Třída System. Threading. Timer</span><span class="sxs-lookup"><span data-stu-id="63ddf-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="63ddf-113">Třída <xref:System.Threading.Timer?displayProperty=nameWithType> umožňuje nepřetržitě volat delegáta v zadaných časových intervalech.</span><span class="sxs-lookup"><span data-stu-id="63ddf-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="63ddf-114">Tuto třídu můžete použít také k naplánování jednoho volání delegáta v zadaném časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="63ddf-114">You also can use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="63ddf-115">Delegát je spuštěn ve vlákně <xref:System.Threading.ThreadPool>.</span><span class="sxs-lookup"><span data-stu-id="63ddf-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="63ddf-116">Při vytváření objektu <xref:System.Threading.Timer?displayProperty=nameWithType> zadáte delegáta <xref:System.Threading.TimerCallback>, který definuje metodu zpětného volání, objekt volitelného stavu, který je předán zpětnému volání, čas zpoždění před prvním voláním zpětného volání a časový interval mezi vyvolání zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="63ddf-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="63ddf-117">Chcete-li zrušit probíhající časovač, zavolejte metodu <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="63ddf-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="63ddf-118">Následující příklad vytvoří časovač, který volá poskytnutého delegáta poprvé po jedné sekundě (1000 milisekund) a pak je zavolá každé dvě sekundy.</span><span class="sxs-lookup"><span data-stu-id="63ddf-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="63ddf-119">Objekt State v příkladu slouží ke zjištění, kolikrát je volán delegát.</span><span class="sxs-lookup"><span data-stu-id="63ddf-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="63ddf-120">Časovač se zastaví, pokud byl delegát volán nejméně desetkrát.</span><span class="sxs-lookup"><span data-stu-id="63ddf-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="63ddf-121">Další informace a příklady naleznete v tématu <xref:System.Threading.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="63ddf-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="63ddf-122">Třída System. Timers. Timer</span><span class="sxs-lookup"><span data-stu-id="63ddf-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="63ddf-123">Další časovač, který lze použít v prostředí s více vlákny, je <xref:System.Timers.Timer?displayProperty=nameWithType>, že ve výchozím nastavení vyvolá událost ve <xref:System.Threading.ThreadPool> vlákně.</span><span class="sxs-lookup"><span data-stu-id="63ddf-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="63ddf-124">Při vytváření objektu <xref:System.Timers.Timer?displayProperty=nameWithType> můžete zadat časový interval, ve kterém se má vyvolat událost <xref:System.Timers.Timer.Elapsed>.</span><span class="sxs-lookup"><span data-stu-id="63ddf-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="63ddf-125">Vlastnost <xref:System.Timers.Timer.Enabled%2A> použijte k označení, zda má časovač vyvolat událost <xref:System.Timers.Timer.Elapsed>.</span><span class="sxs-lookup"><span data-stu-id="63ddf-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="63ddf-126">Pokud potřebujete událost <xref:System.Timers.Timer.Elapsed> vyvolat pouze jednou po uplynutí zadaného intervalu, nastavte <xref:System.Timers.Timer.AutoReset%2A> na `false`.</span><span class="sxs-lookup"><span data-stu-id="63ddf-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="63ddf-127">Výchozí hodnota vlastnosti <xref:System.Timers.Timer.AutoReset%2A> je `true`, což znamená, že se událost <xref:System.Timers.Timer.Elapsed> generuje pravidelně v intervalu definovaném vlastností <xref:System.Timers.Timer.Interval%2A>.</span><span class="sxs-lookup"><span data-stu-id="63ddf-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="63ddf-128">Další informace a příklady naleznete v tématu <xref:System.Timers.Timer?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="63ddf-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="63ddf-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63ddf-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="63ddf-130">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="63ddf-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
