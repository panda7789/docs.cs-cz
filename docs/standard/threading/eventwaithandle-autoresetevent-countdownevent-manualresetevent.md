---
title: Eventwaithandle – CountdownEvent
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fafdc2a360038021217d9a42406c971b1094678b
ms.sourcegitcommit: dcc8feeff4718664087747529638ec9b47e65234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/31/2019
ms.locfileid: "55479929"
---
# <a name="eventwaithandle-countdownevent"></a><span data-ttu-id="3255f-102">Eventwaithandle – CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="3255f-102">EventWaitHandle, CountdownEvent</span></span>

<span data-ttu-id="3255f-103">Obslužné rutiny události čekání povolit vláken pro synchronizaci činností signalizace mezi sebou a čeká se na druhé strany signálů.</span><span class="sxs-lookup"><span data-stu-id="3255f-103">Event wait handles allow threads to synchronize activities by signaling each other and by waiting on each other's signals.</span></span> <span data-ttu-id="3255f-104">Tyto události synchronizace jsou založeny na obslužné rutiny čekání operačního systému a je možné rozdělit do dvou typů: ty, které obnovit automaticky, když se signál a ty, které jsou ručně obnovit.</span><span class="sxs-lookup"><span data-stu-id="3255f-104">These synchronization events are based on operating system wait handles and can be divided into two types: those that reset automatically when signaled and those that are reset manually.</span></span>  
  
<span data-ttu-id="3255f-105">Obslužné rutiny čekání události jsou užitečné v mnoha stejné synchronizačních scénářů, jako <xref:System.Threading.Monitor> třídy.</span><span class="sxs-lookup"><span data-stu-id="3255f-105">Event wait handles are useful in many of the same synchronization scenarios as the <xref:System.Threading.Monitor> class.</span></span> <span data-ttu-id="3255f-106">Obslužné rutiny čekání události jsou často jednodušší než <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody a nabízí větší kontrolu nad signalizace.</span><span class="sxs-lookup"><span data-stu-id="3255f-106">Event wait handles are often easier to use than the <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> and <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> methods, and they offer more control over signaling.</span></span> <span data-ttu-id="3255f-107">Obslužné rutiny čekání pojmenované události lze také synchronizovat aktivity napříč doménami aplikace a procesy, že monitorování jsou místní vůči doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="3255f-107">Named event wait handles can also be used to synchronize activities across application domains and processes, whereas monitors are local to an application domain.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3255f-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3255f-108">In this section</span></span>

 [<span data-ttu-id="3255f-109">EventWaitHandle</span><span class="sxs-lookup"><span data-stu-id="3255f-109">EventWaitHandle</span></span>](eventwaithandle.md)  
 <span data-ttu-id="3255f-110"><xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Může představovat buď automatické nebo ruční resetování buď místní události a události nebo pojmenována jako událost systému.</span><span class="sxs-lookup"><span data-stu-id="3255f-110">The <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> class can represent either automatic or manual reset events and either local events or named system events.</span></span>  
  
 [<span data-ttu-id="3255f-111">CountdownEvent</span><span class="sxs-lookup"><span data-stu-id="3255f-111">CountdownEvent</span></span>](countdownevent.md)  
 <span data-ttu-id="3255f-112"><xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Třída poskytuje zjednodušený způsob, jak implementovat rozvětvení/spojení paralelismu vzorů v kódu, že používá obslužné rutiny čekání.</span><span class="sxs-lookup"><span data-stu-id="3255f-112">The <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> class provides a simplified way to implement fork/join parallelism patterns in code that uses wait handles.</span></span>  

## <a name="see-also"></a><span data-ttu-id="3255f-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3255f-113">See also</span></span>

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [<span data-ttu-id="3255f-114">Práce s vlákny funkce a objekty</span><span class="sxs-lookup"><span data-stu-id="3255f-114">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="3255f-115">Dělení na spravovaná vlákna základy</span><span class="sxs-lookup"><span data-stu-id="3255f-115">Managed threading basics</span></span>](managed-threading-basics.md)
