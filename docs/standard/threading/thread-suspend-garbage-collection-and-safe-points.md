---
title: Thread.Suspend, kolekce paměti a bezpečné body
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- suspending threads
- safe points
- threading [.NET Framework], suspending
- threading [.NET Framework], garbage collection
- garbage collection, threads
ms.assetid: e8f58e17-2714-4821-802a-f8eb3b2baa62
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ded5c057b1c257e8bcf3c8427f5810720eaf0947
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582158"
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="ecc41-102">Thread.Suspend, kolekce paměti a bezpečné body</span><span class="sxs-lookup"><span data-stu-id="ecc41-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="ecc41-103">Při volání <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> na vlákno, poznámky k systému, pozastavení vláken požaduje a umožňuje vlákno k provedení dokud nedosáhne bod bezpečné než ve skutečnosti pozastavení vlákno.</span><span class="sxs-lookup"><span data-stu-id="ecc41-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="ecc41-104">Bod bezpečné pro vlákna je bod v jeho spuštění v paměti, které lze provést kolekce.</span><span class="sxs-lookup"><span data-stu-id="ecc41-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="ecc41-105">Jakmile bude dosaženo bod bezpečné, modul runtime zaručuje, že pozastavené vlákno nebude provádět žádné další průběh ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="ecc41-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="ecc41-106">Podproces provádění mimo spravovaný kód je vždy bezpečné pro uvolňování paměti a vykonávání pokračuje, dokud se pokusí pokračovat v provádění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="ecc41-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ecc41-107">Chcete-li provést uvolnění paměti, musí modulu runtime pozastavit všechny vláken s výjimkou vláken provádění kolekce.</span><span class="sxs-lookup"><span data-stu-id="ecc41-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="ecc41-108">Každé vlákno musí být převeden do bezpečného bodu předtím, než se může pozastavit.</span><span class="sxs-lookup"><span data-stu-id="ecc41-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecc41-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecc41-109">See Also</span></span>  
 <xref:System.Threading.Thread>  
 <xref:System.GC>  
 [<span data-ttu-id="ecc41-110">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="ecc41-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="ecc41-111">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="ecc41-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
