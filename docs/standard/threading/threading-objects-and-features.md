---
title: Dělení objektů a funkcí na vlákna
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
ms.openlocfilehash: dd9b7b8cb194353d0a1c285af10d54dc7366896e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128959"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="b63a7-102">Dělení objektů a funkcí na vlákna</span><span class="sxs-lookup"><span data-stu-id="b63a7-102">Threading objects and features</span></span>

<span data-ttu-id="b63a7-103">Společně s třídou <xref:System.Threading.Thread?displayProperty=nameWithType> poskytuje .NET řadu tříd, které vám pomůžou vyvíjet aplikace s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="b63a7-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="b63a7-104">Následující články poskytují přehled těchto tříd:</span><span class="sxs-lookup"><span data-stu-id="b63a7-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="b63a7-105">Název</span><span class="sxs-lookup"><span data-stu-id="b63a7-105">Title</span></span>|<span data-ttu-id="b63a7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b63a7-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="b63a7-107">Spravovaný fond vláken</span><span class="sxs-lookup"><span data-stu-id="b63a7-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="b63a7-108">Popisuje třídu <xref:System.Threading.ThreadPool?displayProperty=nameWithType>, která poskytuje fond pracovních vláken spravovaných technologií .NET.</span><span class="sxs-lookup"><span data-stu-id="b63a7-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="b63a7-109">Časovače</span><span class="sxs-lookup"><span data-stu-id="b63a7-109">Timers</span></span>](timers.md)|<span data-ttu-id="b63a7-110">Popisuje časovače .NET, které lze použít ve vícevláknovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="b63a7-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="b63a7-111">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="b63a7-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="b63a7-112">Popisuje typy, které lze použít k synchronizaci přístupu k interakci sdíleného vlákna prostředku nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b63a7-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="b63a7-113">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="b63a7-113">EventWaitHandle</span></span>](eventwaithandle.md)|<span data-ttu-id="b63a7-114">Popisuje třídu <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>, která představuje událost synchronizace vlákna.</span><span class="sxs-lookup"><span data-stu-id="b63a7-114">Describes the <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class, which represents a thread synchronization event.</span></span>|
|[<span data-ttu-id="b63a7-115">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="b63a7-115">CountdownEvent</span></span>](countdownevent.md)|<span data-ttu-id="b63a7-116">Popisuje třídu <xref:System.Threading.CountdownEvent?displayProperty=nameWithType>, která představuje událost synchronizace vlákna, která se nastaví, když je její počet nula.</span><span class="sxs-lookup"><span data-stu-id="b63a7-116">Describes the <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class, which represents a thread synchronization event that becomes set when its count is zero.</span></span>|
|[<span data-ttu-id="b63a7-117">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="b63a7-117">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="b63a7-118">Popisuje třídu <xref:System.Threading.Mutex?displayProperty=nameWithType>, která uděluje exkluzivní přístup ke sdílenému prostředku.</span><span class="sxs-lookup"><span data-stu-id="b63a7-118">Describes the <xref:System.Threading.Mutex?displayProperty=nameWithType> class, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="b63a7-119">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="b63a7-119">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="b63a7-120">Popisuje třídu <xref:System.Threading.Semaphore?displayProperty=nameWithType>, která omezuje počet vláken, která mají souběžný přístup ke sdílenému prostředku nebo fondu prostředků.</span><span class="sxs-lookup"><span data-stu-id="b63a7-120">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="b63a7-121">Barrier</span><span class="sxs-lookup"><span data-stu-id="b63a7-121">Barrier</span></span>](barrier.md)|<span data-ttu-id="b63a7-122">Popisuje třídu <xref:System.Threading.Barrier?displayProperty=nameWithType>, která implementuje vzor bariéry pro koordinaci vláken v rámci dvoufázové operace.</span><span class="sxs-lookup"><span data-stu-id="b63a7-122">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class, which implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="b63a7-123">SpinLock</span><span class="sxs-lookup"><span data-stu-id="b63a7-123">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="b63a7-124">V této části najdete popis <xref:System.Threading.SpinLock?displayProperty=nameWithType> struktury, což je zjednodušená alternativa ke třídě <xref:System.Threading.Monitor?displayProperty=nameWithType> pro určité scénáře zamykání nízké úrovně.</span><span class="sxs-lookup"><span data-stu-id="b63a7-124">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="b63a7-125">SpinWait</span><span class="sxs-lookup"><span data-stu-id="b63a7-125">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="b63a7-126">Popisuje strukturu <xref:System.Threading.SpinWait?displayProperty=nameWithType>, která poskytuje podporu pro čekání na číselník.</span><span class="sxs-lookup"><span data-stu-id="b63a7-126">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="b63a7-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b63a7-127">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="b63a7-128">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="b63a7-128">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="b63a7-129">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="b63a7-129">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="b63a7-130">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="b63a7-130">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="b63a7-131">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="b63a7-131">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
