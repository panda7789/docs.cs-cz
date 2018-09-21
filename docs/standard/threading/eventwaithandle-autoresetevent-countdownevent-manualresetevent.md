---
title: EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: be9c858d7c76fdcc1b3e02485eb0b459f4e7555c
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46519260"
---
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a><span data-ttu-id="93987-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="93987-102">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>

<span data-ttu-id="93987-103">Obslužné rutiny události čekání povolit vláken pro synchronizaci činností signalizace mezi sebou a čeká se na druhé strany signálů.</span><span class="sxs-lookup"><span data-stu-id="93987-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="93987-104">Tyto události synchronizace jsou založeny na obslužné rutiny čekání operačního systému a je možné rozdělit do dvou typů: ty, které obnovit automaticky, když se signál a ty, které jsou ručně obnovit.</span><span class="sxs-lookup"><span data-stu-id="93987-104">These synchronization events are based on operating system wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
<span data-ttu-id="93987-105">Obslužné rutiny čekání události jsou užitečné v mnoha stejné synchronizačních scénářů, jako <xref:System.Threading.Monitor> třídy.</span><span class="sxs-lookup"><span data-stu-id="93987-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="93987-106">Obslužné rutiny čekání události jsou často jednodušší než <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody a nabízí větší kontrolu nad signalizace.</span><span class="sxs-lookup"><span data-stu-id="93987-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="93987-107">Obslužné rutiny čekání pojmenované události lze také synchronizovat aktivity napříč doménami aplikace a procesy, že monitorování jsou místní vůči doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="93987-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="93987-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="93987-108">In this section</span></span>

 [<span data-ttu-id="93987-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="93987-109">EventWaitHandle</span></span>](eventwaithandle.md)  
 <span data-ttu-id="93987-110"><xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Může představovat buď automatické nebo ruční resetování buď místní události a události nebo pojmenována jako událost systému.</span><span class="sxs-lookup"><span data-stu-id="93987-110">The <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="93987-111">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="93987-111">AutoResetEvent</span></span>](autoresetevent.md)  
 <span data-ttu-id="93987-112"><xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> Třída odvozena z <xref:System.Threading.EventWaitHandle> a představuje místní události, které se automaticky obnoví.</span><span class="sxs-lookup"><span data-stu-id="93987-112">The <xref:System.Threading.AutoResetEvent?displayProperty=nameWithType> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that resets automatically.</span></span>  
  
 [<span data-ttu-id="93987-113">ManualResetEvent a ManualResetEventSlim</span><span class="sxs-lookup"><span data-stu-id="93987-113">ManualResetEvent and ManualResetEventSlim</span></span>](manualresetevent-and-manualreseteventslim.md)  
 <span data-ttu-id="93987-114"><xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída odvozena z <xref:System.Threading.EventWaitHandle> a představuje místní událost, která musí být v továrním ručně.</span><span class="sxs-lookup"><span data-stu-id="93987-114">The <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> class derives from <xref:System.Threading.EventWaitHandle> and represents a local event that must be reset manually.</span></span> <span data-ttu-id="93987-115"><xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> Třída je jednoduché a rychlejší verzi, která lze použít pro události v rámci stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="93987-115">The <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> class is a lightweight, faster version that can be used for events within the same process.</span></span>  
  
 [<span data-ttu-id="93987-116">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="93987-116">CountdownEvent</span></span>](countdownevent.md)  
 <span data-ttu-id="93987-117"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Třída poskytuje zjednodušený způsob, jak implementovat rozvětvení/spojení paralelismu vzorů v kódu, že používá obslužné rutiny čekání.</span><span class="sxs-lookup"><span data-stu-id="93987-117">The <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  

## <a name="see-also"></a><span data-ttu-id="93987-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93987-118">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [<span data-ttu-id="93987-119">Práce s vlákny funkce a objekty</span><span class="sxs-lookup"><span data-stu-id="93987-119">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="93987-120">Dělení na spravovaná vlákna základy</span><span class="sxs-lookup"><span data-stu-id="93987-120">Managed threading basics</span></span>](managed-threading-basics.md)
