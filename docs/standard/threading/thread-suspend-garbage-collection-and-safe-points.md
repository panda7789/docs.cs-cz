---
title: "Thread.Suspend, kolekce paměti a bezpečné body"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e47674ef8d1b1a7487e42765bcbce4b33cf98769
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="3f8e9-102">Thread.Suspend, kolekce paměti a bezpečné body</span><span class="sxs-lookup"><span data-stu-id="3f8e9-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="3f8e9-103">Při volání <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> na vlákno, poznámky k systému, pozastavení vláken požaduje a umožňuje vlákno k provedení dokud nedosáhne bod bezpečné než ve skutečnosti pozastavení vlákno.</span><span class="sxs-lookup"><span data-stu-id="3f8e9-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="3f8e9-104">Bod bezpečné pro vlákna je bod v jeho spuštění v paměti, které lze provést kolekce.</span><span class="sxs-lookup"><span data-stu-id="3f8e9-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="3f8e9-105">Jakmile bude dosaženo bod bezpečné, modul runtime zaručuje, že pozastavené vlákno nebude provádět žádné další průběh ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="3f8e9-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="3f8e9-106">Podproces provádění mimo spravovaný kód je vždy bezpečné pro uvolňování paměti a vykonávání pokračuje, dokud se pokusí pokračovat v provádění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="3f8e9-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f8e9-107">Chcete-li provést uvolnění paměti, musí modulu runtime pozastavit všechny vláken s výjimkou vláken provádění kolekce.</span><span class="sxs-lookup"><span data-stu-id="3f8e9-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="3f8e9-108">Každé vlákno musí být převeden do bezpečného bodu předtím, než se může pozastavit.</span><span class="sxs-lookup"><span data-stu-id="3f8e9-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8e9-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f8e9-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="3f8e9-110">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3f8e9-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="3f8e9-111">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="3f8e9-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
