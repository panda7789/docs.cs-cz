---
title: Událost Trasování událostí pro Windows zásobníku
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: f3014a04ba7cacbe37b6706e2919ffd7de19aa65
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715910"
---
# <a name="stack-etw-event"></a><span data-ttu-id="9c4e5-102">Událost Trasování událostí pro Windows zásobníku</span><span class="sxs-lookup"><span data-stu-id="9c4e5-102">Stack ETW Event</span></span>
<span data-ttu-id="9c4e5-103">Událost zásobníku by měla být použita ve spojení s jinými událostmi k vygenerování trasování zásobníku po vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="9c4e5-104">Je zaznamenána v případě, že je povolen zprostředkovatel modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="9c4e5-105">Jedná se o velmi vysokou frekvenci, protože se vyvolá při každém vyvolání jiné běhové události.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="9c4e5-106">Z tohoto důvodu doporučujeme, abyste tuto událost používali opatrně.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="9c4e5-107">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="9c4e5-108">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="9c4e5-108">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="9c4e5-109">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="9c4e5-109">Keyword for raising the event</span></span>|<span data-ttu-id="9c4e5-110">Úroveň</span><span class="sxs-lookup"><span data-stu-id="9c4e5-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="9c4e5-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="9c4e5-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="9c4e5-112">LogAlways (0)</span><span class="sxs-lookup"><span data-stu-id="9c4e5-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="9c4e5-113">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="9c4e5-114">Událost</span><span class="sxs-lookup"><span data-stu-id="9c4e5-114">Event</span></span>|<span data-ttu-id="9c4e5-115">ID události</span><span class="sxs-lookup"><span data-stu-id="9c4e5-115">Event ID</span></span>|<span data-ttu-id="9c4e5-116">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="9c4e5-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="9c4e5-117">82</span><span class="sxs-lookup"><span data-stu-id="9c4e5-117">82</span></span>|<span data-ttu-id="9c4e5-118">Ve spojení s dalšími událostmi pro generování trasování zásobníku za událostí.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="9c4e5-119">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="9c4e5-120">Název pole</span><span class="sxs-lookup"><span data-stu-id="9c4e5-120">Field name</span></span>|<span data-ttu-id="9c4e5-121">Datový typ</span><span class="sxs-lookup"><span data-stu-id="9c4e5-121">Data Type</span></span>|<span data-ttu-id="9c4e5-122">Popis</span><span class="sxs-lookup"><span data-stu-id="9c4e5-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="9c4e5-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="9c4e5-123">ClrInstanceID</span></span>|<span data-ttu-id="9c4e5-124">Win: Uint16</span><span class="sxs-lookup"><span data-stu-id="9c4e5-124">win:Uint16</span></span>|<span data-ttu-id="9c4e5-125">Jedinečný identifikátor modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="9c4e5-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="9c4e5-126">Reserved1</span></span>|<span data-ttu-id="9c4e5-127">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="9c4e5-127">win:UInt8</span></span>|<span data-ttu-id="9c4e5-128">Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-128">Reserved.</span></span>|  
|<span data-ttu-id="9c4e5-129">Reserved2</span><span class="sxs-lookup"><span data-stu-id="9c4e5-129">Reserved2</span></span>|<span data-ttu-id="9c4e5-130">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="9c4e5-130">win:UInt8</span></span>|<span data-ttu-id="9c4e5-131">Rezervovaný.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-131">Reserved.</span></span>|  
|<span data-ttu-id="9c4e5-132">FrameCount</span><span class="sxs-lookup"><span data-stu-id="9c4e5-132">FrameCount</span></span>|<span data-ttu-id="9c4e5-133">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="9c4e5-133">win:UInt32</span></span>|<span data-ttu-id="9c4e5-134">Počet snímků v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="9c4e5-135">Zásobník</span><span class="sxs-lookup"><span data-stu-id="9c4e5-135">Stack</span></span>|<span data-ttu-id="9c4e5-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="9c4e5-136">win:Pointer</span></span>|<span data-ttu-id="9c4e5-137">Sloupce ukazatelů instrukcí.</span><span class="sxs-lookup"><span data-stu-id="9c4e5-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9c4e5-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c4e5-138">See also</span></span>

- [<span data-ttu-id="9c4e5-139">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="9c4e5-139">CLR ETW Events</span></span>](clr-etw-events.md)
