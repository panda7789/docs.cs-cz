---
title: Kolizní události Trasování událostí pro Windows
ms.date: 03/30/2017
helpviewer_keywords:
- contention events [.NET Framework]
- ETW, contention events (CLR)
ms.assetid: 6933e753-2f2a-425b-ae84-42138c957d76
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3487b67ea49cecfd0da2b5b3f993ea54d562145d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397517"
---
# <a name="contention-etw-events"></a><span data-ttu-id="e75f2-102">Kolizní události Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="e75f2-102">Contention ETW Events</span></span>
<span data-ttu-id="e75f2-103">Kolizní události jsou vyvolány vždy, když je nutné vyřešit <xref:System.Threading.Monitor?displayProperty=nameWithType> zámky nebo nativní zámky používá modulem runtime.</span><span class="sxs-lookup"><span data-stu-id="e75f2-103">Contention events are raised whenever there is contention for <xref:System.Threading.Monitor?displayProperty=nameWithType> locks or native locks used by the runtime.</span></span> <span data-ttu-id="e75f2-104">Kolize nastane, když je při jiné vlákno má zámek vlákno čekání na zámek.</span><span class="sxs-lookup"><span data-stu-id="e75f2-104">Contention occurs when a thread is waiting for a lock while another thread possesses the lock.</span></span>  
  
 <span data-ttu-id="e75f2-105">V následující tabulce jsou uvedeny klíčové slovo, pod kterým jsou vyvolány kolizní události a úroveň události.</span><span class="sxs-lookup"><span data-stu-id="e75f2-105">The following table shows the keyword under which contention events are raised, and the level of the events.</span></span> <span data-ttu-id="e75f2-106">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="e75f2-106">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="e75f2-107">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="e75f2-107">Keyword for raising the event</span></span>|<span data-ttu-id="e75f2-108">úroveň</span><span class="sxs-lookup"><span data-stu-id="e75f2-108">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="e75f2-109">`ContentionKeyword` (0x4000)</span><span class="sxs-lookup"><span data-stu-id="e75f2-109">`ContentionKeyword` (0x4000)</span></span>|<span data-ttu-id="e75f2-110">Informativní (4)</span><span class="sxs-lookup"><span data-stu-id="e75f2-110">Informational (4)</span></span>|  
  
 <span data-ttu-id="e75f2-111">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="e75f2-111">The following table shows event information.</span></span>  
  
|<span data-ttu-id="e75f2-112">Událost</span><span class="sxs-lookup"><span data-stu-id="e75f2-112">Event</span></span>|<span data-ttu-id="e75f2-113">ID události</span><span class="sxs-lookup"><span data-stu-id="e75f2-113">Event ID</span></span>|<span data-ttu-id="e75f2-114">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="e75f2-114">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`ContentionStart_V1`|<span data-ttu-id="e75f2-115">81</span><span class="sxs-lookup"><span data-stu-id="e75f2-115">81</span></span>|<span data-ttu-id="e75f2-116">Kolizní spustí.</span><span class="sxs-lookup"><span data-stu-id="e75f2-116">Contention starts.</span></span> <span data-ttu-id="e75f2-117">Tato událost nezahrnuje množství otáčí dobu, než je vlákno čeká na získání zámku; je vyvolána, pouze v případě, že vlákno čeká na získání zámku.</span><span class="sxs-lookup"><span data-stu-id="e75f2-117">This event does not include the amount of spinning time before a thread waits to acquire a lock; it is raised only when the thread waits to acquire a lock.</span></span>|  
|`ContentionStop`|<span data-ttu-id="e75f2-118">81</span><span class="sxs-lookup"><span data-stu-id="e75f2-118">81</span></span>|<span data-ttu-id="e75f2-119">Kolizní ukončí.</span><span class="sxs-lookup"><span data-stu-id="e75f2-119">Contention ends.</span></span>|  
  
 <span data-ttu-id="e75f2-120">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="e75f2-120">The following table shows event data.</span></span>  
  
|<span data-ttu-id="e75f2-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="e75f2-121">Field name</span></span>|<span data-ttu-id="e75f2-122">Datový typ</span><span class="sxs-lookup"><span data-stu-id="e75f2-122">Data type</span></span>|<span data-ttu-id="e75f2-123">Popis</span><span class="sxs-lookup"><span data-stu-id="e75f2-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="e75f2-124">Příznaky</span><span class="sxs-lookup"><span data-stu-id="e75f2-124">Flags</span></span>|<span data-ttu-id="e75f2-125">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="e75f2-125">win:UInt8</span></span>|<span data-ttu-id="e75f2-126">0 pro spravované; 1 pro nativní.</span><span class="sxs-lookup"><span data-stu-id="e75f2-126">0 for managed; 1 for native.</span></span>|  
|<span data-ttu-id="e75f2-127">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="e75f2-127">ClrInstanceID</span></span>|<span data-ttu-id="e75f2-128">Win: UInt16</span><span class="sxs-lookup"><span data-stu-id="e75f2-128">win:UInt16</span></span>|<span data-ttu-id="e75f2-129">Jedinečné ID pro instanci CLR.</span><span class="sxs-lookup"><span data-stu-id="e75f2-129">Unique ID for the instance of CLR.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e75f2-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="e75f2-130">See Also</span></span>  
 [<span data-ttu-id="e75f2-131">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="e75f2-131">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
