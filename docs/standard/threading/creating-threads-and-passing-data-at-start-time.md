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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 028f8b978a7809fa9ae4710ab85d7dc84e7b04fc
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44201878"
---
# <a name="creating-threads-and-passing-data-at-start-time"></a><span data-ttu-id="7ccd5-102">Vytváření vláken a předávání dat při spuštění</span><span class="sxs-lookup"><span data-stu-id="7ccd5-102">Creating threads and passing data at start time</span></span>

<span data-ttu-id="7ccd5-103">Když se procesu operačního systému, operační systém vloží vlákna ke spouštění kódu v tomto procesu, včetně domén původní aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-103">When an operating-system process is created, the operating system injects a thread to execute code in that process, including any original application domain.</span></span> <span data-ttu-id="7ccd5-104">Od této chvíle lze vytvořit a zničit bez žádného vlákna operačního systému, nemusí být vytváření nebo zničení aplikačních doménách.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-104">From that point on, application domains can be created and destroyed without any operating system threads necessarily being created or destroyed.</span></span> <span data-ttu-id="7ccd5-105">Pokud jde o spravovaného kódu při provádění kódu, o <xref:System.Threading.Thread> objektu pro vlákno provádění v aktuální doméně aplikace, můžete získat výčtem načítání statické <xref:System.Threading.Thread.CurrentThread%2A> vlastnost typu <xref:System.Threading.Thread>.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-105">If the code being executed is managed code, then a <xref:System.Threading.Thread> object for the thread executing in the current application domain can be obtained by retrieving the static <xref:System.Threading.Thread.CurrentThread%2A> property of type <xref:System.Threading.Thread>.</span></span> <span data-ttu-id="7ccd5-106">Toto téma popisuje vytvoření vlákna a alternativy k předávání dat procedura vlákna.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-106">This topic describes thread creation and discusses alternatives for passing data to the thread procedure.</span></span>  
  
