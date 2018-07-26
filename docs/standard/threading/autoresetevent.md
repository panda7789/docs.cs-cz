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
ms.openlocfilehash: c1785ce223f0dcd4da7ea6ef9fa3a3e897a39dca
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143515"
---
# <a name="autoresetevent"></a><span data-ttu-id="3f3dd-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="3f3dd-102">AutoResetEvent</span></span>
<span data-ttu-id="3f3dd-103"><xref:System.Threading.AutoResetEvent> Třída představuje místní čekání popisovač událost, která se automaticky obnoví při signalizován po uvolnění jedno vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="3f3dd-104">Tato třída představuje zvláštní případ své základní třídy <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="3f3dd-105">Zobrazit [eventwaithandle –](../../../docs/standard/threading/eventwaithandle.md) rámcové dokumentaci pro použití a funkce automatického resetu událostí.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="3f3dd-106"><xref:System.Threading.AutoResetEvent> Objekt je automaticky obnovit do nesignálového systém po vydala jedno vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="3f3dd-107">Pokud žádná vlákna čekající, zůstane signalizovaného stavu objektu události.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="3f3dd-108"><xref:System.Threading.AutoResetEvent> odpovídá Win32 `CreateEvent` volání, určení `false` pro `bManualReset` argument.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="3f3dd-109">Příklad, který používá <xref:System.Threading.AutoResetEvent>, naleznete v tématu <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="3f3dd-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f3dd-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f3dd-110">See Also</span></span>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="3f3dd-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="3f3dd-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [<span data-ttu-id="3f3dd-112">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3f3dd-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
 [<span data-ttu-id="3f3dd-113">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="3f3dd-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
 [<span data-ttu-id="3f3dd-114">Obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="3f3dd-114">Wait Handles</span></span>](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
