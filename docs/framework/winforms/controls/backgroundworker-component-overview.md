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
ms.openlocfilehash: e91d74b7ca5515dd63ba17a9111cadf5090dae2a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046110"
---
# <a name="backgroundworker-component-overview"></a><span data-ttu-id="4ae29-102">BackgroundWorker – přehled komponenty</span><span class="sxs-lookup"><span data-stu-id="4ae29-102">BackgroundWorker Component Overview</span></span>
<span data-ttu-id="4ae29-103">Existuje mnoho běžně prováděných operací, které mohou trvat dlouhou dobu.</span><span class="sxs-lookup"><span data-stu-id="4ae29-103">There are many commonly performed operations that can take a long time to execute.</span></span> <span data-ttu-id="4ae29-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4ae29-104">For example:</span></span>  
  
- <span data-ttu-id="4ae29-105">Stahování obrázků</span><span class="sxs-lookup"><span data-stu-id="4ae29-105">Image downloads</span></span>  
  
- <span data-ttu-id="4ae29-106">Vyvolání webové služby</span><span class="sxs-lookup"><span data-stu-id="4ae29-106">Web service invocations</span></span>  
  
- <span data-ttu-id="4ae29-107">Stahování souborů a nahrávání (včetně pro aplikace peer-to-peer)</span><span class="sxs-lookup"><span data-stu-id="4ae29-107">File downloads and uploads (including for peer-to-peer applications)</span></span>  
  
- <span data-ttu-id="4ae29-108">Komplexní místní výpočty</span><span class="sxs-lookup"><span data-stu-id="4ae29-108">Complex local computations</span></span>  
  
- <span data-ttu-id="4ae29-109">Transakce databáze</span><span class="sxs-lookup"><span data-stu-id="4ae29-109">Database transactions</span></span>  
  