## <a name="creating-a-thread"></a><span data-ttu-id="7ccd5-107">Vytvořením vlákna</span><span class="sxs-lookup"><span data-stu-id="7ccd5-107">Creating a thread</span></span>

 <span data-ttu-id="7ccd5-108">Vytvoření nového <xref:System.Threading.Thread> objekt vytvoří nové spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-108">Creating a new <xref:System.Threading.Thread> object creates a new managed thread.</span></span> <span data-ttu-id="7ccd5-109"><xref:System.Threading.Thread> Třída nemá konstruktor <xref:System.Threading.ThreadStart> delegáta nebo <xref:System.Threading.ParameterizedThreadStart> delegovat; zabalí delegát metody, která je volána při volání nové vlákno <xref:System.Threading.Thread.Start%2A> – metoda.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-109">The <xref:System.Threading.Thread> class has constructors that take a <xref:System.Threading.ThreadStart> delegate or a <xref:System.Threading.ParameterizedThreadStart> delegate; the delegate wraps the method that is invoked by the new thread when you call the <xref:System.Threading.Thread.Start%2A> method.</span></span> <span data-ttu-id="7ccd5-110">Volání <xref:System.Threading.Thread.Start%2A> více než jednou způsobí, že <xref:System.Threading.ThreadStateException> vyvolání.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-110">Calling <xref:System.Threading.Thread.Start%2A> more than once causes a <xref:System.Threading.ThreadStateException> to be thrown.</span></span>  
  
 <span data-ttu-id="7ccd5-111"><xref:System.Threading.Thread.Start%2A> Metoda vrátí okamžitě, často před zahájením nové vlákno je ve skutečnosti.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-111">The <xref:System.Threading.Thread.Start%2A> method returns immediately, often before the new thread has actually started.</span></span> <span data-ttu-id="7ccd5-112">Můžete použít <xref:System.Threading.Thread.ThreadState%2A> a <xref:System.Threading.Thread.IsAlive%2A> vlastnosti k určení stavu vlákna v daném okamžiku provádějí jednu, ale tyto vlastnosti by měla být nikdy použit pro synchronizaci činností vlákna.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-112">You can use the <xref:System.Threading.Thread.ThreadState%2A> and <xref:System.Threading.Thread.IsAlive%2A> properties to determine the state of the thread at any one moment, but these properties should never be used for synchronizing the activities of threads.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ccd5-113">Po zahájení vlákno není nutné zachovat odkaz na <xref:System.Threading.Thread> objektu.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-113">Once a thread is started, it is not necessary to retain a reference to the <xref:System.Threading.Thread> object.</span></span> <span data-ttu-id="7ccd5-114">Vlákno pokračuje v běhu až do ukončení procedura vlákna.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-114">The thread continues to execute until the thread procedure ends.</span></span>  
  
 <span data-ttu-id="7ccd5-115">Následující příklad kódu vytvoří dva nové vláken pro volání instance a statické metody na jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-115">The following code example creates two new threads to call instance and static methods on another object.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#2](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source2.cpp#2)]
 [!code-csharp[System.Threading.ThreadStart2#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source2.cs#2)]
 [!code-vb[System.Threading.ThreadStart2#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source2.vb#2)]  
  
## <a name="passing-data-to-threads"></a><span data-ttu-id="7ccd5-116">Předání dat do vláken</span><span class="sxs-lookup"><span data-stu-id="7ccd5-116">Passing data to threads</span></span>

 <span data-ttu-id="7ccd5-117">V rozhraní .NET Framework verze 2.0 <xref:System.Threading.ParameterizedThreadStart> delegáta poskytuje snadný způsob, jak předat objekt, který obsahuje data na vlákno při volání <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-117">In the .NET Framework version 2.0, the <xref:System.Threading.ParameterizedThreadStart> delegate provides an easy way to pass an object containing data to a thread when you call the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload.</span></span> <span data-ttu-id="7ccd5-118">Zobrazit <xref:System.Threading.ParameterizedThreadStart> příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-118">See <xref:System.Threading.ParameterizedThreadStart> for a code example.</span></span>  
  
 <span data-ttu-id="7ccd5-119">Použití <xref:System.Threading.ParameterizedThreadStart> delegáta není typově bezpečný způsob, jak předávat data, protože <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> přetížení metody přijímá libovolný objekt.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-119">Using the <xref:System.Threading.ParameterizedThreadStart> delegate is not a type-safe way to pass data, because the <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> method overload accepts any object.</span></span> <span data-ttu-id="7ccd5-120">Alternativou je k zapouzdření procedura vlákna a data v pomocnou třídu a použít <xref:System.Threading.ThreadStart> delegát k provádění procedura vlákna.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-120">An alternative is to encapsulate the thread procedure and the data in a helper class and use the <xref:System.Threading.ThreadStart> delegate to execute the thread procedure.</span></span> <span data-ttu-id="7ccd5-121">Následující příklad ukazuje tento postup:</span><span class="sxs-lookup"><span data-stu-id="7ccd5-121">The following example demonstrates this technique:</span></span>

 [!code-cpp[System.Threading.ThreadStart2#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source3.cpp#3)]
 [!code-csharp[System.Threading.ThreadStart2#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source3.cs#3)]
 [!code-vb[System.Threading.ThreadStart2#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source3.vb#3)]  

<span data-ttu-id="7ccd5-122">Ani <xref:System.Threading.ThreadStart> ani <xref:System.Threading.ParameterizedThreadStart> delegát má návratovou hodnotu, protože neexistuje žádný místo pro vrácení dat z asynchronní volání.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-122">Neither <xref:System.Threading.ThreadStart> nor <xref:System.Threading.ParameterizedThreadStart> delegate has a return value, because there is no place to return the data from an asynchronous call.</span></span> <span data-ttu-id="7ccd5-123">K načtení výsledků metody vlákno, můžete použít metodu zpětného volání, jak je znázorněno v následující části.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-123">To retrieve the results of a thread method, you can use a callback method, as shown in the next section.</span></span>
  
## <a name="retrieving-data-from-threads-with-callback-methods"></a><span data-ttu-id="7ccd5-124">Načtení dat z vláken pomocí metody zpětného volání</span><span class="sxs-lookup"><span data-stu-id="7ccd5-124">Retrieving data from threads with callback methods</span></span>

 <span data-ttu-id="7ccd5-125">Následující příklad ukazuje metodu zpětného volání, která načte data z vlákna.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-125">The following example demonstrates a callback method that retrieves data from a thread.</span></span> <span data-ttu-id="7ccd5-126">Konstruktor pro třídu, která obsahuje data a metoda vlákna také přijímá delegát představující metodu zpětného volání; předtím, než metoda vlákno ukončí, vyvolá delegáta zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="7ccd5-126">The constructor for the class that contains the data and the thread method also accepts a delegate representing the callback method; before the thread method ends, it invokes the callback delegate.</span></span>  
  
 [!code-cpp[System.Threading.ThreadStart2#4](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CPP/source4.cpp#4)]
 [!code-csharp[System.Threading.ThreadStart2#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Threading.ThreadStart2/CS/source4.cs#4)]
 [!code-vb[System.Threading.ThreadStart2#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Threading.ThreadStart2/VB/source4.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7ccd5-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ccd5-127">See also</span></span>

- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadStart>  
- <xref:System.Threading.ParameterizedThreadStart>  
- <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="7ccd5-128">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="7ccd5-128">Threading</span></span>](index.md)  
- [<span data-ttu-id="7ccd5-129">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="7ccd5-129">Using Threads and Threading</span></span>](using-threads-and-threading.md)
