---
title: Vytváření vláken a předávání dat při spuštění
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
ms.openlocfilehash: a628cbb4c9ec8e1c9ccd9fd73e72a82ecf2b2836
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138106"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="31fba-102">Vytváření vláken a předávání dat při spuštění</span><span class="sxs-lookup"><span data-stu-id="31fba-102">Creating threads and passing data at start time</span></span>

<span data-ttu-id="31fba-103">Při vytvoření procesu operačního systému, operační systém vloží vlákno ke spuštění kódu v tomto procesu, včetně jakékoli původní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="31fba-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="31fba-104">Od tohoto okamžiku mohou být domény aplikací vytvořeny a zničeny bez nutnosti vytváření nebo zničení vláken operačního systému.</span><span class="sxs-lookup"><span data-stu-id="31fba-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="31fba-105">Pokud je spouštěný kód spravován, <xref:System.Threading.Thread> lze získat objekt pro vlákno prováděné v aktuální doméně <xref:System.Threading.Thread.CurrentThread%2A> aplikace <xref:System.Threading.Thread>načtením statické vlastnosti typu .</span><span class="sxs-lookup"><span data-stu-id="31fba-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="31fba-106">Toto téma popisuje vytváření vláken a popisuje alternativy pro předávání dat do postupu podprocesu.</span><span class="sxs-lookup"><span data-stu-id="31fba-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="31fba-107">Vytvoření vlákna</span><span class="sxs-lookup"><span data-stu-id="31fba-107">Creating a thread</span></span>

 <span data-ttu-id="31fba-108">Vytvořenínového <xref:System.Threading.Thread> objektu vytvoří nové spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="31fba-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="31fba-109">Třída <xref:System.Threading.Thread> má konstruktory, <xref:System.Threading.ThreadStart> které mají <xref:System.Threading.ParameterizedThreadStart> delegáta nebo delegáta; delegát zabalí metodu, která je vyvolána novým <xref:System.Threading.Thread.Start%2A> vláknem při volání metody.</span><span class="sxs-lookup"><span data-stu-id="31fba-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="31fba-110">Volání <xref:System.Threading.Thread.Start%2A> více než <xref:System.Threading.ThreadStateException> jednou způsobí, že být vyvolána.</span><span class="sxs-lookup"><span data-stu-id="31fba-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="31fba-111">Metoda <xref:System.Threading.Thread.Start%2A> vrátí okamžitě, často před skutečně spuštěna nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="31fba-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="31fba-112">Vlastnosti <xref:System.Threading.Thread.ThreadState%2A> a <xref:System.Threading.Thread.IsAlive%2A> můžete použít k určení stavu vlákna v jednom okamžiku, ale tyto vlastnosti by nikdy neměly být použity pro synchronizaci aktivit podprocesů.</span><span class="sxs-lookup"><span data-stu-id="31fba-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31fba-113">Po spuštění vlákna není nutné zachovat odkaz na <xref:System.Threading.Thread> objekt.</span><span class="sxs-lookup"><span data-stu-id="31fba-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="31fba-114">Vlákno pokračuje v provádění, dokud procedura podprocesu neskončí.</span><span class="sxs-lookup"><span data-stu-id="31fba-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="31fba-115">Následující příklad kódu vytvoří dvě nová vlákna pro volání instance a statické metody na jiném objektu.</span><span class="sxs-lookup"><span data-stu-id="31fba-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="31fba-116">Předávání dat vláknům</span><span class="sxs-lookup"><span data-stu-id="31fba-116">Passing data to threads</span></span>

 <span data-ttu-id="31fba-117">V rozhraní .NET Framework verze <xref:System.Threading.ParameterizedThreadStart> 2.0 delegát poskytuje snadný způsob, jak předat objekt <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> obsahující data do vlákna při volání přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="31fba-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="31fba-118">Viz <xref:System.Threading.ParameterizedThreadStart> příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="31fba-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="31fba-119">Použití <xref:System.Threading.ParameterizedThreadStart> delegáta není typově bezpečný způsob předání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> dat, protože přetížení metody přijímá libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="31fba-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="31fba-120">Alternativou je zapouzdřit proceduru podprocesu a data <xref:System.Threading.ThreadStart> v pomocné třídě a použít delegáta k provedení postupu podprocesu.</span><span class="sxs-lookup"><span data-stu-id="31fba-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="31fba-121">Následující příklad ukazuje tuto techniku:</span><span class="sxs-lookup"><span data-stu-id="31fba-121">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="31fba-122">Ani <xref:System.Threading.ThreadStart> <xref:System.Threading.ParameterizedThreadStart> delegát nemá vrácenou hodnotu, protože neexistuje žádné místo pro vrácení dat z asynchronního volání.</span><span class="sxs-lookup"><span data-stu-id="31fba-122">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="31fba-123">Chcete-li načíst výsledky metody podprocesu, můžete použít metodu zpětného volání, jak je znázorněno v další části.</span><span class="sxs-lookup"><span data-stu-id="31fba-123">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="31fba-124">Načítání dat z vláken pomocí metod zpětného volání</span><span class="sxs-lookup"><span data-stu-id="31fba-124">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="31fba-125">Následující příklad ukazuje metodu zpětného volání, která načítá data z vlákna.</span><span class="sxs-lookup"><span data-stu-id="31fba-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="31fba-126">Konstruktor pro třídu, která obsahuje data a metodu podprocesu, také přijímá delegáta představujícímetodu zpětného volání; před ukončením metody podprocesu vyvolá delegáta zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="31fba-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="31fba-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="31fba-127">See also</span></span>

- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadStart>
- <xref:System.Threading.ParameterizedThreadStart>
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>
- [<span data-ttu-id="31fba-128">Threading</span><span class="sxs-lookup"><span data-stu-id="31fba-128">Threading</span></span>](index.md)
- [<span data-ttu-id="31fba-129">Použití vláken a zřetězení</span><span class="sxs-lookup"><span data-stu-id="31fba-129">Using Threads and Threading</span></span>](using-threads-and-threading.md)
