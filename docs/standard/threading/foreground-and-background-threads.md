---
title: "Vlákna v popředí a v pozadí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], foreground
- threading [.NET Framework], background
- foreground threads
- background threads
ms.assetid: cfe0d632-dd35-47e0-91ad-f742a444005e
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 83022bd27379e1ee34197af4897a5c809f495f48
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="foreground-and-background-threads"></a><span data-ttu-id="9596e-102">Vlákna v popředí a v pozadí</span><span class="sxs-lookup"><span data-stu-id="9596e-102">Foreground and Background Threads</span></span>
<span data-ttu-id="9596e-103">Spravované vlákno je vlákna na pozadí nebo vlákna popředí.</span><span class="sxs-lookup"><span data-stu-id="9596e-103">A managed thread is either a background thread or a foreground thread.</span></span> <span data-ttu-id="9596e-104">Vlákna na pozadí jsou stejné jako vlákna na popředí s jednou výjimkou: vlákna na pozadí nezachovat spravovaného spouštění prostředí spuštěna.</span><span class="sxs-lookup"><span data-stu-id="9596e-104">Background threads are identical to foreground threads with one exception: a background thread does not keep the managed execution environment running.</span></span> <span data-ttu-id="9596e-105">Jakmile v spravovaného procesu (kde soubor .exe je spravované sestavení) byly zastaveny všechny vlákna na popředí, systém zastaví všechny vlákna na pozadí a ukončí.</span><span class="sxs-lookup"><span data-stu-id="9596e-105">Once all foreground threads have been stopped in a managed process (where the .exe file is a managed assembly), the system stops all background threads and shuts down.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9596e-106">Když se modul runtime zastaví vlákna na pozadí, protože proces se vypíná, nedojde k výjimce v vlákno.</span><span class="sxs-lookup"><span data-stu-id="9596e-106">When the runtime stops a background thread because the process is shutting down, no exception is thrown in the thread.</span></span> <span data-ttu-id="9596e-107">Ale když vláken byla zastavena, protože <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> metoda uvolní doménu aplikace, <xref:System.Threading.ThreadAbortException> je vyvolána v popředí ani pozadí vláken.</span><span class="sxs-lookup"><span data-stu-id="9596e-107">However, when threads are stopped because the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method unloads the application domain, a <xref:System.Threading.ThreadAbortException> is thrown in both foreground and background threads.</span></span>  
  
 <span data-ttu-id="9596e-108">Použití <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> vlastnosti k určení, zda je vlákna na pozadí nebo vlákna popředí nebo změnit jeho stav.</span><span class="sxs-lookup"><span data-stu-id="9596e-108">Use the <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType> property to determine whether a thread is a background or a foreground thread, or to change its status.</span></span> <span data-ttu-id="9596e-109">Vlákno můžete změnit tak, aby vlákna na pozadí kdykoli znovu nastavením jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="9596e-109">A thread can be changed to a background thread at any time by setting its <xref:System.Threading.Thread.IsBackground%2A> property to `true`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9596e-110">Stav popředí nebo pozadí vlákno nemá vliv na výsledek k neošetřené výjimce v vlákno.</span><span class="sxs-lookup"><span data-stu-id="9596e-110">The foreground or background status of a thread does not affect the outcome of an unhandled exception in the thread.</span></span> <span data-ttu-id="9596e-111">V rozhraní .NET Framework verze 2.0 k neošetřené výjimce v popředí nebo pozadí vláken výsledkem ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="9596e-111">In the .NET Framework version 2.0, an unhandled exception in either foreground or background threads results in termination of the application.</span></span> <span data-ttu-id="9596e-112">V tématu [výjimky ve spravovaných vláknech](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span><span class="sxs-lookup"><span data-stu-id="9596e-112">See [Exceptions in Managed Threads](../../../docs/standard/threading/exceptions-in-managed-threads.md).</span></span>  
  
 <span data-ttu-id="9596e-113">Vláken, které patří do spravovaný fond vláken (to znamená, jehož vláken <xref:System.Threading.Thread.IsThreadPoolThread%2A> vlastnost je `true`) jsou vlákna na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9596e-113">Threads that belong to the managed thread pool (that is, threads whose <xref:System.Threading.Thread.IsThreadPoolThread%2A> property is `true`) are background threads.</span></span> <span data-ttu-id="9596e-114">Všechna vlákna, zadejte spravovaného prostředí pro spouštění z nespravovaného kódu jsou označeny jako vlákna na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9596e-114">All threads that enter the managed execution environment from unmanaged code are marked as background threads.</span></span> <span data-ttu-id="9596e-115">Všechna vlákna vygenerovaných vytvoření a spuštění nové <xref:System.Threading.Thread> objektu se ve výchozím nastavení vlákna na popředí.</span><span class="sxs-lookup"><span data-stu-id="9596e-115">All threads generated by creating and starting a new <xref:System.Threading.Thread> object are by default foreground threads.</span></span>  
  
 <span data-ttu-id="9596e-116">Používáte-li vlákna monitorování aktivity, jako je připojení soketu, nastavte jeho <xref:System.Threading.Thread.IsBackground%2A> vlastnost `true` tak, aby vlákno nezabrání váš proces se ukončuje.</span><span class="sxs-lookup"><span data-stu-id="9596e-116">If you use a thread to monitor an activity, such as a socket connection, set its <xref:System.Threading.Thread.IsBackground%2A> property to `true` so that the thread does not prevent your process from terminating.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9596e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9596e-117">See Also</span></span>  
 <xref:System.Threading.Thread.IsBackground%2A?displayProperty=nameWithType>  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.ThreadAbortException>
