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
ms.openlocfilehash: 7602a61a4403b7ab85015876823aa41e250b23de
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863306"
---
# <a name="autoresetevent"></a><span data-ttu-id="68b2c-102">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="68b2c-102">AutoResetEvent</span></span>
<span data-ttu-id="68b2c-103"><xref:System.Threading.AutoResetEvent> Třída představuje místní čekání popisovač událost, která se automaticky obnoví při signalizován po uvolnění jedno vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="68b2c-103">The <xref:System.Threading.AutoResetEvent> class represents a local wait handle event that resets automatically when signaled, after releasing a single waiting thread.</span></span> <span data-ttu-id="68b2c-104">Tato třída představuje zvláštní případ své základní třídy <xref:System.Threading.EventWaitHandle>.</span><span class="sxs-lookup"><span data-stu-id="68b2c-104">This class represents a special case of its base class, <xref:System.Threading.EventWaitHandle>.</span></span> <span data-ttu-id="68b2c-105">Zobrazit [eventwaithandle –](../../../docs/standard/threading/eventwaithandle.md) rámcové dokumentaci pro použití a funkce automatického resetu událostí.</span><span class="sxs-lookup"><span data-stu-id="68b2c-105">See the [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) conceptual documentation for the use and features of automatic reset events.</span></span>  
  
 <span data-ttu-id="68b2c-106"><xref:System.Threading.AutoResetEvent> Objekt je automaticky obnovit do nesignálového systém po vydala jedno vlákno čekání.</span><span class="sxs-lookup"><span data-stu-id="68b2c-106">An <xref:System.Threading.AutoResetEvent> object is automatically reset to non-signaled by the system after a single waiting thread has been released.</span></span> <span data-ttu-id="68b2c-107">Pokud žádná vlákna čekající, zůstane signalizovaného stavu objektu události.</span><span class="sxs-lookup"><span data-stu-id="68b2c-107">If no threads are waiting, the event object's state remains signaled.</span></span> <span data-ttu-id="68b2c-108"><xref:System.Threading.AutoResetEvent> odpovídá Win32 `CreateEvent` volání, určení `false` pro `bManualReset` argument.</span><span class="sxs-lookup"><span data-stu-id="68b2c-108"><xref:System.Threading.AutoResetEvent> corresponds to a Win32 `CreateEvent` call, specifying `false` for the `bManualReset` argument.</span></span>  
  
 <span data-ttu-id="68b2c-109">Příklad, který používá <xref:System.Threading.AutoResetEvent>, naleznete v tématu <xref:System.Threading.Monitor>.</span><span class="sxs-lookup"><span data-stu-id="68b2c-109">For an example that uses <xref:System.Threading.AutoResetEvent>, see <xref:System.Threading.Monitor>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68b2c-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68b2c-110">See also</span></span>

- <xref:System.Threading.ManualResetEvent>  
- <xref:System.Threading.Monitor>  
- [<span data-ttu-id="68b2c-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span><span class="sxs-lookup"><span data-stu-id="68b2c-111">EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent</span></span>](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [<span data-ttu-id="68b2c-112">Dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="68b2c-112">Threading</span></span>](../../../docs/standard/threading/index.md)  
- [<span data-ttu-id="68b2c-113">Funkce a objekty dělení na vlákna</span><span class="sxs-lookup"><span data-stu-id="68b2c-113">Threading Objects and Features</span></span>](../../../docs/standard/threading/threading-objects-and-features.md)  
- [<span data-ttu-id="68b2c-114">Obslužné rutiny čekání</span><span class="sxs-lookup"><span data-stu-id="68b2c-114">Wait Handles</span></span>](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
