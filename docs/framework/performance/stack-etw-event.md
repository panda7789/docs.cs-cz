---
title: Událost Trasování událostí pro Windows zásobníku
ms.date: 03/30/2017
helpviewer_keywords:
- stack event [.NET Framework]
- ETW, stack event (CLR)
ms.assetid: f612fa5b-4b62-4593-a19e-85c9b1018dce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7cba2bd1dd5b83e29c7a6c192a1a7e5e2d33ecc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076469"
---
# <a name="stack-etw-event"></a><span data-ttu-id="77131-102">Událost Trasování událostí pro Windows zásobníku</span><span class="sxs-lookup"><span data-stu-id="77131-102">Stack ETW Event</span></span>
<span data-ttu-id="77131-103">Událost zásobníku by měl použít ve spojení s jinými událostmi ke generování trasování zásobníku, poté, co je vyvolána událost.</span><span class="sxs-lookup"><span data-stu-id="77131-103">The stack event should be used in conjunction with other events to generate stack traces after an event is raised.</span></span> <span data-ttu-id="77131-104">Je zaznamenána, pokud je povolen zprostředkovatel běhového prostředí.</span><span class="sxs-lookup"><span data-stu-id="77131-104">It is logged when the runtime provider is enabled.</span></span> <span data-ttu-id="77131-105">To je velmi vysoká frekvence událostí, vzhledem k tomu, že je vyvolána pokaždé, když se jiný modul runtime událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="77131-105">This is a very high frequency event, because it is raised whenever another runtime event is raised.</span></span> <span data-ttu-id="77131-106">Z tohoto důvodu doporučujeme použít tuto událost opatrně.</span><span class="sxs-lookup"><span data-stu-id="77131-106">For this reason, we recommend that you use this event with caution.</span></span>  
  
 <span data-ttu-id="77131-107">V následující tabulce jsou uvedeny klíčové slovo a úroveň.</span><span class="sxs-lookup"><span data-stu-id="77131-107">The following table shows the keyword and level.</span></span> <span data-ttu-id="77131-108">(Další informace najdete v tématu [CLR ETW – klíčová slova a úrovně](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span><span class="sxs-lookup"><span data-stu-id="77131-108">(For more information, see [CLR ETW Keywords and Levels](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)</span></span>  
  
|<span data-ttu-id="77131-109">Klíčové slovo pro vyvolání události</span><span class="sxs-lookup"><span data-stu-id="77131-109">Keyword for raising the event</span></span>|<span data-ttu-id="77131-110">úroveň</span><span class="sxs-lookup"><span data-stu-id="77131-110">Level</span></span>|  
|-----------------------------------|-----------|  
|<span data-ttu-id="77131-111">`StackKeyword` (0x40000000)</span><span class="sxs-lookup"><span data-stu-id="77131-111">`StackKeyword` (0x40000000)</span></span>|<span data-ttu-id="77131-112">LogAlways(0)</span><span class="sxs-lookup"><span data-stu-id="77131-112">LogAlways(0)</span></span>|  
  
 <span data-ttu-id="77131-113">V následující tabulce jsou uvedeny informace o události.</span><span class="sxs-lookup"><span data-stu-id="77131-113">The following table shows the event information.</span></span>  
  
|<span data-ttu-id="77131-114">Událost</span><span class="sxs-lookup"><span data-stu-id="77131-114">Event</span></span>|<span data-ttu-id="77131-115">ID události</span><span class="sxs-lookup"><span data-stu-id="77131-115">Event ID</span></span>|<span data-ttu-id="77131-116">Vyvolá se, když</span><span class="sxs-lookup"><span data-stu-id="77131-116">Raised when</span></span>|  
|-----------|--------------|-----------------|  
|`CLRStackWalk`|<span data-ttu-id="77131-117">82</span><span class="sxs-lookup"><span data-stu-id="77131-117">82</span></span>|<span data-ttu-id="77131-118">Ve spojení s jinými událostmi generovat následující událost trasování zásobníku.</span><span class="sxs-lookup"><span data-stu-id="77131-118">In conjunction with other events to generate stack traces following an event.</span></span>|  
  
 <span data-ttu-id="77131-119">Následující tabulka zobrazuje data událostí.</span><span class="sxs-lookup"><span data-stu-id="77131-119">The following table shows the event data.</span></span>  
  
|<span data-ttu-id="77131-120">Název pole</span><span class="sxs-lookup"><span data-stu-id="77131-120">Field name</span></span>|<span data-ttu-id="77131-121">Datový typ</span><span class="sxs-lookup"><span data-stu-id="77131-121">Data Type</span></span>|<span data-ttu-id="77131-122">Popis</span><span class="sxs-lookup"><span data-stu-id="77131-122">Description</span></span>|  
|----------------|---------------|-----------------|  
|<span data-ttu-id="77131-123">ClrInstanceID</span><span class="sxs-lookup"><span data-stu-id="77131-123">ClrInstanceID</span></span>|<span data-ttu-id="77131-124">Windows: Uint16</span><span class="sxs-lookup"><span data-stu-id="77131-124">win:Uint16</span></span>|<span data-ttu-id="77131-125">Identifikátor modulu runtime jedinečný.</span><span class="sxs-lookup"><span data-stu-id="77131-125">Unique runtime identifier.</span></span>|  
|<span data-ttu-id="77131-126">Reserved1</span><span class="sxs-lookup"><span data-stu-id="77131-126">Reserved1</span></span>|<span data-ttu-id="77131-127">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="77131-127">win:UInt8</span></span>|<span data-ttu-id="77131-128">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="77131-128">Reserved.</span></span>|  
|<span data-ttu-id="77131-129">Vyhrazeno2</span><span class="sxs-lookup"><span data-stu-id="77131-129">Reserved2</span></span>|<span data-ttu-id="77131-130">win:UInt8</span><span class="sxs-lookup"><span data-stu-id="77131-130">win:UInt8</span></span>|<span data-ttu-id="77131-131">Vyhrazená.</span><span class="sxs-lookup"><span data-stu-id="77131-131">Reserved.</span></span>|  
|<span data-ttu-id="77131-132">Hodnoty FrameCount</span><span class="sxs-lookup"><span data-stu-id="77131-132">FrameCount</span></span>|<span data-ttu-id="77131-133">win:UInt32</span><span class="sxs-lookup"><span data-stu-id="77131-133">win:UInt32</span></span>|<span data-ttu-id="77131-134">Počet rámců v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="77131-134">The number of frames in the stack trace.</span></span>|  
|<span data-ttu-id="77131-135">Rámec</span><span class="sxs-lookup"><span data-stu-id="77131-135">Stack</span></span>|<span data-ttu-id="77131-136">win:Pointer</span><span class="sxs-lookup"><span data-stu-id="77131-136">win:Pointer</span></span>|<span data-ttu-id="77131-137">Sloupce ukazatele na instrukce.</span><span class="sxs-lookup"><span data-stu-id="77131-137">Columns of instruction pointers.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="77131-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77131-138">See also</span></span>

- [<span data-ttu-id="77131-139">Události Trasování událostí pro Windows v CLR</span><span class="sxs-lookup"><span data-stu-id="77131-139">CLR ETW Events</span></span>](../../../docs/framework/performance/clr-etw-events.md)
