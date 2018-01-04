---
title: "BackgroundWorker – přehled komponenty"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
f1_keywords: BackgroundWorker
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2e49c9c3a8f2b133337ee3c153841a7daeff178
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="25f12-102">BackgroundWorker – přehled komponenty</span><span class="sxs-lookup"><span data-stu-id="25f12-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="25f12-103">Existuje mnoho běžně provádět operace, které může trvat dlouhou dobu spuštění.</span><span class="sxs-lookup"><span data-stu-id="25f12-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="25f12-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="25f12-104">For example:</span></span>  
  
-   <span data-ttu-id="25f12-105">Soubory ke stažení bitové kopie</span><span class="sxs-lookup"><span data-stu-id="25f12-105">Image downloads</span></span>  
  
-   <span data-ttu-id="25f12-106">Volání webové služby</span><span class="sxs-lookup"><span data-stu-id="25f12-106">Web service invocations</span></span>  
  
-   <span data-ttu-id="25f12-107">Soubor se stáhne a odešle (včetně pro aplikace peer-to-peer)</span><span class="sxs-lookup"><span data-stu-id="25f12-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
-   <span data-ttu-id="25f12-108">Komplexní místní výpočty</span><span class="sxs-lookup"><span data-stu-id="25f12-108">Complex local computations</span></span>  
  
-   <span data-ttu-id="25f12-109">Databázové transakce</span><span class="sxs-lookup"><span data-stu-id="25f12-109">Database transactions</span></span>  
  
-   <span data-ttu-id="25f12-110">Místní disk přístupu, vzhledem k jeho nízká rychlost relativně k přístupu do paměti</span><span class="sxs-lookup"><span data-stu-id="25f12-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="25f12-111">Operace, jako je to může způsobit přesah při spuštění uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="25f12-111">Operations like these can cause your user interface to hang while they are running.</span></span> <span data-ttu-id="25f12-112">Pokud chcete, aby citlivé uživatelské rozhraní a se potýkají s velká zpoždění spojené s takové operace, <xref:System.ComponentModel.BackgroundWorker> součást nabízí pohodlný řešení.</span><span class="sxs-lookup"><span data-stu-id="25f12-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="25f12-113"><xref:System.ComponentModel.BackgroundWorker> Součásti budete moci provést časově náročná operace asynchronně ("v pozadí"), na vlákno, která se liší od hlavního vlákna uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="25f12-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="25f12-114">Použít <xref:System.ComponentModel.BackgroundWorker>, jednoduše nedostane jakou metodu časově náročné pracovním provést na pozadí, a poté zavoláte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="25f12-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="25f12-115">Volající vlákno dál normálně spustit, když pracovní metoda běží asynchronně.</span><span class="sxs-lookup"><span data-stu-id="25f12-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="25f12-116">Po dokončení metody <xref:System.ComponentModel.BackgroundWorker> výstrahy volající vlákno vypálením <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> událostí, který volitelně obsahuje výsledky operace.</span><span class="sxs-lookup"><span data-stu-id="25f12-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="25f12-117"><xref:System.ComponentModel.BackgroundWorker> Součást má k dispozici **sada nástrojů**v **součásti** kartě. Chcete-li přidat <xref:System.ComponentModel.BackgroundWorker> do svého formuláře, přetáhněte <xref:System.ComponentModel.BackgroundWorker> součásti do formuláře.</span><span class="sxs-lookup"><span data-stu-id="25f12-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="25f12-118">Zobrazí se na hlavním panelu součástí a její vlastnosti se zobrazí v **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="25f12-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="25f12-119">Chcete-li začít asynchronní operaci, použijte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="25f12-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="25f12-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>přijímá volitelný `object` parametr, který slouží k předání argumentů metodu pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="25f12-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="25f12-121"><xref:System.ComponentModel.BackgroundWorker> Třídy zpřístupňuje <xref:System.ComponentModel.BackgroundWorker.DoWork> událostí, ke kterému je pracovní vlákno připojená prostřednictvím <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="25f12-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="25f12-122"><xref:System.ComponentModel.BackgroundWorker.DoWork> Trvá obslužné rutiny události <xref:System.ComponentModel.DoWorkEventArgs> parametr, který má <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="25f12-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="25f12-123">Tato vlastnost přijímá parametru z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a se dá předat do pracovního procesu metodu, která bude volána v <xref:System.ComponentModel.BackgroundWorker.DoWork> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="25f12-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="25f12-124">Následující příklad ukazuje, jak přiřadit výsledku z pracovní metodu s názvem `ComputeFibonacci`.</span><span class="sxs-lookup"><span data-stu-id="25f12-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="25f12-125">Je součástí většího příkladu, které můžete najít v [postupy: implementace formuláře, který používá operaci na pozadí](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span><span class="sxs-lookup"><span data-stu-id="25f12-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="25f12-126">Další informace o používání obslužných rutin událostí najdete v tématu [události](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="25f12-126">For more information on using event handlers, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="25f12-127">Při použití jakékoli více vláken, potenciálně vystavit sami na velmi závažnou a komplexní chyby.</span><span class="sxs-lookup"><span data-stu-id="25f12-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="25f12-128">Obrátit [spravované dělení na vlákna osvědčené postupy](../../../../docs/standard/threading/managed-threading-best-practices.md) před implementací řešení, která používá více vláken.</span><span class="sxs-lookup"><span data-stu-id="25f12-128">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="25f12-129">Další informace o používání <xref:System.ComponentModel.BackgroundWorker> třídy najdete v tématu [postupy: spuštění operace na pozadí](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="25f12-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25f12-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="25f12-130">See Also</span></span>  
 [<span data-ttu-id="25f12-131">NENÍ v sestavení: Více vláken v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="25f12-131">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [<span data-ttu-id="25f12-132">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="25f12-132">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)
