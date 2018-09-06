---
title: Vlákna v popředí a v pozadí
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fcedd478ee1eb89c11dc9535b1d2ffe843d0f658
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43868534"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="b8694-102">Vlákna v popředí a v pozadí</span><span class="sxs-lookup"><span data-stu-id="b8694-102">Foreground and Background Threads</span></span>
<span data-ttu-id="b8694-103">Spravované vlákno je vlákno na pozadí nebo vlákno na popředí.</span><span class="sxs-lookup"><span data-stu-id="b8694-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="b8694-104">Vlákna na pozadí jsou shodné s vlákna na popředí s jednou výjimkou: vlákno na pozadí neudržuje spravovaném spouštěcím prostředí spuštění.</span><span class="sxs-lookup"><span data-stu-id="b8694-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="b8694-105">Po ukončení všech vláken v popředí v spravovaného procesu (kde soubor .exe je spravovaná sestavení) systému všechna vlákna na pozadí se zastaví a ukončí.</span><span class="sxs-lookup"><span data-stu-id="b8694-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8694-106">Když modul runtime zastaví vlákna na pozadí, protože proces se vypíná, není vyvolána žádná výjimka ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="b8694-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="b8694-107">Ale když vlákna se zastavila, protože <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda uvolnění domény aplikace <xref:System.Threading.ThreadAbortException> je vyvolána v popředí a pozadí podprocesů.</span><span class="sxs-lookup"><span data-stu-id="b8694-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="b8694-108">Použití <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> vlastnosti k určení, zda je vlákno na pozadí nebo vlákno na popředí nebo na změnu stavu.</span><span class="sxs-lookup"><span data-stu-id="b8694-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="b8694-109">Vlákno lze změnit na vlákně na pozadí v každém okamžiku nastavením jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="b8694-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b8694-110">Popředí nebo pozadí stav vlákna nemá vliv na výsledek neošetřené výjimce ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="b8694-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="b8694-111">V rozhraní .NET Framework verze 2.0 neošetřené výjimky v popředí nebo pozadí vláken výsledkem ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8694-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="b8694-112">Zobrazit [výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="b8694-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="b8694-113">Vlákna, které patří do spravovaný fond vláken (to znamená, jehož vlákna <xref:System.Threading.Thread.IsThreadPoolThread%2A> vlastnost `true`) jsou vlákna na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b8694-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="b8694-114">Všechna vlákna, zadejte spravovaném spouštěcím prostředí z nespravovaného kódu jsou označeny jako vláken na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b8694-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="b8694-115">Všechna vlákna generovaných vytváření a spouštění nového <xref:System.Threading.Thread> objektu jsou ve výchozí vláken v popředí.</span><span class="sxs-lookup"><span data-stu-id="b8694-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="b8694-116">Pokud použijete vlákno k monitorování aktivity, jako je například připojení soketu, nastavte jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost `true` tak, aby vlákno nebrání váš proces se ukončuje.</span><span class="sxs-lookup"><span data-stu-id="b8694-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8694-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8694-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
- <xref:System.Threading.Thread>  
- <xref:System.Threading.ThreadAbortException>
