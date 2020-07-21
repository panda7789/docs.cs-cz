---
title: Událost Trasování událostí pro Windows zásobníku
description: Přečtěte si o události ETW zásobníku, která by se měla používat ve spojení s jinými událostmi k vygenerování trasování zásobníku po vyvolání události.
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
ms.openlocfilehash: cab496615c4ef17831895b72c8987917e3c06e77
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474134"
---
# <a name="stack-etw-event"></a><span data-ttu-id="2c4d9-103">Událost Trasování událostí pro Windows zásobníku</span><span class="sxs-lookup"><span data-stu-id="2c4d9-103">Stack ETW Event</span></span>
<span data-ttu-id="2c4d9-104">Událost zásobníku by měla být použita ve spojení s jinými událostmi k vygenerování trasování zásobníku po vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-104">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="2c4d9-105">Je zaznamenána v případě, že je povolen zprostředkovatel modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-105">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="2c4d9-106">Jedná se o velmi vysokou frekvenci, protože se vyvolá při každém vyvolání jiné běhové události.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-106">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="2c4d9-107">Z tohoto důvodu doporučujeme, abyste tuto událost používali opatrně.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-107">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="2c4d9-108">Klíčové slovo a úroveň jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-108">The following table shows the keyword and level.</span></span> <span data-ttu-id="2c4d9-109">(Další informace najdete v tématu [klíčová slova a úrovně CLR ETW](clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="2c4d9-109">(For more information, see [CLR ETW Keywords and Levels](clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="2c4d9-110">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="2c4d9-110">Keyword for raising the event</span></span>|<span data-ttu-id="2c4d9-111">Úroveň</span><span class="sxs-lookup"><span data-stu-id="2c4d9-111">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="2c4d9-112">`StackKeyword`0x40000000</span><span class="sxs-lookup"><span data-stu-id="2c4d9-112">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="2c4d9-113">LogAlways (0)</span><span class="sxs-lookup"><span data-stu-id="2c4d9-113">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="2c4d9-114">V následující tabulce jsou uvedeny informace o událostech.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-114">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="2c4d9-115">Událost</span><span class="sxs-lookup"><span data-stu-id="2c4d9-115">Event</span></span>|<span data-ttu-id="2c4d9-116">ID události</span><span class="sxs-lookup"><span data-stu-id="2c4d9-116">Event ID</span></span>|<span data-ttu-id="2c4d9-117">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="2c4d9-117">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="2c4d9-118">82</span><span class="sxs-lookup"><span data-stu-id="2c4d9-118">82</span></span>|<span data-ttu-id="2c4d9-119">Ve spojení s dalšími událostmi pro generování trasování zásobníku za událostí.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-119">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="2c4d9-120">V následující tabulce jsou uvedena data události.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-120">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="2c4d9-121">Název pole</span><span class="sxs-lookup"><span data-stu-id="2c4d9-121">Field name</span></span>|<span data-ttu-id="2c4d9-122">Typ dat</span><span class="sxs-lookup"><span data-stu-id="2c4d9-122">Data Type</span></span>|<span data-ttu-id="2c4d9-123">Popis</span><span class="sxs-lookup"><span data-stu-id="2c4d9-123">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="2c4d9-124">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="2c4d9-124">ClrInstanceID</span></span>|<span data-ttu-id="2c4d9-125">Win: Uint16</span><span class="sxs-lookup"><span data-stu-id="2c4d9-125">win:Uint16</span></span>|<span data-ttu-id="2c4d9-126">Jedinečný identifikátor modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-126">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="2c4d9-127">Reserved1</span><span class="sxs-lookup"><span data-stu-id="2c4d9-127">Reserved1</span></span>|<span data-ttu-id="2c4d9-128">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="2c4d9-128">win:UInt8</span></span>|<span data-ttu-id="2c4d9-129">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-129">Reserved.</span></span>|  
|<span data-ttu-id="2c4d9-130">Reserved2</span><span class="sxs-lookup"><span data-stu-id="2c4d9-130">Reserved2</span></span>|<span data-ttu-id="2c4d9-131">Win: UInt8</span><span class="sxs-lookup"><span data-stu-id="2c4d9-131">win:UInt8</span></span>|<span data-ttu-id="2c4d9-132">Vyhrazeno.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-132">Reserved.</span></span>|  
|<span data-ttu-id="2c4d9-133">FrameCount</span><span class="sxs-lookup"><span data-stu-id="2c4d9-133">FrameCount</span></span>|<span data-ttu-id="2c4d9-134">Win: UInt32</span><span class="sxs-lookup"><span data-stu-id="2c4d9-134">win:UInt32</span></span>|<span data-ttu-id="2c4d9-135">Počet snímků v trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-135">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="2c4d9-136">Zásobník</span><span class="sxs-lookup"><span data-stu-id="2c4d9-136">Stack</span></span>|<span data-ttu-id="2c4d9-137">Win: ukazatel</span><span class="sxs-lookup"><span data-stu-id="2c4d9-137">win:Pointer</span></span>|<span data-ttu-id="2c4d9-138">Sloupce ukazatelů instrukcí.</span><span class="sxs-lookup"><span data-stu-id="2c4d9-138">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2c4d9-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c4d9-139">See also</span></span>

- [<span data-ttu-id="2c4d9-140">Události ETW CLR</span><span class="sxs-lookup"><span data-stu-id="2c4d9-140">CLR ETW Events</span></span>](clr-etw-events.md)
