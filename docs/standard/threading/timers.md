---
title: Časovače
description: Zjistěte, co se mají používat časovače rozhraní .NET v prostředí s více vlákny.
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
ms.openlocfilehash: d463eb2a8d598dc5ba9b2fb51a6fc08c563e6fe4
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739486"
---
# <a name="timers"></a><span data-ttu-id="73060-103">Časovače</span><span class="sxs-lookup"><span data-stu-id="73060-103">Timers</span></span>

<span data-ttu-id="73060-104">Rozhraní .NET poskytuje dva časovače pro použití v prostředí s více vlákny:</span><span class="sxs-lookup"><span data-stu-id="73060-104">.NET provides two timers to use in a multithreaded environment:</span></span>

- <span data-ttu-id="73060-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, který v pravidelných intervalech <xref:System.Threading.ThreadPool> provede jednu metodu zpětného volání ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="73060-105"><xref:System.Threading.Timer?displayProperty=nameWithType>, which executes a single callback method on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>
- <span data-ttu-id="73060-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, který ve výchozím nastavení <xref:System.Threading.ThreadPool> vyvolá událost ve vlákně v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="73060-106"><xref:System.Timers.Timer?displayProperty=nameWithType>, which by default raises an event on a <xref:System.Threading.ThreadPool> thread at regular intervals.</span></span>

> [!NOTE]
> <span data-ttu-id="73060-107">Některé implementace rozhraní .NET mohou obsahovat další časovače:</span><span class="sxs-lookup"><span data-stu-id="73060-107">Some .NET implementations may include additional timers:</span></span>
>
> - <span data-ttu-id="73060-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: součást Windows Forms, která v pravidelných intervalech aktivuje událost.</span><span class="sxs-lookup"><span data-stu-id="73060-108"><xref:System.Windows.Forms.Timer?displayProperty=nameWithType>: a Windows Forms component that fires an event at regular intervals.</span></span> <span data-ttu-id="73060-109">Komponenta nemá žádné uživatelské rozhraní a je určena pro použití v prostředí s jedním podprocesem.</span><span class="sxs-lookup"><span data-stu-id="73060-109">The component has no user interface and is designed for use in a single-threaded environment.</span></span>  
> - <span data-ttu-id="73060-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: součást ASP.NET, která v pravidelných intervalech provádí asynchronní nebo synchronní postbacky webových stránek.</span><span class="sxs-lookup"><span data-stu-id="73060-110"><xref:System.Web.UI.Timer?displayProperty=nameWithType>: an ASP.NET component that performs asynchronous or synchronous web page postbacks at a regular interval.</span></span>
> - <span data-ttu-id="73060-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: časovač, který je <xref:System.Windows.Threading.Dispatcher> integrován do fronty, který je zpracován v určeném časovém intervalu a se zadanou prioritou.</span><span class="sxs-lookup"><span data-stu-id="73060-111"><xref:System.Windows.Threading.DispatcherTimer?displayProperty=nameWithType>: a timer that is integrated into the <xref:System.Windows.Threading.Dispatcher> queue which is processed at a specified interval of time and at a specified priority.</span></span>

## <a name="the-systemthreadingtimer-class"></a><span data-ttu-id="73060-112">Třída System.Threading.Timer</span><span class="sxs-lookup"><span data-stu-id="73060-112">The System.Threading.Timer class</span></span>

<span data-ttu-id="73060-113">Třída <xref:System.Threading.Timer?displayProperty=nameWithType> umožňuje průběžně volat delegáta v určených časových intervalech.</span><span class="sxs-lookup"><span data-stu-id="73060-113">The <xref:System.Threading.Timer?displayProperty=nameWithType> class enables you to continuously call a delegate at specified time intervals.</span></span> <span data-ttu-id="73060-114">Tuto třídu můžete také použít k naplánování jednoho volání delegátovi v zadaném časovém intervalu.</span><span class="sxs-lookup"><span data-stu-id="73060-114">You can also use this class to schedule a single call to a delegate in a specified time interval.</span></span> <span data-ttu-id="73060-115">Delegát je spuštěn ve <xref:System.Threading.ThreadPool> vlákně.</span><span class="sxs-lookup"><span data-stu-id="73060-115">The delegate is executed on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="73060-116">Při vytváření <xref:System.Threading.Timer?displayProperty=nameWithType> objektu určíte <xref:System.Threading.TimerCallback> delegáta, který definuje metodu zpětného volání, volitelný objekt stavu, který je předán zpětnému volání, dobu zpoždění před prvním vyvoláním zpětného volání a časový interval mezi vyvoláním zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="73060-116">When you create a <xref:System.Threading.Timer?displayProperty=nameWithType> object, you specify a <xref:System.Threading.TimerCallback> delegate that defines the callback method, an optional state object that is passed to the callback, the amount of time to delay before the first invocation of the callback, and the time interval between callback invocations.</span></span> <span data-ttu-id="73060-117">Chcete-li zrušit čekající <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> časovač, zavolejte metodu.</span><span class="sxs-lookup"><span data-stu-id="73060-117">To cancel a pending timer, call the <xref:System.Threading.Timer.Dispose%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="73060-118">Následující příklad vytvoří časovač, který volá zadaný delegát poprvé po jedné sekundě (1000 milisekund) a pak jej volá každé dvě sekundy.</span><span class="sxs-lookup"><span data-stu-id="73060-118">The following example creates a timer that calls the provided delegate for the first time after one second (1000 milliseconds) and then calls it every two seconds.</span></span> <span data-ttu-id="73060-119">Objekt stavu v příkladu se používá ke spočítání, kolikrát je volána delegáta.</span><span class="sxs-lookup"><span data-stu-id="73060-119">The state object in the example is used to count how many times the delegate is called.</span></span> <span data-ttu-id="73060-120">Časovač je zastaven, pokud delegát byl volán alespoň 10 krát.</span><span class="sxs-lookup"><span data-stu-id="73060-120">The timer is stopped when the delegate has been called at least 10 times.</span></span>

