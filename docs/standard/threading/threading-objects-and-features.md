---
title: Dělení objektů a funkcí na vlákna
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73128959"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="6e1de-102">Dělení objektů a funkcí na vlákna</span><span class="sxs-lookup"><span data-stu-id="6e1de-102">Threading objects and features</span></span>

<span data-ttu-id="6e1de-103">Spolu s <xref:System.Threading.Thread?displayProperty=nameWithType> třídou .NET poskytuje řadu tříd, které vám pomohou vyvíjet aplikace s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="6e1de-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="6e1de-104">Následující články poskytují přehled těchto tříd:</span><span class="sxs-lookup"><span data-stu-id="6e1de-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="6e1de-105">Nadpis</span><span class="sxs-lookup"><span data-stu-id="6e1de-105">Title</span></span>|<span data-ttu-id="6e1de-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6e1de-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="6e1de-107">Spravovaný fond vláken</span><span class="sxs-lookup"><span data-stu-id="6e1de-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="6e1de-108">Popisuje třídu, <xref:System.Threading.ThreadPool?displayProperty=nameWithType> která poskytuje fond pracovních podprocesů, které jsou spravovány rozhraním .NET.</span><span class="sxs-lookup"><span data-stu-id="6e1de-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="6e1de-109">Časovače</span><span class="sxs-lookup"><span data-stu-id="6e1de-109">Timers</span></span>](timers.md)|<span data-ttu-id="6e1de-110">Popisuje časovače rozhraní .NET, které lze použít v prostředí s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="6e1de-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="6e1de-111">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="6e1de-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="6e1de-112">Popisuje typy, které lze použít k synchronizaci přístupu ke sdílenému prostředku nebo ovládacímu vláknu.</span><span class="sxs-lookup"><span data-stu-id="6e1de-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="6e1de-113">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="6e1de-113">EventWaitHandle</span></span>](eventwaithandle.md)|<span data-ttu-id="6e1de-114">Popisuje třídu, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> která představuje událost synchronizace vláken.</span><span class="sxs-lookup"><span data-stu-id="6e1de-114">Describes the <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class, which represents a thread synchronization event.</span></span>|
|[<span data-ttu-id="6e1de-115">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="6e1de-115">CountdownEvent</span></span>](countdownevent.md)|<span data-ttu-id="6e1de-116">Popisuje třídu, <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> která představuje událost synchronizace vláken, která se nastaví, když je její počet nula.</span><span class="sxs-lookup"><span data-stu-id="6e1de-116">Describes the <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class, which represents a thread synchronization event that becomes set when its count is zero.</span></span>|
|[<span data-ttu-id="6e1de-117">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="6e1de-117">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="6e1de-118">Popisuje třídu, <xref:System.Threading.Mutex?displayProperty=nameWithType> která uděluje výhradní přístup ke sdílenému prostředku.</span><span class="sxs-lookup"><span data-stu-id="6e1de-118">Describes the <xref:System.Threading.Mutex?displayProperty=nameWithType> class, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="6e1de-119">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="6e1de-119">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="6e1de-120">Popisuje třídu, <xref:System.Threading.Semaphore?displayProperty=nameWithType> která omezuje počet podprocesů, které mají přístup ke sdílenému prostředku nebo fondu prostředků současně.</span><span class="sxs-lookup"><span data-stu-id="6e1de-120">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="6e1de-121">Bariéra</span><span class="sxs-lookup"><span data-stu-id="6e1de-121">Barrier</span></span>](barrier.md)|<span data-ttu-id="6e1de-122">Popisuje třídu, <xref:System.Threading.Barrier?displayProperty=nameWithType> která implementuje bariérový vzor pro koordinaci vláken v postupných operacích.</span><span class="sxs-lookup"><span data-stu-id="6e1de-122">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class, which implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="6e1de-123">SpinLock</span><span class="sxs-lookup"><span data-stu-id="6e1de-123">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="6e1de-124">Popisuje <xref:System.Threading.SpinLock?displayProperty=nameWithType> strukturu, která je zjednodušenou <xref:System.Threading.Monitor?displayProperty=nameWithType> alternativou ke třídě pro určité scénáře uzamčení nižší úrovně.</span><span class="sxs-lookup"><span data-stu-id="6e1de-124">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="6e1de-125">SpinWait</span><span class="sxs-lookup"><span data-stu-id="6e1de-125">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="6e1de-126">Popisuje <xref:System.Threading.SpinWait?displayProperty=nameWithType> strukturu, která poskytuje podporu pro čekání na základě spin.</span><span class="sxs-lookup"><span data-stu-id="6e1de-126">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="6e1de-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e1de-127">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="6e1de-128">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="6e1de-128">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="6e1de-129">Asynchronní I/O soubory</span><span class="sxs-lookup"><span data-stu-id="6e1de-129">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="6e1de-130">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="6e1de-130">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="6e1de-131">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="6e1de-131">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
