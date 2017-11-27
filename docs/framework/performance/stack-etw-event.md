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
ms.openlocfilehash: 55219fe755f49b6edbd3b53cc686bf4f9087aa08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="stack-etw-event"></a><span data-ttu-id="95530-102">Událost Trasování událostí pro Windows zásobníku</span><span class="sxs-lookup"><span data-stu-id="95530-102">Stack ETW Event</span></span>
<span data-ttu-id="95530-103">Událost zásobníku by používána v kombinaci s jinými událostmi ke generování trasování zásobníku po událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="95530-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="95530-104">Je zaznamenána, pokud je povolen zprostředkovatel modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="95530-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="95530-105">Toto je velmi vysoká frekvence událost, protože se vyvolá, vždy, když se jiný modul runtime událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="95530-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="95530-106">Z tohoto důvodu doporučujeme používat tato událost se zvýšenou opatrností.</span><span class="sxs-lookup"><span data-stu-id="95530-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="95530-107">V následující tabulce jsou uvedeny – klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="95530-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="95530-108">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="95530-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="95530-109">– Klíčové slovo za vyvolání události</span><span class="sxs-lookup"><span data-stu-id="95530-109">Keyword for raising the event</span></span>|<span data-ttu-id="95530-110">úroveň</span><span class="sxs-lookup"><span data-stu-id="95530-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="95530-111">`StackKeyword`(0x40000000)</span><span class="sxs-lookup"><span data-stu-id="95530-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="95530-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="95530-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="95530-113">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="95530-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="95530-114">Událost</span><span class="sxs-lookup"><span data-stu-id="95530-114">Event</span></span>|<span data-ttu-id="95530-115">ID události</span><span class="sxs-lookup"><span data-stu-id="95530-115">Event ID</span></span>|<span data-ttu-id="95530-116">Vyvolá, když</span><span class="sxs-lookup"><span data-stu-id="95530-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="95530-117">82</span><span class="sxs-lookup"><span data-stu-id="95530-117">82</span></span>|<span data-ttu-id="95530-118">Ve spojení s jinými událostmi ke generování následující událost trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="95530-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="95530-119">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="95530-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="95530-120">Název pole</span><span class="sxs-lookup"><span data-stu-id="95530-120">Field name</span></span>|<span data-ttu-id="95530-121">Datový typ</span><span class="sxs-lookup"><span data-stu-id="95530-121">Data Type</span></span>|<span data-ttu-id="95530-122">Popis</span><span class="sxs-lookup"><span data-stu-id="95530-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="95530-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="95530-123">ClrInstanceID</span></span>|<span data-ttu-id="95530-124">Win: Uint16</span><span class="sxs-lookup"><span data-stu-id="95530-124">win:Uint16</span></span>|<span data-ttu-id="95530-125">Modul runtime jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="95530-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="95530-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="95530-126">Reserved1</span></span>|<span data-ttu-id="95530-127">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="95530-127">win:UInt8</span></span>|<span data-ttu-id="95530-128">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="95530-128">Reserved.</span></span>|  
|<span data-ttu-id="95530-129">Vyhrazeno2</span><span class="sxs-lookup"><span data-stu-id="95530-129">Reserved2</span></span>|<span data-ttu-id="95530-130">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="95530-130">win:UInt8</span></span>|<span data-ttu-id="95530-131">Vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="95530-131">Reserved.</span></span>|  
|<span data-ttu-id="95530-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="95530-132">FrameCount</span></span>|<span data-ttu-id="95530-133">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="95530-133">win:UInt32</span></span>|<span data-ttu-id="95530-134">Počet rámců v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="95530-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="95530-135">Rámec</span><span class="sxs-lookup"><span data-stu-id="95530-135">Stack</span></span>|<span data-ttu-id="95530-136">Win: ukazatele</span><span class="sxs-lookup"><span data-stu-id="95530-136">win:Pointer</span></span>|<span data-ttu-id="95530-137">Sloupce ukazatele na instrukce.</span><span class="sxs-lookup"><span data-stu-id="95530-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95530-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="95530-138">See Also</span></span>  
 [<span data-ttu-id="95530-139">CLR ETW – události</span><span class="sxs-lookup"><span data-stu-id="95530-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
