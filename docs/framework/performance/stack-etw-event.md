---
title: Událost Trasování událostí pro Windows zásobníku
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b0cb166f2753b910465aabb8abd68c31c6f56ff8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497535"
---
# <a name="stack-etw-event"></a><span data-ttu-id="91710-102">Událost Trasování událostí pro Windows zásobníku</span><span class="sxs-lookup"><span data-stu-id="91710-102">Stack ETW Event</span></span>
<span data-ttu-id="91710-103">Událost zásobníku by měl použít ve spojení s jinými událostmi ke generování trasování zásobníku, poté, co je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="91710-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="91710-104">Je zaznamenána, pokud je povolen zprostředkovatel běhového prostředí.</span><span class="sxs-lookup"><span data-stu-id="91710-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="91710-105">To je velmi vysoká frekvence událostí, vzhledem k tomu, že je vyvolána pokaždé, když se jiný modul runtime událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="91710-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="91710-106">Z tohoto důvodu doporučujeme použít tuto událost opatrně.</span><span class="sxs-lookup"><span data-stu-id="91710-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="91710-107">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="91710-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="91710-108">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="91710-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="91710-109">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="91710-109">Keyword for raising the event</span></span>|<span data-ttu-id="91710-110">úroveň</span><span class="sxs-lookup"><span data-stu-id="91710-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="91710-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="91710-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="91710-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="91710-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="91710-113">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="91710-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="91710-114">Událost</span><span class="sxs-lookup"><span data-stu-id="91710-114">Event</span></span>|<span data-ttu-id="91710-115">ID události</span><span class="sxs-lookup"><span data-stu-id="91710-115">Event ID</span></span>|<span data-ttu-id="91710-116">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="91710-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="91710-117">82</span><span class="sxs-lookup"><span data-stu-id="91710-117">82</span></span>|<span data-ttu-id="91710-118">Ve spojení s jinými událostmi generovat následující událost trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="91710-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="91710-119">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="91710-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="91710-120">Název pole</span><span class="sxs-lookup"><span data-stu-id="91710-120">Field name</span></span>|<span data-ttu-id="91710-121">Datový typ</span><span class="sxs-lookup"><span data-stu-id="91710-121">Data Type</span></span>|<span data-ttu-id="91710-122">Popis</span><span class="sxs-lookup"><span data-stu-id="91710-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="91710-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="91710-123">ClrInstanceID</span></span>|<span data-ttu-id="91710-124">Windows: Uint16</span><span class="sxs-lookup"><span data-stu-id="91710-124">win:Uint16</span></span>|<span data-ttu-id="91710-125">Identifikátor modulu runtime jedinečný.</span><span class="sxs-lookup"><span data-stu-id="91710-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="91710-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="91710-126">Reserved1</span></span>|<span data-ttu-id="91710-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="91710-127">win:UInt8</span></span>|<span data-ttu-id="91710-128">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="91710-128">Reserved.</span></span>|  
|<span data-ttu-id="91710-129">Vyhrazeno2</span><span class="sxs-lookup"><span data-stu-id="91710-129">Reserved2</span></span>|<span data-ttu-id="91710-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="91710-130">win:UInt8</span></span>|<span data-ttu-id="91710-131">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="91710-131">Reserved.</span></span>|  
|<span data-ttu-id="91710-132">Hodnoty FrameCount</span><span class="sxs-lookup"><span data-stu-id="91710-132">FrameCount</span></span>|<span data-ttu-id="91710-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="91710-133">win:UInt32</span></span>|<span data-ttu-id="91710-134">Počet rámců v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="91710-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="91710-135">Rámec</span><span class="sxs-lookup"><span data-stu-id="91710-135">Stack</span></span>|<span data-ttu-id="91710-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="91710-136">win:Pointer</span></span>|<span data-ttu-id="91710-137">Sloupce ukazatele na instrukce.</span><span class="sxs-lookup"><span data-stu-id="91710-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="91710-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91710-138">See also</span></span>
- [<span data-ttu-id="91710-139">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="91710-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
