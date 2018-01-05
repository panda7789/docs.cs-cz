---
title: "Kolizní události Trasování událostí pro Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a09419c208d4ac754eb48da0c8d1b5d93386eb3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="contention-etw-events"></a><span data-ttu-id="62ba4-102">Kolizní události Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="62ba4-102">Contention ETW Events</span></span>
<span data-ttu-id="62ba4-103">Kolizní události jsou vyvolány vždy, když je nutné vyřešit <xref:System.Threading.Monitor?displayProperty=nameWithType> zámky nebo nativní zámky používá modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="62ba4-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="62ba4-104">Kolize nastane, když je při jiné vlákno má zámek vlákno čekání na zámek.</span><span class="sxs-lookup"><span data-stu-id="62ba4-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="62ba4-105">V následující tabulce jsou uvedeny klíčové slovo, pod kterým jsou vyvolány kolizní události a úroveň události.</span><span class="sxs-lookup"><span data-stu-id="62ba4-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="62ba4-106">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="62ba4-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="62ba4-107">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="62ba4-107">Keyword for raising the event</span></span>|<span data-ttu-id="62ba4-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="62ba4-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="62ba4-109">`ContentionKeyword`(0x4000)</span><span class="sxs-lookup"><span data-stu-id="62ba4-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="62ba4-110">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="62ba4-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="62ba4-111">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="62ba4-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="62ba4-112">Událost</span><span class="sxs-lookup"><span data-stu-id="62ba4-112">Event</span></span>|<span data-ttu-id="62ba4-113">ID události</span><span class="sxs-lookup"><span data-stu-id="62ba4-113">Event ID</span></span>|<span data-ttu-id="62ba4-114">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="62ba4-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="62ba4-115">81</span><span class="sxs-lookup"><span data-stu-id="62ba4-115">81</span></span>|<span data-ttu-id="62ba4-116">Kolizní spustí.</span><span class="sxs-lookup"><span data-stu-id="62ba4-116">Contention starts.</span></span> <span data-ttu-id="62ba4-117">Tato událost nezahrnuje množství otáčí dobu, než je vlákno čeká na získání zámku; je vyvolána, pouze v případě, že vlákno čeká na získání zámku.</span><span class="sxs-lookup"><span data-stu-id="62ba4-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="62ba4-118">81</span><span class="sxs-lookup"><span data-stu-id="62ba4-118">81</span></span>|<span data-ttu-id="62ba4-119">Kolizní ukončí.</span><span class="sxs-lookup"><span data-stu-id="62ba4-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="62ba4-120">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="62ba4-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="62ba4-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="62ba4-121">Field name</span></span>|<span data-ttu-id="62ba4-122">Datový typ</span><span class="sxs-lookup"><span data-stu-id="62ba4-122">Data type</span></span>|<span data-ttu-id="62ba4-123">Popis</span><span class="sxs-lookup"><span data-stu-id="62ba4-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="62ba4-124">Příznaky</span><span class="sxs-lookup"><span data-stu-id="62ba4-124">Flags</span></span>|<span data-ttu-id="62ba4-125">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="62ba4-125">win:UInt8</span></span>|<span data-ttu-id="62ba4-126">0 pro spravované; 1 pro nativní.</span><span class="sxs-lookup"><span data-stu-id="62ba4-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="62ba4-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="62ba4-127">ClrInstanceID</span></span>|<span data-ttu-id="62ba4-128">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="62ba4-128">win:UInt16</span></span>|<span data-ttu-id="62ba4-129">Jedinečné ID pro instanci CLR.</span><span class="sxs-lookup"><span data-stu-id="62ba4-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="62ba4-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="62ba4-130">See Also</span></span>  
 [<span data-ttu-id="62ba4-131">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="62ba4-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
