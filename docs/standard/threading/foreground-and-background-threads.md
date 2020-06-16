---
title: Vlákna v popředí a v pozadí
description: Určete nebo změňte, zda se jedná o vlákno vlákna na pozadí nebo o vlákno na popředí pomocí vlastnosti Thread. na pozadí v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
ms.openlocfilehash: 6cb7a92851728e16f4a317d6c24d072acee72a94
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84769038"
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="b4be9-103">Vlákna v popředí a v pozadí</span><span class="sxs-lookup"><span data-stu-id="b4be9-103">Foreground and Background Threads</span></span>
<span data-ttu-id="b4be9-104">Spravované vlákno je vlákno na pozadí nebo vlákno na popředí.</span><span class="sxs-lookup"><span data-stu-id="b4be9-104">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="b4be9-105">Vlákna na pozadí jsou shodná s vlákny na popředí s jednou výjimkou: vlákno na pozadí neudržuje spravované prostředí pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="b4be9-105">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="b4be9-106">Jakmile jsou všechna vlákna na popředí zastavena ve spravovaném procesu (kde soubor. exe je spravované sestavení), systém zastaví všechna vlákna na pozadí a ukončí činnost.</span><span class="sxs-lookup"><span data-stu-id="b4be9-106">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4be9-107">Když modul runtime zastaví vlákno na pozadí, protože probíhá ukončování procesu, ve vlákně není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="b4be9-107">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="b4be9-108">Nicméně při zastavení vlákna, protože <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda uvolní aplikační doménu, <xref:System.Threading.ThreadAbortException> je vyvolána v vláknech v popředí i na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b4be9-108">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="b4be9-109">Pomocí <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> vlastnosti určíte, zda je vlákno pozadí nebo vlákno na popředí nebo zda chcete změnit jeho stav.</span><span class="sxs-lookup"><span data-stu-id="b4be9-109">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="b4be9-110">Vlákno lze kdykoli změnit na vlákno na pozadí nastavením jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnosti na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="b4be9-110">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b4be9-111">Stav popředí nebo pozadí vlákna nemá vliv na výsledek neošetřené výjimky ve vlákně.</span><span class="sxs-lookup"><span data-stu-id="b4be9-111">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="b4be9-112">V .NET Framework verze 2,0 způsobí Neošetřená výjimka v obou vláknech popředí nebo na pozadí ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="b4be9-112">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="b4be9-113">Viz [výjimky ve spravovaných vláknech](exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="b4be9-113">See [Exceptions in Managed Threads](exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="b4be9-114">Vlákna, která patří do spravovaného fondu vláken (tj. vlákna, jejichž <xref:System.Threading.Thread.IsThreadPoolThread%2A> vlastnost je `true` ), jsou vlákna na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b4be9-114">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="b4be9-115">Všechna vlákna, která vstupují do spravovaného prostředí pro spuštění z nespravovaného kódu, jsou označena jako vlákna na pozadí.</span><span class="sxs-lookup"><span data-stu-id="b4be9-115">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="b4be9-116">Všechna vlákna vygenerovaná vytvořením a spuštěním nového <xref:System.Threading.Thread> objektu jsou ve výchozím nastavení vlákna na popředí.</span><span class="sxs-lookup"><span data-stu-id="b4be9-116">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="b4be9-117">Použijete-li vlákno k monitorování aktivity, jako je například připojení soketu, nastavte jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost na `true` tak, aby vlákno nebránilo ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="b4be9-117">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4be9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4be9-118">See also</span></span>

- <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>
- <xref:System.Threading.Thread>
- <xref:System.Threading.ThreadAbortException>
