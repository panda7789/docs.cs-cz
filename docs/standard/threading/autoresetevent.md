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
ms.openlocfilehash: 519776b5c1c237deb520476384495b8dd96a4e39
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039280"
---
# <a name="autoresetevent"></a><span data-ttu-id="a09ba-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="a09ba-102">AutoResetEvent</span></span>
<span data-ttu-id="a09ba-103"><xref:System.Threading.AutoResetEvent> Třída představuje místní čekání popisovač událost, která se automaticky obnoví při signalizován po uvolnění jedno vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="a09ba-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="a09ba-104">Tato třída představuje zvláštní případ své základní třídy <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="a09ba-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="a09ba-105">Zobrazit [eventwaithandle –](../../../docs/standard/threading/eventwaithandle.md) rámcové dokumentaci pro použití a funkce automatického resetu událostí.</span><span class="sxs-lookup"><span data-stu-id="a09ba-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="a09ba-106"><xref:System.Threading.AutoResetEvent> Objekt je automaticky obnovit do nesignálového systém po vydala jedno vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="a09ba-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="a09ba-107">Pokud žádná vlákna čekající, zůstane signalizovaného stavu objektu události.</span><span class="sxs-lookup"><span data-stu-id="a09ba-107">If no threads are waiting, the event object's state remains signaled.</span></span>
  
 <span data-ttu-id="a09ba-108">Příklad, který používá <xref:System.Threading.AutoResetEvent>, naleznete v tématu <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="a09ba-108">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a09ba-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a09ba-109">See also</span></span>

- <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>
- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- [<span data-ttu-id="a09ba-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="a09ba-110">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [<span data-ttu-id="a09ba-111">Práce s vlákny funkce a objekty</span><span class="sxs-lookup"><span data-stu-id="a09ba-111">Threading objects and features</span></span>](threading-objects-and-features.md)  
- [<span data-ttu-id="a09ba-112">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="a09ba-112">Threading</span></span>](index.md)  
