---
title: "Vytváření vláken a předávání dat při spuštění"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 61808dc804cc627ab368a5250414dfcc5f54c87e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="3ea64-102">Vytváření vláken a předávání dat při spuštění</span><span class="sxs-lookup"><span data-stu-id="3ea64-102">Creating Threads and Passing Data at Start Time</span></span>
<span data-ttu-id="3ea64-103">Když je vytvořen procesu operačního systému, operační systém vloží vlákna ke spouštění kódu v procesu, včetně všech původní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="3ea64-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="3ea64-104">Od tohoto okamžiku se lze vytvořit a zničen bez žádné podprocesy operačního systému nutně vytvořením nebo zničení aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="3ea64-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="3ea64-105">Pokud je spravovaný kód spouštěna kód, pak <xref:System.Threading.Thread> objektu pro přístup z více vláken provádění v aktuální doméně aplikace je možné získat načítání statických <xref:System.Threading.Thread.CurrentThread%2A> vlastnost typu <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="3ea64-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="3ea64-106">Toto téma popisuje vytváření vláken a alternativami pro předávání dat na postup přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="3ea64-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="3ea64-107">Vytváření vlákna</span><span class="sxs-lookup"><span data-stu-id="3ea64-107">Creating a Thread</span></span>  
 <span data-ttu-id="3ea64-108">Vytvoření nové <xref:System.Threading.Thread> objekt vytvoří nové spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="3ea64-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="3ea64-109"><xref:System.Threading.Thread> Třída obsahuje konstruktory, které nepřijímají <xref:System.Threading.ThreadStart> delegovat nebo <xref:System.Threading.ParameterizedThreadStart> delegovat; delegát zabalí metody, která je volána nové vlákno při volání <xref:System.Threading.Thread.Start%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="3ea64-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="3ea64-110">Volání metody <xref:System.Threading.Thread.Start%2A> více než jednou způsobí, že <xref:System.Threading.ThreadStateException> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="3ea64-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="3ea64-111"><xref:System.Threading.Thread.Start%2A> Metoda vrátí okamžitě, často předtím, než má ve skutečnosti spustit nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="3ea64-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="3ea64-112">Můžete použít <xref:System.Threading.Thread.ThreadState%2A> a <xref:System.Threading.Thread.IsAlive%2A> vlastnosti k určení stavu vlákno daném okamžiku, ale tyto vlastnosti musí být nikdy použit pro synchronizaci aktivity vláken.</span><span class="sxs-lookup"><span data-stu-id="3ea64-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ea64-113">Jakmile začne vlákno, není nutné zachovat odkaz na <xref:System.Threading.Thread> objektu.</span><span class="sxs-lookup"><span data-stu-id="3ea64-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="3ea64-114">Vlákno bude pokračovat v provádění až do ukončení procesu přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="3ea64-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="3ea64-115">Následující příklad kódu vytvoří dva nové vláken pro volání instance a statické metody na jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="3ea64-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads-and-retrieving-data-from-threads"></a><span data-ttu-id="3ea64-116">Předání dat do vláken a načtení dat z vláken</span><span class="sxs-lookup"><span data-stu-id="3ea64-116">Passing Data to Threads and Retrieving Data from Threads</span></span>  
 <span data-ttu-id="3ea64-117">V rozhraní .NET Framework verze 2.0 <xref:System.Threading.ParameterizedThreadStart> delegáta poskytuje snadný způsob, jak předat objekt obsahující data na vlákno při volání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="3ea64-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="3ea64-118">V tématu <xref:System.Threading.ParameterizedThreadStart> příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="3ea64-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="3ea64-119">Pomocí <xref:System.Threading.ParameterizedThreadStart> delegát není bezpečný způsob k předávání dat, protože <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody přijímá libovolného objektu.</span><span class="sxs-lookup"><span data-stu-id="3ea64-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="3ea64-120">Alternativou je zapouzdření vlákno postup a data v pomocnou třídu a použijte <xref:System.Threading.ThreadStart> delegáta ke spuštění procedury přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="3ea64-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="3ea64-121">Tento postup je uveden v příklady dvě kódu, které následují.</span><span class="sxs-lookup"><span data-stu-id="3ea64-121">This technique is shown in the two code examples that follow.</span></span>  
  
 <span data-ttu-id="3ea64-122">Ani jeden z těchto delegáti má návratovou hodnotu, protože není k dispozici žádné místní vrátit data z asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="3ea64-122">Neither of these delegates has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="3ea64-123">Pokud chcete načíst výsledky metody přístup z více vláken, můžete použít metody zpětného volání, jak je předvedeno v druhém příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3ea64-123">To retrieve the results of a thread method, you can use a callback method, as demonstrated in the second code example.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  
  
### <a name="retrieving-data-with-callback-methods"></a><span data-ttu-id="3ea64-124">Načítání dat pomocí metody zpětného volání</span><span class="sxs-lookup"><span data-stu-id="3ea64-124">Retrieving Data with Callback Methods</span></span>  
 <span data-ttu-id="3ea64-125">Následující příklad ukazuje metodu zpětného volání, která načte data z vlákna.</span><span class="sxs-lookup"><span data-stu-id="3ea64-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="3ea64-126">Konstruktor pro třídu, která obsahuje data a metodu přístup z více vláken také přijímá delegáta představující metoda zpětného volání; předtím, než skončí metodu přístup z více vláken, vyvolá delegáta zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="3ea64-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3ea64-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ea64-127">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadStart>  
 <xref:System.Threading.ParameterizedThreadStart>  
 <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="3ea64-128">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3ea64-128">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="3ea64-129">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3ea64-129">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)
