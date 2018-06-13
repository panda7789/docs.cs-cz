---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 543853f581436a5fb7e5c897012b99bef20dc289
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33582931"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="2215a-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="2215a-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="2215a-103">Obslužné rutiny čekání na událost povolit vláken pro synchronizaci aktivity podle sebe navzájem signalizace a čekání na signály druhé strany.</span><span class="sxs-lookup"><span data-stu-id="2215a-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="2215a-104">Tyto události synchronizace jsou založená na obslužné rutiny čekání Win32 a je možné rozdělit do dvou typů: ty, které automaticky resetovat při signál a ty, které jsou ručně obnovit.</span><span class="sxs-lookup"><span data-stu-id="2215a-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="2215a-105">Obslužné rutiny čekání na události jsou užitečné v mnoha stejné synchronizace scénáře, jako <xref:System.Threading.Monitor> třídy.</span><span class="sxs-lookup"><span data-stu-id="2215a-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="2215a-106">Obslužné rutiny čekání na události jsou často jednodušší než <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody a nabízí větší kontrolu nad signalizace.</span><span class="sxs-lookup"><span data-stu-id="2215a-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="2215a-107">Obslužné rutiny čekání na událost s názvem lze také synchronizovat aktivity napříč doménami aplikací a procesů, zatímco monitorování jsou místní vzhledem k domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="2215a-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2215a-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2215a-108">In This Section</span></span>  
 [<span data-ttu-id="2215a-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="2215a-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="2215a-110"><xref:System.Threading.EventWaitHandle> Třída může představovat buď automatické nebo Ruční vynulování události a buď místní události nebo s názvem systémové události.</span><span class="sxs-lookup"><span data-stu-id="2215a-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="2215a-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="2215a-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="2215a-112"><xref:System.Threading.AutoResetEvent> Třída odvozená z <xref:System.Threading.EventWaitHandle> a představuje místní událost, která automaticky obnoví.</span><span class="sxs-lookup"><span data-stu-id="2215a-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="2215a-113">ManualResetEvent a ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="2215a-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="2215a-114"><xref:System.Threading.ManualResetEvent> Třída odvozená z <xref:System.Threading.EventWaitHandle> a představuje místní události, které je nutné ručně obnovit.</span><span class="sxs-lookup"><span data-stu-id="2215a-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="2215a-115"><xref:System.Threading.ManualResetEventSlim> Třída je odlehčený, rychlejší verzi, která lze použít pro události v rámci stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="2215a-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="2215a-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="2215a-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="2215a-117"><xref:System.Threading.CountdownEvent> Třída poskytuje jednodušší způsob implementace vzorů paralelismus rozvětvení/join v kódu, používá obslužné rutiny čekání.</span><span class="sxs-lookup"><span data-stu-id="2215a-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2215a-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2215a-118">Related Sections</span></span>  
 [<span data-ttu-id="2215a-119">Obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="2215a-119">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="2215a-120"><xref:System.Threading.WaitHandle> Třída je základní třídu pro <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, a <xref:System.Threading.Mutex> třídy.</span><span class="sxs-lookup"><span data-stu-id="2215a-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="2215a-121">Například obsahuje statické metody <xref:System.Threading.WaitHandle.SignalAndWait%2A> a <xref:System.Threading.WaitHandle.WaitAll%2A> , jsou užitečné při práci se všemi typy obslužné rutiny čekání.</span><span class="sxs-lookup"><span data-stu-id="2215a-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2215a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="2215a-122">See Also</span></span>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [<span data-ttu-id="2215a-123">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="2215a-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="2215a-124">Základy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="2215a-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
