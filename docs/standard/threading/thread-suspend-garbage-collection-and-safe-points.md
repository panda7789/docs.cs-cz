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
ms.openlocfilehash: fc3af01167fe97b701bdb0c7bc37af02d8e8a77c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658584"
---
# <a name="threadsuspend-garbage-collection-and-safe-points"></a><span data-ttu-id="1e2ee-102">Thread.Suspend, kolekce paměti a bezpečné body</span><span class="sxs-lookup"><span data-stu-id="1e2ee-102">Thread.Suspend, Garbage Collection, and Safe Points</span></span>
<span data-ttu-id="1e2ee-103">Při volání <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> ve vlákně, systém zjistí, že se požaduje pozastavení vlákna a umožňuje spuštění, dokud nedosáhne bezpečné bod před skutečně pozastavení vlákna vlákna.</span><span class="sxs-lookup"><span data-stu-id="1e2ee-103">When you call <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> on a thread, the system notes that a thread suspension has been requested and allows the thread to execute until it has reached a safe point before actually suspending the thread.</span></span> <span data-ttu-id="1e2ee-104">Bod bezpečné pro vlákna je bod v jeho spuštění, na které uvolňování paměti kolekce provést.</span><span class="sxs-lookup"><span data-stu-id="1e2ee-104">A safe point for a thread is a point in its execution at which garbage collection can be performed.</span></span>  
  
 <span data-ttu-id="1e2ee-105">Po dosažení bod bezpečné, modul runtime zaručuje, že pozastaveného vlákna nebude provádět žádný další krok ve spravovaném kódu.</span><span class="sxs-lookup"><span data-stu-id="1e2ee-105">Once a safe point is reached, the runtime guarantees that the suspended thread will not make any further progress in managed code.</span></span> <span data-ttu-id="1e2ee-106">Vlákno provádění mimo spravovaný kód je vždy bezpečné pro uvolnění paměti a provádění pokračuje, dokud se pokusí pokračovat v provádění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="1e2ee-106">A thread executing outside managed code is always safe for garbage collection, and its execution continues until it attempts to resume execution of managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e2ee-107">Aby bylo možné provádět uvolňování paměti, modul runtime musí pozastavit všechna vlákna kromě vlákna provádění v kolekci.</span><span class="sxs-lookup"><span data-stu-id="1e2ee-107">In order to perform a garbage collection, the runtime must suspend all the threads except the thread performing the collection.</span></span> <span data-ttu-id="1e2ee-108">Každé vlákno musí být převeden do bezpečného bodu předtím, než je možné ho pozastavit.</span><span class="sxs-lookup"><span data-stu-id="1e2ee-108">Each thread must be brought to a safe point before it can be suspended.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2ee-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e2ee-109">See also</span></span>

- <xref:System.Threading.Thread>  
- <xref:System.GC>  
- [<span data-ttu-id="1e2ee-110">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="1e2ee-110">Threading</span></span>](../../../docs/standard/threading/index.md)  
- [<span data-ttu-id="1e2ee-111">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="1e2ee-111">Automatic Memory Management</span></span>](../../../docs/standard/automatic-memory-management.md)
