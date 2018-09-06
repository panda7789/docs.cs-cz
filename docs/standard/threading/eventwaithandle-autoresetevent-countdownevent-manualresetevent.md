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
ms.openlocfilehash: 2f61e614696e731a85a030e34aa4356137d9000d
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43882344"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="05222-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="05222-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>
<span data-ttu-id="05222-103">Obslužné rutiny události čekání povolit vláken pro synchronizaci činností signalizace mezi sebou a čeká se na druhé strany signálů.</span><span class="sxs-lookup"><span data-stu-id="05222-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="05222-104">Tyto události synchronizace jsou založené na Win32 obslužné rutiny čekání a je možné rozdělit do dvou typů: ty, které obnovit automaticky, když se signál a ty, které jsou ručně obnovit.</span><span class="sxs-lookup"><span data-stu-id="05222-104">These synchronization events are based on Win32 wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
 <span data-ttu-id="05222-105">Obslužné rutiny čekání události jsou užitečné v mnoha stejné synchronizačních scénářů, jako <xref:System.Threading.Monitor> třídy.</span><span class="sxs-lookup"><span data-stu-id="05222-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="05222-106">Obslužné rutiny čekání události jsou často jednodušší než <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody a nabízí větší kontrolu nad signalizace.</span><span class="sxs-lookup"><span data-stu-id="05222-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="05222-107">Obslužné rutiny čekání pojmenované události lze také synchronizovat aktivity napříč doménami aplikace a procesy, že monitorování jsou místní vůči doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="05222-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05222-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="05222-108">In This Section</span></span>  
 [<span data-ttu-id="05222-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="05222-109">EventWaitHandle</span></span>](../../../docs/standard/threading/eventwaithandle.md)  
 <span data-ttu-id="05222-110"><xref:System.Threading.EventWaitHandle> Může představovat buď automatické nebo ruční resetování buď místní události a události nebo pojmenována jako událost systému.</span><span class="sxs-lookup"><span data-stu-id="05222-110">The <xref:System.Threading.EventWaitHandle> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="05222-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="05222-111">AutoResetEvent</span></span>](../../../docs/standard/threading/autoresetevent.md)  
 <span data-ttu-id="05222-112"><xref:System.Threading.AutoResetEvent> Třída odvozena z <xref:System.Threading.EventWaitHandle> a představuje místní události, které se automaticky obnoví.</span><span class="sxs-lookup"><span data-stu-id="05222-112">The <xref:System.Threading.AutoResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="05222-113">ManualResetEvent a ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="05222-113">ManualResetEvent and ManualResetEventSlim</span></span>](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="05222-114"><xref:System.Threading.ManualResetEvent> Třída odvozena z <xref:System.Threading.EventWaitHandle> a představuje místní událost, která musí být v továrním ručně.</span><span class="sxs-lookup"><span data-stu-id="05222-114">The <xref:System.Threading.ManualResetEvent> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="05222-115"><xref:System.Threading.ManualResetEventSlim> Třída je jednoduché a rychlejší verzi, která lze použít pro události v rámci stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="05222-115">The <xref:System.Threading.ManualResetEventSlim> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="05222-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="05222-116">CountdownEvent</span></span>](../../../docs/standard/threading/countdownevent.md)  
 <span data-ttu-id="05222-117"><xref:System.Threading.CountdownEvent> Třída poskytuje zjednodušený způsob, jak implementovat rozvětvení/spojení paralelismu vzorů v kódu, že používá obslužné rutiny čekání.</span><span class="sxs-lookup"><span data-stu-id="05222-117">The <xref:System.Threading.CountdownEvent> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="05222-118">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="05222-118">Related Sections</span></span>  
 [<span data-ttu-id="05222-119">Obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="05222-119">Wait Handles</span></span>](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <span data-ttu-id="05222-120"><xref:System.Threading.WaitHandle> Třída je základní třídou pro <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, a <xref:System.Threading.Mutex> třídy.</span><span class="sxs-lookup"><span data-stu-id="05222-120">The <xref:System.Threading.WaitHandle> class is the base class for the <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, and <xref:System.Threading.Mutex> classes.</span></span> <span data-ttu-id="05222-121">Obsahuje statické metody, jako <xref:System.Threading.WaitHandle.SignalAndWait%2A> a <xref:System.Threading.WaitHandle.WaitAll%2A> , které jsou užitečné při práci se všemi typy obslužné rutiny čekání.</span><span class="sxs-lookup"><span data-stu-id="05222-121">It contains static methods such as <xref:System.Threading.WaitHandle.SignalAndWait%2A> and <xref:System.Threading.WaitHandle.WaitAll%2A> that are useful when working with all types of wait handles.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05222-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05222-122">See also</span></span>

- <xref:System.Threading.EventWaitHandle>  
- <xref:System.Threading.WaitHandle>  
- <xref:System.Threading.AutoResetEvent>  
- <xref:System.Threading.ManualResetEvent>  
- [<span data-ttu-id="05222-123">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="05222-123">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
- [<span data-ttu-id="05222-124">Základy dělení na spravovaná vlákna</span><span class="sxs-lookup"><span data-stu-id="05222-124">Managed Threading Basics</span></span>](../../../docs/standard/threading/managed-threading-basics.md)
