---
title: "Plánování vláken"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 6bb715c11cc0d9b07e4ea8805ace7680ca92097c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="scheduling-threads"></a><span data-ttu-id="008a8-102">Plánování vláken</span><span class="sxs-lookup"><span data-stu-id="008a8-102">Scheduling Threads</span></span>
<span data-ttu-id="008a8-103">Každé vlákno má přiřazen prioritu přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="008a8-103">Every thread has a thread priority assigned to it.</span></span> <span data-ttu-id="008a8-104">Vlákna v rámci modul common language runtime vytvořili původně přiřazené priority **ThreadPriority.Normal**.</span><span class="sxs-lookup"><span data-stu-id="008a8-104">Threads created within the common language runtime are initially assigned the priority of **ThreadPriority.Normal**.</span></span> <span data-ttu-id="008a8-105">Vlákna vytvořen vně modulu runtime zachovat prioritu, kterou měla před jejich zadali spravovaném prostředí.</span><span class="sxs-lookup"><span data-stu-id="008a8-105">Threads created outside the runtime retain the priority they had before they entered the managed environment.</span></span> <span data-ttu-id="008a8-106">Můžete získat nebo nastavit prioritu všech vlákno se **Thread.Priority** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="008a8-106">You can get or set the priority of any thread with the **Thread.Priority** property.</span></span>  
  
 <span data-ttu-id="008a8-107">Vláken je naplánováno spuštění na základě jejich priority.</span><span class="sxs-lookup"><span data-stu-id="008a8-107">Threads are scheduled for execution based on their priority.</span></span> <span data-ttu-id="008a8-108">I když vláken jsou prováděny v modulu runtime, všechna vlákna přiřazené řezy čas procesoru v operačním systému.</span><span class="sxs-lookup"><span data-stu-id="008a8-108">Even though threads are executing within the runtime, all threads are assigned processor time slices by the operating system.</span></span> <span data-ttu-id="008a8-109">Podrobnosti o plánování algoritmus používaný k určení pořadí, ve kterém jsou prováděny vláken se liší podle každý operační systém.</span><span class="sxs-lookup"><span data-stu-id="008a8-109">The details of the scheduling algorithm used to determine the order in which threads are executed varies with each operating system.</span></span> <span data-ttu-id="008a8-110">V některých operačních systémů je vždy vlákno s nejvyšší prioritou (z těchto vláken, které mohou být provedeny) naplánovat na spuštění první.</span><span class="sxs-lookup"><span data-stu-id="008a8-110">Under some operating systems, the thread with the highest priority (of those threads that can be executed) is always scheduled to run first.</span></span> <span data-ttu-id="008a8-111">Pokud více vláken se stejnou prioritou jsou všechny dostupné scheduler procházení vláken, na který tuto prioritu, udělíte každé vlákno pevné časovém intervalu, do kterého chcete provést.</span><span class="sxs-lookup"><span data-stu-id="008a8-111">If multiple threads with the same priority are all available, the scheduler cycles through the threads at that priority, giving each thread a fixed time slice in which to execute.</span></span> <span data-ttu-id="008a8-112">Tak dlouho, dokud je k dispozici pro spouštění vlákna s vyšší prioritou, nižší prioritu vláken Nezískávat provést.</span><span class="sxs-lookup"><span data-stu-id="008a8-112">As long as a thread with a higher priority is available to run, lower priority threads do not get to execute.</span></span> <span data-ttu-id="008a8-113">Když na uvedenou prioritou nejsou žádné další spustitelného vláken, Plánovač přesune na další nižší prioritu a plány vláken, na který tuto prioritu pro provedení.</span><span class="sxs-lookup"><span data-stu-id="008a8-113">When there are no more runnable threads at a given priority, the scheduler moves to the next lower priority and schedules the threads at that priority for execution.</span></span> <span data-ttu-id="008a8-114">Pokud bude spustitelného vyšší priorita vlákna, nižší prioritu vlákno je zrušené a vyšší prioritu vlákno je povoleno spustit znovu.</span><span class="sxs-lookup"><span data-stu-id="008a8-114">If a higher priority thread becomes runnable, the lower priority thread is preempted and the higher priority thread is allowed to execute once again.</span></span> <span data-ttu-id="008a8-115">Nad všechny který operační systém můžete také upravit vlákno priority dynamicky jako uživatelské rozhraní aplikace jsou přesouvána mezi popředí a na pozadí.</span><span class="sxs-lookup"><span data-stu-id="008a8-115">On top of all that, the operating system can also adjust thread priorities dynamically as an application's user interface is moved between foreground and background.</span></span> <span data-ttu-id="008a8-116">Jinými operačními systémy můžete použít jiný algoritmus plánování.</span><span class="sxs-lookup"><span data-stu-id="008a8-116">Other operating systems might choose to use a different scheduling algorithm.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="008a8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="008a8-117">See Also</span></span>  
 [<span data-ttu-id="008a8-118">Použití vláken a dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="008a8-118">Using Threads and Threading</span></span>](../../../docs/standard/threading/using-threads-and-threading.md)  
 [<span data-ttu-id="008a8-119">Dělení na spravovaná a nespravovaná vlákna ve Windows</span><span class="sxs-lookup"><span data-stu-id="008a8-119">Managed and Unmanaged Threading in Windows</span></span>](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
