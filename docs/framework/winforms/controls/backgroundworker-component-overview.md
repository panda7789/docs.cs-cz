---
title: BackgroundWorker – přehled komponenty
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- BackgroundWorker
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 64e9b3ab-7443-4a77-ab17-b8b8c0cb3f62
ms.openlocfilehash: 2ef09fdc755480205b9929037277162349afa135
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423817"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="560f3-102">BackgroundWorker – přehled komponenty</span><span class="sxs-lookup"><span data-stu-id="560f3-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="560f3-103">Existuje mnoho běžně provádí operace, které může trvat dlouhou dobu spuštění.</span><span class="sxs-lookup"><span data-stu-id="560f3-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="560f3-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="560f3-104">For example:</span></span>  
  
- <span data-ttu-id="560f3-105">Soubory ke stažení bitové kopie</span><span class="sxs-lookup"><span data-stu-id="560f3-105">Image downloads</span></span>  
  
- <span data-ttu-id="560f3-106">Volání webové služby</span><span class="sxs-lookup"><span data-stu-id="560f3-106">Web service invocations</span></span>  
  
- <span data-ttu-id="560f3-107">Soubor se stáhne a nahraje (včetně aplikace peer-to-peer)</span><span class="sxs-lookup"><span data-stu-id="560f3-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
- <span data-ttu-id="560f3-108">Komplexní místní výpočty</span><span class="sxs-lookup"><span data-stu-id="560f3-108">Complex local computations</span></span>  
  
- <span data-ttu-id="560f3-109">Databázové transakce</span><span class="sxs-lookup"><span data-stu-id="560f3-109">Database transactions</span></span>  
  
- <span data-ttu-id="560f3-110">Místní disk, jeho pomalé vzhledem k přístupu do paměti udělený přístup</span><span class="sxs-lookup"><span data-stu-id="560f3-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="560f3-111">Operace, jako je to může způsobit uživatelského rozhraní pro blokování při spuštění.</span><span class="sxs-lookup"><span data-stu-id="560f3-111">Operations like these can cause your user interface to block while they are running.</span></span> <span data-ttu-id="560f3-112">Pokud chcete, aby responzivní uživatelské rozhraní a se potýkají s dlouhým zpožděním spojené s takovými operacemi <xref:System.ComponentModel.BackgroundWorker> součást poskytuje pohodlné řešení.</span><span class="sxs-lookup"><span data-stu-id="560f3-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="560f3-113"><xref:System.ComponentModel.BackgroundWorker> Komponenty vám dává možnost provádět časově náročná operace asynchronně ("na pozadí"), ve vlákně, která se liší od hlavního vlákna uživatelského rozhraní vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="560f3-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="560f3-114">Použití <xref:System.ComponentModel.BackgroundWorker>, vám stačí určit, jakou metodu časově náročné pracovní provádět na pozadí, a poté zavoláte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="560f3-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="560f3-115">Volající vlákno dál běží normálně při metodě pracovního podprocesu běží asynchronně.</span><span class="sxs-lookup"><span data-stu-id="560f3-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="560f3-116">Po dokončení metody <xref:System.ComponentModel.BackgroundWorker> výstrahy volající vlákno s jeho spuštění <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí, který volitelně obsahuje výsledky operace.</span><span class="sxs-lookup"><span data-stu-id="560f3-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="560f3-117"><xref:System.ComponentModel.BackgroundWorker> Komponenta je k dispozici **nástrojů**v **součásti** kartu. Chcete-li přidat <xref:System.ComponentModel.BackgroundWorker> do formuláře, přetáhněte <xref:System.ComponentModel.BackgroundWorker> komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="560f3-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="560f3-118">Zobrazí se v panelu komponent a jeho vlastnosti se zobrazí v **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="560f3-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="560f3-119">Chcete-li začít asynchronní operace, použijte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="560f3-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="560f3-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> přijímá volitelný `object` parametr, který slouží k předání argumentů metodě pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="560f3-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="560f3-121"><xref:System.ComponentModel.BackgroundWorker> Třídy zpřístupňuje <xref:System.ComponentModel.BackgroundWorker.DoWork> události, ke kterému je připojený pracovní podproces prostřednictvím <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="560f3-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="560f3-122"><xref:System.ComponentModel.BackgroundWorker.DoWork> Obslužná rutina události <xref:System.ComponentModel.DoWorkEventArgs> parametr, který má <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="560f3-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="560f3-123">Tato vlastnost přijímá parametr z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a mohou být předány do metody pracovního procesu, která bude volána v <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="560f3-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="560f3-124">Následující příklad ukazuje, jak přiřadit výsledek z pracovního procesu metodu nazvanou `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="560f3-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="560f3-125">Je součástí většího příkladu, které můžete vyhledat v [jak: Implementace formuláře, který používá operaci na pozadí](how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="560f3-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="560f3-126">Další informace o používání obslužných rutin událostí, naleznete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="560f3-126">For more information on using event handlers, see [Events](../../../standard/events/index.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="560f3-127">Pokud používáte multithreading jakéhokoli druhu, potenciálně zpřístupníte sami velmi závažných a složitých chyb.</span><span class="sxs-lookup"><span data-stu-id="560f3-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="560f3-128">Poraďte [spravovaných vláken osvědčené postupy](../../../standard/threading/managed-threading-best-practices.md) před implementací jakéhokoli řešení, které používá multithreading.</span><span class="sxs-lookup"><span data-stu-id="560f3-128">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="560f3-129">Další informace o používání <xref:System.ComponentModel.BackgroundWorker> najdete v tématu [jak: Spuštění operace na pozadí](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="560f3-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="560f3-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="560f3-130">See also</span></span>

- [<span data-ttu-id="560f3-131">Dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="560f3-131">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="560f3-132">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="560f3-132">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="560f3-133">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="560f3-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
