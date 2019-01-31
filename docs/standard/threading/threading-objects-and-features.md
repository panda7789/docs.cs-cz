---
title: Práce s vlákny funkce a objekty
ms.date: 10/01/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], features
- managed threading
ms.assetid: 239b2e8d-581b-4ca3-992b-0e8525b9321c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51cbe8296c265be2433b0648c38b9ad60ae57fcb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55257692"
---
# <a name="threading-objects-and-features"></a><span data-ttu-id="92f6e-102">Práce s vlákny funkce a objekty</span><span class="sxs-lookup"><span data-stu-id="92f6e-102">Threading objects and features</span></span>

<span data-ttu-id="92f6e-103">Spolu s <xref:System.Threading.Thread?displayProperty=nameWithType> třídy .NET poskytuje několik tříd, které umožňují vývoj aplikací s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="92f6e-103">Along with the <xref:System.Threading.Thread?displayProperty=nameWithType> class, .NET provides a number of classes that help you develop multithreaded applications.</span></span> <span data-ttu-id="92f6e-104">Následující články poskytují přehled těchto tříd:</span><span class="sxs-lookup"><span data-stu-id="92f6e-104">The following articles provide overview of those classes:</span></span>

|<span data-ttu-id="92f6e-105">Název</span><span class="sxs-lookup"><span data-stu-id="92f6e-105">Title</span></span>|<span data-ttu-id="92f6e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="92f6e-106">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="92f6e-107">Spravovaný fond vláken</span><span class="sxs-lookup"><span data-stu-id="92f6e-107">The managed thread pool</span></span>](the-managed-thread-pool.md)|<span data-ttu-id="92f6e-108">Popisuje <xref:System.Threading.ThreadPool?displayProperty=nameWithType> třídu, která poskytuje fondu pracovních vláken, které se spravují přes rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="92f6e-108">Describes the <xref:System.Threading.ThreadPool?displayProperty=nameWithType> class, which provides a pool of worker threads that are managed by .NET.</span></span>|  
|[<span data-ttu-id="92f6e-109">Časovače</span><span class="sxs-lookup"><span data-stu-id="92f6e-109">Timers</span></span>](timers.md)|<span data-ttu-id="92f6e-110">Popisuje .NET časovače, které lze použít v prostředí s více vlákny.</span><span class="sxs-lookup"><span data-stu-id="92f6e-110">Describes .NET timers that can be used in a multithreaded environment.</span></span>|
|[<span data-ttu-id="92f6e-111">Přehled primitiv synchronizace</span><span class="sxs-lookup"><span data-stu-id="92f6e-111">Overview of synchronization primitives</span></span>](overview-of-synchronization-primitives.md)|<span data-ttu-id="92f6e-112">Popisuje typy, které slouží k synchronizaci přístupu k sdíleného prostředku nebo vlákna interakce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="92f6e-112">Describes types that can be used to synchronize access to a shared resource or control thread interaction.</span></span>|
|[<span data-ttu-id="92f6e-113">Eventwaithandle – CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="92f6e-113">EventWaitHandle, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)|<span data-ttu-id="92f6e-114">Popisuje obslužné rutiny čekání spravované události, které se používají k synchronizaci aktivity vláken signalizace a čeká na signál.</span><span class="sxs-lookup"><span data-stu-id="92f6e-114">Describes managed event wait handles, which are used to synchronize thread activities by signaling and waiting for signals.</span></span>|
|[<span data-ttu-id="92f6e-115">Mutex – třídy</span><span class="sxs-lookup"><span data-stu-id="92f6e-115">Mutexes</span></span>](mutexes.md)|<span data-ttu-id="92f6e-116">Popisuje <xref:System.Threading.Mutex?displayProperty=nameWithType>, která uděluje exkluzivní přístup ke sdíleným prostředkům.</span><span class="sxs-lookup"><span data-stu-id="92f6e-116">Describes <xref:System.Threading.Mutex?displayProperty=nameWithType>, which grants exclusive access to a shared resource.</span></span>|
|[<span data-ttu-id="92f6e-117">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="92f6e-117">Semaphore and SemaphoreSlim</span></span>](semaphore-and-semaphoreslim.md)|<span data-ttu-id="92f6e-118">Popisuje <xref:System.Threading.Semaphore?displayProperty=nameWithType> třídu, která omezuje počet vláken, které můžete přístup ke sdílenému prostředku nebo fond prostředků současně.</span><span class="sxs-lookup"><span data-stu-id="92f6e-118">Describes the <xref:System.Threading.Semaphore?displayProperty=nameWithType> class, which limits number of threads that can access a shared resource or a pool of resources concurrently.</span></span>|
|[<span data-ttu-id="92f6e-119">Barrier</span><span class="sxs-lookup"><span data-stu-id="92f6e-119">Barrier</span></span>](barrier.md)|<span data-ttu-id="92f6e-120">Popisuje <xref:System.Threading.Barrier?displayProperty=nameWithType> třídu, která implementuje vzor barrier koordinace vláken v postupné operacích.</span><span class="sxs-lookup"><span data-stu-id="92f6e-120">Describes the <xref:System.Threading.Barrier?displayProperty=nameWithType> class that implements the barrier pattern for coordination of threads in phased operations.</span></span>|
|[<span data-ttu-id="92f6e-121">SpinLock</span><span class="sxs-lookup"><span data-stu-id="92f6e-121">SpinLock</span></span>](spinlock.md)|<span data-ttu-id="92f6e-122">Popisuje <xref:System.Threading.SpinLock?displayProperty=nameWithType> strukturu, která představuje jednoduché alternativa <xref:System.Threading.Monitor?displayProperty=nameWithType> třídy pro určité scénáře nízké úrovně zamykání.</span><span class="sxs-lookup"><span data-stu-id="92f6e-122">Describes the <xref:System.Threading.SpinLock?displayProperty=nameWithType> structure, which is a lightweight alternative to the <xref:System.Threading.Monitor?displayProperty=nameWithType> class for certain low-level locking scenarios.</span></span>|
|[<span data-ttu-id="92f6e-123">SpinWait</span><span class="sxs-lookup"><span data-stu-id="92f6e-123">SpinWait</span></span>](spinwait.md)|<span data-ttu-id="92f6e-124">Popisuje <xref:System.Threading.SpinWait?displayProperty=nameWithType> strukturu, která poskytuje podporu pro čekání na základě typu číselník.</span><span class="sxs-lookup"><span data-stu-id="92f6e-124">Describes the <xref:System.Threading.SpinWait?displayProperty=nameWithType> structure, which provides support for spin-based waiting.</span></span>|

## <a name="see-also"></a><span data-ttu-id="92f6e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92f6e-125">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>
- [<span data-ttu-id="92f6e-126">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="92f6e-126">Using threads and threading</span></span>](using-threads-and-threading.md)
- [<span data-ttu-id="92f6e-127">Asynchronní vstupně-výstupní operace se soubory</span><span class="sxs-lookup"><span data-stu-id="92f6e-127">Asynchronous File I/O</span></span>](../io/asynchronous-file-i-o.md)
- [<span data-ttu-id="92f6e-128">Paralelní programování</span><span class="sxs-lookup"><span data-stu-id="92f6e-128">Parallel Programming</span></span>](../parallel-programming/index.md)
- [<span data-ttu-id="92f6e-129">Task Parallel Library (TPL)</span><span class="sxs-lookup"><span data-stu-id="92f6e-129">Task Parallel Library (TPL)</span></span>](../parallel-programming/task-parallel-library-tpl.md)
