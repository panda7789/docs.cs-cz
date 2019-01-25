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
ms.openlocfilehash: 70af739bdb90a70a1319354b4964c261e432912b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729954"
---
# <a name="autoresetevent"></a><span data-ttu-id="39c9a-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="39c9a-102">AutoResetEvent</span></span>
<span data-ttu-id="39c9a-103"><xref:System.Threading.AutoResetEvent> Třída představuje místní čekání popisovač událost, která se automaticky obnoví při signalizován po uvolnění jedno vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="39c9a-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="39c9a-104">Tato třída představuje zvláštní případ své základní třídy <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="39c9a-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="39c9a-105">Zobrazit [eventwaithandle –](../../../docs/standard/threading/eventwaithandle.md) rámcové dokumentaci pro použití a funkce automatického resetu událostí.</span><span class="sxs-lookup"><span data-stu-id="39c9a-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="39c9a-106"><xref:System.Threading.AutoResetEvent> Objekt je automaticky obnovit do nesignálového systém po vydala jedno vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="39c9a-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="39c9a-107">Pokud žádná vlákna čekající, zůstane signalizovaného stavu objektu události.</span><span class="sxs-lookup"><span data-stu-id="39c9a-107">If no threads are waiting, the event object's state remains signaled.</span></span>
  
 <span data-ttu-id="39c9a-108">Příklad, který používá <xref:System.Threading.AutoResetEvent>, naleznete v tématu <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="39c9a-108">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39c9a-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39c9a-109">See also</span></span>

- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [<span data-ttu-id="39c9a-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="39c9a-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
- [<span data-ttu-id="39c9a-111">Práce s vlákny funkce a objekty</span><span class="sxs-lookup"><span data-stu-id="39c9a-111">Threading objects and features</span></span>](threading-objects-and-features.md)
- [<span data-ttu-id="39c9a-112">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="39c9a-112">Threading</span></span>](index.md)