- <span data-ttu-id="4ae29-110">Přístup k místnímu disku s ohledem na jeho zpomalení vzhledem k přístupu k paměti</span><span class="sxs-lookup"><span data-stu-id="4ae29-110">Local disk access, given its slow speed relative to memory access</span></span>  
  
 <span data-ttu-id="4ae29-111">Tyto operace mohou způsobit, že vaše uživatelské rozhraní bude blokovat při jejich spuštění.</span><span class="sxs-lookup"><span data-stu-id="4ae29-111">Operations like these can cause your user interface to block while they are running.</span></span> <span data-ttu-id="4ae29-112">Když chcete reagovat na uživatelské rozhraní s dlouhou dobou zpoždění spojené s těmito operacemi, <xref:System.ComponentModel.BackgroundWorker> komponenta nabízí pohodlné řešení.</span><span class="sxs-lookup"><span data-stu-id="4ae29-112">When you want a responsive UI and you are faced with long delays associated with such operations, the <xref:System.ComponentModel.BackgroundWorker> component provides a convenient solution.</span></span>  
  
 <span data-ttu-id="4ae29-113"><xref:System.ComponentModel.BackgroundWorker> Komponenta poskytuje možnost asynchronního provádění časově náročných operací ("na pozadí") na vlákně, které se liší od hlavního vlákna uživatelského rozhraní vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4ae29-113">The <xref:System.ComponentModel.BackgroundWorker> component gives you the ability to execute time-consuming operations asynchronously ("in the background"), on a thread different from your application's main UI thread.</span></span> <span data-ttu-id="4ae29-114">Chcete-li <xref:System.ComponentModel.BackgroundWorker>použít, jednoduše Řekněte mu, jakou časově náročnou metodu pracovního procesu spustit na pozadí a pak <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> zavolejte metodu.</span><span class="sxs-lookup"><span data-stu-id="4ae29-114">To use a <xref:System.ComponentModel.BackgroundWorker>, you simply tell it what time-consuming worker method to execute in the background, and then you call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="4ae29-115">Volající vlákno pokračuje v normálním běhu, zatímco metoda Worker běží asynchronně.</span><span class="sxs-lookup"><span data-stu-id="4ae29-115">Your calling thread continues to run normally while the worker method runs asynchronously.</span></span> <span data-ttu-id="4ae29-116">Až se metoda dokončí, <xref:System.ComponentModel.BackgroundWorker> upozorní volající vlákno <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> vyvoláním události, která volitelně obsahuje výsledky operace.</span><span class="sxs-lookup"><span data-stu-id="4ae29-116">When the method is finished, the <xref:System.ComponentModel.BackgroundWorker> alerts the calling thread by firing the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event, which optionally contains the results of the operation.</span></span>  
  
 <span data-ttu-id="4ae29-117">Součást je k dispozici v **sadě nástrojů**na kartě **součásti.** <xref:System.ComponentModel.BackgroundWorker> Chcete-li <xref:System.ComponentModel.BackgroundWorker> přidat do formuláře, <xref:System.ComponentModel.BackgroundWorker> přetáhněte komponentu do formuláře.</span><span class="sxs-lookup"><span data-stu-id="4ae29-117">The <xref:System.ComponentModel.BackgroundWorker> component is available from the **Toolbox**, in the **Components** tab. To add a <xref:System.ComponentModel.BackgroundWorker> to your form, drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span> <span data-ttu-id="4ae29-118">Zobrazuje se v zásobníku komponent a jeho vlastnosti se zobrazí v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="4ae29-118">It appears in the component tray, and its properties appear in the **Properties** window.</span></span>  
  
 <span data-ttu-id="4ae29-119">Chcete-li spustit asynchronní operaci, použijte <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="4ae29-119">To start your asynchronous operation, use the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method.</span></span> <span data-ttu-id="4ae29-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>převezme volitelný `object` parametr, který lze použít k předání argumentů metodě pracovního procesu.</span><span class="sxs-lookup"><span data-stu-id="4ae29-120"><xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> takes an optional `object` parameter, which can be used to pass arguments to your worker method.</span></span> <span data-ttu-id="4ae29-121">Třída zveřejňuje událost, ke které je pracovní <xref:System.ComponentModel.BackgroundWorker.DoWork> vlákno připojeno prostřednictvím obslužné rutiny události. <xref:System.ComponentModel.BackgroundWorker.DoWork> <xref:System.ComponentModel.BackgroundWorker></span><span class="sxs-lookup"><span data-stu-id="4ae29-121">The <xref:System.ComponentModel.BackgroundWorker> class exposes the <xref:System.ComponentModel.BackgroundWorker.DoWork> event, to which your worker thread is attached through a <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
 <span data-ttu-id="4ae29-122">Obslužná rutina <xref:System.ComponentModel.DoWorkEventArgs> <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> události přebírá parametr, který má vlastnost. <xref:System.ComponentModel.BackgroundWorker.DoWork></span><span class="sxs-lookup"><span data-stu-id="4ae29-122">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler takes a <xref:System.ComponentModel.DoWorkEventArgs> parameter, which has an <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property.</span></span> <span data-ttu-id="4ae29-123">Tato vlastnost přijímá parametr z <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> a lze jej předat metodě pracovního procesu, která bude volána <xref:System.ComponentModel.BackgroundWorker.DoWork> v obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="4ae29-123">This property receives the parameter from <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> and can be passed to your worker method, which will be called in the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="4ae29-124">Následující příklad ukazuje, jak přiřadit výsledek z volané `ComputeFibonacci`metody Worker.</span><span class="sxs-lookup"><span data-stu-id="4ae29-124">The following example shows how to assign a result from a worker method called `ComputeFibonacci`.</span></span> <span data-ttu-id="4ae29-125">Je součástí většího příkladu, který můžete najít v [tématu Postup: Implementujte formulář, který používá operaci](how-to-implement-a-form-that-uses-a-background-operation.md)na pozadí.</span><span class="sxs-lookup"><span data-stu-id="4ae29-125">It is part of a larger example, which you can find at [How to: Implement a Form That Uses a Background Operation](how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
 [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
 [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
 <span data-ttu-id="4ae29-126">Další informace o použití obslužných rutin událostí naleznete v tématu [events](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="4ae29-126">For more information on using event handlers, see [Events](../../../standard/events/index.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="4ae29-127">Při použití multithreadingu s více vlákny můžete vystavit hodně závažných a složitých chyb.</span><span class="sxs-lookup"><span data-stu-id="4ae29-127">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="4ae29-128">Před implementací jakéhokoli řešení, které používá multithreading, si Projděte [osvědčené postupy spravovaného vlákna](../../../standard/threading/managed-threading-best-practices.md) .</span><span class="sxs-lookup"><span data-stu-id="4ae29-128">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
 <span data-ttu-id="4ae29-129">Další informace o použití <xref:System.ComponentModel.BackgroundWorker> třídy naleznete v tématu [How to: Spustí operaci na pozadí](how-to-run-an-operation-in-the-background.md).</span><span class="sxs-lookup"><span data-stu-id="4ae29-129">For more information on using the <xref:System.ComponentModel.BackgroundWorker> class, see [How to: Run an Operation in the Background](how-to-run-an-operation-in-the-background.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ae29-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ae29-130">See also</span></span>

- [<span data-ttu-id="4ae29-131">Spravované podprocesy</span><span class="sxs-lookup"><span data-stu-id="4ae29-131">Managed Threading</span></span>](../../../standard/threading/index.md)
- [<span data-ttu-id="4ae29-132">Přehled asynchronních vzorů založených na událostech</span><span class="sxs-lookup"><span data-stu-id="4ae29-132">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="4ae29-133">Postupy: Implementace formuláře, který používá operaci na pozadí</span><span class="sxs-lookup"><span data-stu-id="4ae29-133">How to: Implement a Form That Uses a Background Operation</span></span>](how-to-implement-a-form-that-uses-a-background-operation.md)
