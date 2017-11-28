---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a><span data-ttu-id="ba6ce-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="ba6ce-102">AutoResetEvent</span></span>
<span data-ttu-id="ba6ce-103"><xref:System.Threading.AutoResetEvent> Třída reprezentuje událost popisovač místní čekání, která automaticky obnoví při signál po vydání jedním vláknem a čekání.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="ba6ce-104">Tato třída reprezentuje ve speciálním případě její základní třída <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="ba6ce-105">Najdete v článku [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) rámcová dokumentace pro použití a funkce automatického vynulování události.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="ba6ce-106"><xref:System.Threading.AutoResetEvent> Objektu se automaticky změní na jiný signál, v systému po vydala jedním vláknem a čekání.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="ba6ce-107">Pokud nejsou žádná vlákna čekají, zůstane signalizovaného stav události objektu.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="ba6ce-108"><xref:System.Threading.AutoResetEvent>odpovídá Win32 `CreateEvent` volání, zadání `false` pro `bManualReset` argument.</span><span class="sxs-lookup"><span data-stu-id="ba6ce-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="ba6ce-109">Pro příklad, který používá <xref:System.Threading.AutoResetEvent>, najdete v části [monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span><span class="sxs-lookup"><span data-stu-id="ba6ce-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba6ce-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba6ce-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="ba6ce-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="ba6ce-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="ba6ce-112">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="ba6ce-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="ba6ce-113">Dělení na vlákna objektů a funkcí</span><span class="sxs-lookup"><span data-stu-id="ba6ce-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="ba6ce-114">Obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="ba6ce-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
