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
ms.openlocfilehash: 9e93f07b3b84264373db0317919b6ee519c8127c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138054"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="2daba-102">Vlákna v popředí a v pozadí</span><span class="sxs-lookup"><span data-stu-id="2daba-102">Foreground and Background Threads</span></span>
<span data-ttu-id="2daba-103">Spravované vlákno je vlákno na pozadí nebo vlákno v popředí.</span><span class="sxs-lookup"><span data-stu-id="2daba-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="2daba-104">Vlákna na pozadí jsou shodné s vlákny na popředí s jednou výjimkou: vlákno na pozadí neudržuje spuštěné prostředí spravovaného spuštění.</span><span class="sxs-lookup"><span data-stu-id="2daba-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="2daba-105">Jakmile jsou všechna vlákna popředí zastavena ve spravovaném procesu (kde soubor EXE je spravované sestavení), systém zastaví všechna vlákna na pozadí a vypne se.</span><span class="sxs-lookup"><span data-stu-id="2daba-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2daba-106">Když zaběhu zastaví vlákno na pozadí, protože proces se vypíná, není vyvolána žádná výjimka ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="2daba-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="2daba-107">Však při podprocesů jsou <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> zastaveny, protože metoda <xref:System.Threading.ThreadAbortException> uvolní doménu aplikace, a je vyvolána v popředí a podprocesů na pozadí.</span><span class="sxs-lookup"><span data-stu-id="2daba-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="2daba-108">Pomocí <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> vlastnosti můžete určit, zda je vlákno podproces emblémem nebo podprocesem v popředí, nebo změnit jeho stav.</span><span class="sxs-lookup"><span data-stu-id="2daba-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="2daba-109">Vlákno lze kdykoli změnit na vlákno na pozadí <xref:System.Threading.Thread.IsBackground%2A> nastavením jeho vlastnosti na `true`.</span><span class="sxs-lookup"><span data-stu-id="2daba-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2daba-110">Stav popředí nebo pozadí vlákna nemá vliv na výsledek neošetřené výjimky ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="2daba-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="2daba-111">V rozhraní .NET Framework verze 2.0 neošetřené výjimky v popředí nebo podprocesy na pozadí má za následek ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="2daba-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="2daba-112">Viz [Výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="2daba-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="2daba-113">Vlákna, která patří do fondu spravovaných <xref:System.Threading.Thread.IsThreadPoolThread%2A> vláken `true`(to znamená, že vlákna, jejichž vlastnost je ) jsou vlákna na pozadí.</span><span class="sxs-lookup"><span data-stu-id="2daba-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="2daba-114">Všechna vlákna, která vstupují do prostředí spravovaného spuštění z nespravovaného kódu, jsou označena jako vlákna na pozadí.</span><span class="sxs-lookup"><span data-stu-id="2daba-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="2daba-115">Všechna vlákna generovaná vytvořením <xref:System.Threading.Thread> a spuštěním nového objektu jsou ve výchozím nastavení vlákny v popředí.</span><span class="sxs-lookup"><span data-stu-id="2daba-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="2daba-116">Pokud používáte vlákno ke sledování aktivity, jako je <xref:System.Threading.Thread.IsBackground%2A> například připojení soketu, nastavte jeho vlastnost tak, aby `true` vlákno nebránilo ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="2daba-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2daba-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="2daba-117">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
