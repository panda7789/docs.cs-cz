---
title: Dělení objektů a funkcí na vlákna
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f25609bc3c4dd829c66a1a4514b7f1121f9c0909
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61940930"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="989ab-102">Dělení objektů a funkcí na vlákna</span><span class="sxs-lookup"><span data-stu-id="989ab-102">Threading objects and features</span></span>

<span data-ttu-id="989ab-103">Spolu s <xref:System.Threading.Thread?displayProperty=nameWithType> třídy .NET poskytuje několik tříd, které umožňují vývoj aplikací s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="989ab-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="989ab-104">Následující články poskytují přehled těchto tříd:</span><span class="sxs-lookup"><span data-stu-id="989ab-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="989ab-105">Název</span><span class="sxs-lookup"><span data-stu-id="989ab-105">Title</span></span>|<span data-ttu-id="989ab-106">Popis</span><span class="sxs-lookup"><span data-stu-id="989ab-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="989ab-107">Spravovaný fond vláken</span><span class="sxs-lookup"><span data-stu-id="989ab-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="989ab-108">Popisuje <xref:System.Threading.ThreadPool?displayProperty=nameWithType> třídu, která poskytuje fondu pracovních vláken, které se spravují přes rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="989ab-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="989ab-109">Časovače</span><span class="sxs-lookup"><span data-stu-id="989ab-109">Timers</span></span>](timers.md)|<span data-ttu-id="989ab-110">Popisuje .NET časovače, které lze použít v prostředí s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="989ab-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="989ab-111">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="989ab-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="989ab-112">Popisuje typy, které slouží k synchronizaci přístupu k sdíleného prostředku nebo vlákna interakce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="989ab-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="989ab-113">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="989ab-113">EventWaitHandle</span></span>](eventwaithandle.md)|<span data-ttu-id="989ab-114">Popisuje <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> třídu, která představuje událost synchronizace vlákna.</span><span class="sxs-lookup"><span data-stu-id="989ab-114">Describes the <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class, which represents a thread synchronization event.</span></span>|
|[<span data-ttu-id="989ab-115">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="989ab-115">CountdownEvent</span></span>](countdownevent.md)|<span data-ttu-id="989ab-116">Popisuje <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> třídu, která představuje událost synchronizace podproces, který bude nastaven při její vlastnosti count je nula.</span><span class="sxs-lookup"><span data-stu-id="989ab-116">Describes the <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class, which represents a thread synchronization event that becomes set when its count is zero.</span></span>|
|[<span data-ttu-id="989ab-117">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="989ab-117">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="989ab-118">Popisuje <xref:System.Threading.Mutex?displayProperty=nameWithType> třídu, která udělí se výhradní přístup ke sdíleným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="989ab-118">Describes the <xref:System.Threading.Mutex?displayProperty=nameWithType> class, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="989ab-119">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="989ab-119">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="989ab-120">Popisuje <xref:System.Threading.Semaphore?displayProperty=nameWithType> třídu, která omezuje počet vláken, které můžete přístup ke sdílenému prostředku nebo fond prostředků současně.</span><span class="sxs-lookup"><span data-stu-id="989ab-120">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="989ab-121">Barrier</span><span class="sxs-lookup"><span data-stu-id="989ab-121">Barrier</span></span>](barrier.md)|<span data-ttu-id="989ab-122">Popisuje <xref:System.Threading.Barrier?displayProperty=nameWithType> třídy, která implementuje vzor barrier koordinace vláken v postupné operacích.</span><span class="sxs-lookup"><span data-stu-id="989ab-122">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class, which implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="989ab-123">SpinLock</span><span class="sxs-lookup"><span data-stu-id="989ab-123">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="989ab-124">Popisuje <xref:System.Threading.SpinLock?displayProperty=nameWithType> strukturu, která představuje jednoduché alternativa <xref:System.Threading.Monitor?displayProperty=nameWithType> třídy pro určité scénáře nízké úrovně zamykání.</span><span class="sxs-lookup"><span data-stu-id="989ab-124">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="989ab-125">SpinWait</span><span class="sxs-lookup"><span data-stu-id="989ab-125">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="989ab-126">Popisuje <xref:System.Threading.SpinWait?displayProperty=nameWithType> strukturu, která poskytuje podporu pro čekání na základě typu číselník.</span><span class="sxs-lookup"><span data-stu-id="989ab-126">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="989ab-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="989ab-127">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="989ab-128">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="989ab-128">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="989ab-129">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="989ab-129">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="989ab-130">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="989ab-130">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="989ab-131">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="989ab-131">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
