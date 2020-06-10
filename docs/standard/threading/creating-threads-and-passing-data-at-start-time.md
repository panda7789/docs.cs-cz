---
title: Vytváření vláken a předávání dat při spuštění
description: Naučte se vytvářet vlákna a předávat data v počátečním čase procesu operačního systému v .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [.NET Framework], creating
- threading [.NET Framework], passing data to threads
- threading [.NET Framework], retrieving data from threads
ms.assetid: 52b32222-e185-4f42-91a7-eaca65c0ab6d
ms.openlocfilehash: 811028d3c853441ff3a61d3628a44e5c65ba7059
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84661911"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="bcfa3-103">Vytváření vláken a předávání dat při spuštění</span><span class="sxs-lookup"><span data-stu-id="bcfa3-103">Creating threads and passing data at start time</span></span>

<span data-ttu-id="bcfa3-104">Při vytvoření procesu operačního systému vloží operační systém vlákno a spustí kód v tomto procesu, včetně jakékoli původní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-104">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="bcfa3-105">Od tohoto okamžiku je možné vytvořit a zničit domény aplikace, aniž by bylo nutné vytvořit nebo zničit žádná vlákna operačního systému.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-105">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="bcfa3-106">Pokud je spuštěný kód spravovaný, <xref:System.Threading.Thread> lze získat objekt pro vlákno spuštěné v aktuální doméně aplikace načtením statické <xref:System.Threading.Thread.CurrentThread%2A> vlastnosti typu <xref:System.Threading.Thread> .</span><span class="sxs-lookup"><span data-stu-id="bcfa3-106">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="bcfa3-107">Toto téma popisuje vytvoření vlákna a popisuje alternativy k předávání dat proceduře vlákna.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-107">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="bcfa3-108">Vytvoření vlákna</span><span class="sxs-lookup"><span data-stu-id="bcfa3-108">Creating a thread</span></span>

 <span data-ttu-id="bcfa3-109">Vytvořením nového <xref:System.Threading.Thread> objektu se vytvoří nové spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-109">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="bcfa3-110"><xref:System.Threading.Thread>Třída má konstruktory, které přijímají <xref:System.Threading.ThreadStart> delegáta nebo <xref:System.Threading.ParameterizedThreadStart> delegáta. Tento delegát zabalí metodu, která je vyvolána novým vláknem při volání <xref:System.Threading.Thread.Start%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-110">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="bcfa3-111">Volání <xref:System.Threading.Thread.Start%2A> více než jednou způsobí, že <xref:System.Threading.ThreadStateException> bude vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-111">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="bcfa3-112"><xref:System.Threading.Thread.Start%2A>Metoda se vrátí hned, často před samotným spuštěním nového vlákna.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-112">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="bcfa3-113">Pomocí <xref:System.Threading.Thread.ThreadState%2A> vlastností a můžete <xref:System.Threading.Thread.IsAlive%2A> určit stav vlákna v jednom okamžiku, ale tyto vlastnosti by nikdy neměly být použity pro synchronizaci aktivit vláken.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-113">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bcfa3-114">Po spuštění vlákna není nutné uchovávat odkaz na <xref:System.Threading.Thread> objekt.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-114">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="bcfa3-115">Vlákno pokračuje v provádění až do ukončení procedury vlákna.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-115">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="bcfa3-116">Následující příklad kódu vytvoří dvě nová vlákna pro volání instance a statické metody pro jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-116">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="bcfa3-117">Předávání dat do vláken</span><span class="sxs-lookup"><span data-stu-id="bcfa3-117">Passing data to threads</span></span>

 <span data-ttu-id="bcfa3-118">V .NET Framework verze 2,0 <xref:System.Threading.ParameterizedThreadStart> poskytuje delegát snadný způsob, jak předat objekt obsahující data do vlákna při volání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-118">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="bcfa3-119">Příklad kódu naleznete v tématu <xref:System.Threading.ParameterizedThreadStart> .</span><span class="sxs-lookup"><span data-stu-id="bcfa3-119">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="bcfa3-120">Použití <xref:System.Threading.ParameterizedThreadStart> delegáta není typově bezpečný způsob, jak předat data, protože <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody přijímá libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-120">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="bcfa3-121">Alternativou je zapouzdřit proceduru vlákna a data v pomocné třídě a použít <xref:System.Threading.ThreadStart> delegáta k provedení procedury vlákna.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-121">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="bcfa3-122">Následující příklad znázorňuje tuto techniku:</span><span class="sxs-lookup"><span data-stu-id="bcfa3-122">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="bcfa3-123">Ani <xref:System.Threading.ThreadStart> <xref:System.Threading.ParameterizedThreadStart> delegát nemá návratovou hodnotu, protože k dispozici není žádné místo pro návrat dat z asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-123">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="bcfa3-124">Chcete-li načíst výsledky metody vlákna, můžete použít metodu zpětného volání, jak je znázorněno v následující části.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-124">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="bcfa3-125">Načítání dat z vláken pomocí metod zpětného volání</span><span class="sxs-lookup"><span data-stu-id="bcfa3-125">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="bcfa3-126">Následující příklad ukazuje metodu zpětného volání, která načítá data z vlákna.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-126">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="bcfa3-127">Konstruktor pro třídu, která obsahuje data a metodu vlákna, přijímá také delegáta představující metodu zpětného volání; před ukončením metody vlákna vyvolá delegát zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="bcfa3-127">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="bcfa3-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcfa3-128">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bcfa3-129">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="bcfa3-129">Threading</span></span>](index.md)
- [<span data-ttu-id="bcfa3-130">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="bcfa3-130">Using Threads and Threading</span></span>](using-threads-and-threading.md)
