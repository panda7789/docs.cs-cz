---
title: AutoResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4ab06993eed4b39746875a6ef3ebfad5edbd2e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33581700"
---
# <a name="autoresetevent"></a><span data-ttu-id="2453d-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="2453d-102">AutoResetEvent</span></span>
<span data-ttu-id="2453d-103"><xref:System.Threading.AutoResetEvent> Třída reprezentuje událost popisovač místní čekání, která automaticky obnoví při signál po vydání jedním vláknem a čekání.</span><span class="sxs-lookup"><span data-stu-id="2453d-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="2453d-104">Tato třída reprezentuje ve speciálním případě její základní třída <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="2453d-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="2453d-105">Najdete v článku [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) rámcová dokumentace pro použití a funkce automatického vynulování události.</span><span class="sxs-lookup"><span data-stu-id="2453d-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="2453d-106"><xref:System.Threading.AutoResetEvent> Objektu se automaticky změní na jiný signál, v systému po vydala jedním vláknem a čekání.</span><span class="sxs-lookup"><span data-stu-id="2453d-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="2453d-107">Pokud nejsou žádná vlákna čekají, zůstane signalizovaného stav události objektu.</span><span class="sxs-lookup"><span data-stu-id="2453d-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="2453d-108"><xref:System.Threading.AutoResetEvent> odpovídá Win32 `CreateEvent` volání, zadání `false` pro `bManualReset` argument.</span><span class="sxs-lookup"><span data-stu-id="2453d-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="2453d-109">Pro příklad, který používá <xref:System.Threading.AutoResetEvent>, najdete v části [monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span><span class="sxs-lookup"><span data-stu-id="2453d-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see [Monitor](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2453d-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="2453d-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="2453d-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="2453d-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="2453d-112">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="2453d-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="2453d-113">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="2453d-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="2453d-114">Obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="2453d-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
