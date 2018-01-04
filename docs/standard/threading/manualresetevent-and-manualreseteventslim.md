---
title: ManualResetEvent a ManualResetEventSlim
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], ManualResetEvent class
- ManualResetEvent class, about ManualResetEvent class
ms.assetid: 465fdcf9-ba24-4d8d-a43f-d983b7cb0cc6
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b90a84cf87c6c64d48d89840e2213d83b2e39d44
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="manualresetevent-and-manualreseteventslim"></a><span data-ttu-id="3bbe8-102">ManualResetEvent a ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="3bbe8-102">ManualResetEvent and ManualResetEventSlim</span></span>
<span data-ttu-id="3bbe8-103"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída reprezentuje událost popisovač místní čekání, která musí být ručně obnovit, jakmile to bylo signalizováno.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-103">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class represents a local wait handle event that must be reset manually after it is signaled.</span></span> <span data-ttu-id="3bbe8-104">Tato třída reprezentuje ve speciálním případě její základní třída <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType>.</span></span> <span data-ttu-id="3bbe8-105">Najdete v článku [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) rámcová dokumentace pro použití a funkce ručně resetovat události.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of manual reset events.</span></span>  
  
 <span data-ttu-id="3bbe8-106">A <xref:System.Threading.ManualResetEvent> objekt zůstane signalizovaného dokud jeho <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-106">A <xref:System.Threading.ManualResetEvent> object remains signaled until its <xref:System.Threading.EventWaitHandle.Reset%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="3bbe8-107">Libovolný počet čekajících vláken nebo vláken, která čekat na události po byla signál, můžete vydala, zatímco signalizace stav objektu.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-107">Any number of waiting threads, or threads that wait on the event after it has been signaled, can be released while the object's state is signaled.</span></span> <span data-ttu-id="3bbe8-108"><xref:System.Threading.ManualResetEvent>odpovídá Win32 `CreateEvent` volání, zadání `true` pro `bManualReset` argument.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-108"><xref:System.Threading.ManualResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `true` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="3bbe8-109">V [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], můžete použít <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> třídy pro lepší výkon, pokud očekávané velmi krátké době čekání a pokud událost nekříží hranice procesu.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-109">In the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], you can use the <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class for better performance when wait times are expected to be very short, and when the event does not cross a process boundary.</span></span> <span data-ttu-id="3bbe8-110"><xref:System.Threading.ManualResetEventSlim>používá zaneprázdněn otáčí po krátkou dobu, kdy čeká stát signál události.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-110"><xref:System.Threading.ManualResetEventSlim> uses busy spinning for a short time while it waits for the event to become signaled.</span></span> <span data-ttu-id="3bbe8-111">Po krátkou dobu čekání se může být roztočený mnohem míň nákladné než čekání pomocí obslužných rutin čekání.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-111">When wait times are short, spinning can be much less expensive than waiting by using wait handles.</span></span> <span data-ttu-id="3bbe8-112">Ale pokud událost stane signál není v rámci určité doby běhu <xref:System.Threading.ManualResetEventSlim> používat popisovač čekání pravidelné události.</span><span class="sxs-lookup"><span data-stu-id="3bbe8-112">However, if the event does not become signaled within a certain period of time, <xref:System.Threading.ManualResetEventSlim> resorts to a regular event handle wait.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bbe8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bbe8-113">See Also</span></span>  
 [<span data-ttu-id="3bbe8-114">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3bbe8-114">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="3bbe8-115">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3bbe8-115">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="3bbe8-116">Obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="3bbe8-116">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 [<span data-ttu-id="3bbe8-117">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="3bbe8-117">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 [<span data-ttu-id="3bbe8-118">SpinWait</span><span class="sxs-lookup"><span data-stu-id="3bbe8-118">SpinWait</span></span>](../../../docs/standard/threading/spinwait.md)  
 [<span data-ttu-id="3bbe8-119">Semaphore a SemaphoreSlim</span><span class="sxs-lookup"><span data-stu-id="3bbe8-119">Semaphore and SemaphoreSlim</span></span>](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)
