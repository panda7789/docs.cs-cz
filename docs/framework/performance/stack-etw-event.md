---
title: "Událost Trasování událostí pro Windows zásobníku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1107c6608fe5136eb6159b1d4f0a438e95c4dabb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="stack-etw-event"></a><span data-ttu-id="2d6e6-102">Událost Trasování událostí pro Windows zásobníku</span><span class="sxs-lookup"><span data-stu-id="2d6e6-102">Stack ETW Event</span></span>
<span data-ttu-id="2d6e6-103">Událost zásobníku by používána v kombinaci s jinými událostmi ke generování trasování zásobníku po událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="2d6e6-104">Je zaznamenána, pokud je povolen zprostředkovatel modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="2d6e6-105">Toto je velmi vysoká frekvence událost, protože se vyvolá, vždy, když se jiný modul runtime událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="2d6e6-106">Z tohoto důvodu doporučujeme používat tato událost se zvýšenou opatrností.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="2d6e6-107">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="2d6e6-108">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="2d6e6-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="2d6e6-109">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="2d6e6-109">Keyword for raising the event</span></span>|<span data-ttu-id="2d6e6-110">úroveň</span><span class="sxs-lookup"><span data-stu-id="2d6e6-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2d6e6-111">`StackKeyword`(0x40000000)</span><span class="sxs-lookup"><span data-stu-id="2d6e6-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="2d6e6-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="2d6e6-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="2d6e6-113">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2d6e6-114">Událost</span><span class="sxs-lookup"><span data-stu-id="2d6e6-114">Event</span></span>|<span data-ttu-id="2d6e6-115">ID události</span><span class="sxs-lookup"><span data-stu-id="2d6e6-115">Event ID</span></span>|<span data-ttu-id="2d6e6-116">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="2d6e6-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="2d6e6-117">82</span><span class="sxs-lookup"><span data-stu-id="2d6e6-117">82</span></span>|<span data-ttu-id="2d6e6-118">Ve spojení s jinými událostmi ke generování následující událost trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="2d6e6-119">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2d6e6-120">Název pole</span><span class="sxs-lookup"><span data-stu-id="2d6e6-120">Field name</span></span>|<span data-ttu-id="2d6e6-121">Datový typ</span><span class="sxs-lookup"><span data-stu-id="2d6e6-121">Data Type</span></span>|<span data-ttu-id="2d6e6-122">Popis</span><span class="sxs-lookup"><span data-stu-id="2d6e6-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2d6e6-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2d6e6-123">ClrInstanceID</span></span>|<span data-ttu-id="2d6e6-124">Win: Uint16</span><span class="sxs-lookup"><span data-stu-id="2d6e6-124">win:Uint16</span></span>|<span data-ttu-id="2d6e6-125">Modul runtime jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="2d6e6-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="2d6e6-126">Reserved1</span></span>|<span data-ttu-id="2d6e6-127">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="2d6e6-127">win:UInt8</span></span>|<span data-ttu-id="2d6e6-128">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-128">Reserved.</span></span>|  
|<span data-ttu-id="2d6e6-129">Vyhrazeno2</span><span class="sxs-lookup"><span data-stu-id="2d6e6-129">Reserved2</span></span>|<span data-ttu-id="2d6e6-130">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="2d6e6-130">win:UInt8</span></span>|<span data-ttu-id="2d6e6-131">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-131">Reserved.</span></span>|  
|<span data-ttu-id="2d6e6-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="2d6e6-132">FrameCount</span></span>|<span data-ttu-id="2d6e6-133">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2d6e6-133">win:UInt32</span></span>|<span data-ttu-id="2d6e6-134">Počet rámců v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="2d6e6-135">Rámec</span><span class="sxs-lookup"><span data-stu-id="2d6e6-135">Stack</span></span>|<span data-ttu-id="2d6e6-136">Win: ukazatele</span><span class="sxs-lookup"><span data-stu-id="2d6e6-136">win:Pointer</span></span>|<span data-ttu-id="2d6e6-137">Sloupce ukazatele na instrukce.</span><span class="sxs-lookup"><span data-stu-id="2d6e6-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2d6e6-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="2d6e6-138">See Also</span></span>  
 [<span data-ttu-id="2d6e6-139">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="2d6e6-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