[!code-cpp[System.Threading.Timer#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.Timer/CPP/source2.cpp#2)]
[!code-csharp[System.Threading.Timer#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.Timer/CS/source2.cs#2)]
[!code-vb[System.Threading.Timer#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.Timer/VB/source2.vb#2)]

<span data-ttu-id="73060-121">Další informace a příklady <xref:System.Threading.Timer?displayProperty=nameWithType>naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="73060-121">For more information and examples, see <xref:System.Threading.Timer?displayProperty=nameWithType>.</span></span>

## <a name="the-systemtimerstimer-class"></a><span data-ttu-id="73060-122">Třída System.Timers.Timer</span><span class="sxs-lookup"><span data-stu-id="73060-122">The System.Timers.Timer class</span></span>

<span data-ttu-id="73060-123">Další časovač, který lze použít v <xref:System.Timers.Timer?displayProperty=nameWithType> prostředí s více vlákny <xref:System.Threading.ThreadPool> je, že ve výchozím nastavení vyvolá událost ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="73060-123">Another timer that can be used in a multithreaded environment is <xref:System.Timers.Timer?displayProperty=nameWithType> that by default raises an event on a <xref:System.Threading.ThreadPool> thread.</span></span>

<span data-ttu-id="73060-124">Při vytváření <xref:System.Timers.Timer?displayProperty=nameWithType> objektu můžete určit časový interval, ve <xref:System.Timers.Timer.Elapsed> kterém chcete vyvolat událost.</span><span class="sxs-lookup"><span data-stu-id="73060-124">When you create a <xref:System.Timers.Timer?displayProperty=nameWithType> object, you may specify the time interval in which to raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="73060-125">Pomocí <xref:System.Timers.Timer.Enabled%2A> vlastnosti označte, zda <xref:System.Timers.Timer.Elapsed> časovač má vyvolat událost.</span><span class="sxs-lookup"><span data-stu-id="73060-125">Use the <xref:System.Timers.Timer.Enabled%2A> property to indicate if a timer should raise an <xref:System.Timers.Timer.Elapsed> event.</span></span> <span data-ttu-id="73060-126">Pokud potřebujete <xref:System.Timers.Timer.Elapsed> událost, která má být vyvolána pouze jednou po <xref:System.Timers.Timer.AutoReset%2A> `false`uplynutí zadaného intervalu, nastavte na .</span><span class="sxs-lookup"><span data-stu-id="73060-126">If you need an <xref:System.Timers.Timer.Elapsed> event to be raised only once after the specified interval has elapsed, set the <xref:System.Timers.Timer.AutoReset%2A> to `false`.</span></span> <span data-ttu-id="73060-127">Výchozí <xref:System.Timers.Timer.AutoReset%2A> hodnota vlastnosti `true`je , což <xref:System.Timers.Timer.Elapsed> znamená, že událost je <xref:System.Timers.Timer.Interval%2A> vyvolána pravidelně v intervalu definovaném vlastností.</span><span class="sxs-lookup"><span data-stu-id="73060-127">The default value of the <xref:System.Timers.Timer.AutoReset%2A> property is `true`, which means that an <xref:System.Timers.Timer.Elapsed> event is raised regularly at the interval defined by the <xref:System.Timers.Timer.Interval%2A> property.</span></span>

<span data-ttu-id="73060-128">Další informace a příklady <xref:System.Timers.Timer?displayProperty=nameWithType>naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="73060-128">For more information and examples, see <xref:System.Timers.Timer?displayProperty=nameWithType>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="73060-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="73060-129">See also</span></span>

- <xref:System.Threading.Timer?displayProperty=nameWithType>
- <xref:System.Timers.Timer?displayProperty=nameWithType>
- [<span data-ttu-id="73060-130">Objekty a prvky zřetězení</span><span class="sxs-lookup"><span data-stu-id="73060-130">Threading Objects and Features</span></span>](threading-objects-and-features.md)
