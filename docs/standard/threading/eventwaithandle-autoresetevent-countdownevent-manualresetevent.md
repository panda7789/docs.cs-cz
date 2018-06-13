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
# <a name="eventwaithandle-autoresetevent-countdownevent-manualresetevent"></a>EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent
Obslužné rutiny čekání na událost povolit vláken pro synchronizaci aktivity podle sebe navzájem signalizace a čekání na signály druhé strany. Tyto události synchronizace jsou založená na obslužné rutiny čekání Win32 a je možné rozdělit do dvou typů: ty, které automaticky resetovat při signál a ty, které jsou ručně obnovit.  
  
 Obslužné rutiny čekání na události jsou užitečné v mnoha stejné synchronizace scénáře, jako <xref:System.Threading.Monitor> třídy. Obslužné rutiny čekání na události jsou často jednodušší než <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody a nabízí větší kontrolu nad signalizace. Obslužné rutiny čekání na událost s názvem lze také synchronizovat aktivity napříč doménami aplikací a procesů, zatímco monitorování jsou místní vzhledem k domény aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle> Třída může představovat buď automatické nebo Ruční vynulování události a buď místní události nebo s názvem systémové události.  
  
 [AutoResetEvent](../../../docs/standard/threading/autoresetevent.md)  
 <xref:System.Threading.AutoResetEvent> Třída odvozená z <xref:System.Threading.EventWaitHandle> a představuje místní událost, která automaticky obnoví.  
  
 [ManualResetEvent a ManualResetEventSlim](../../../docs/standard/threading/manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent> Třída odvozená z <xref:System.Threading.EventWaitHandle> a představuje místní události, které je nutné ručně obnovit. <xref:System.Threading.ManualResetEventSlim> Třída je odlehčený, rychlejší verzi, která lze použít pro události v rámci stejného procesu.  
  
 [CountdownEvent](../../../docs/standard/threading/countdownevent.md)  
 <xref:System.Threading.CountdownEvent> Třída poskytuje jednodušší způsob implementace vzorů paralelismus rozvětvení/join v kódu, používá obslužné rutiny čekání.  
  
## <a name="related-sections"></a>Související oddíly  
 [Obslužné rutiny čekání](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
 <xref:System.Threading.WaitHandle> Třída je základní třídu pro <xref:System.Threading.EventWaitHandle>, <xref:System.Threading.Semaphore>, a <xref:System.Threading.Mutex> třídy. Například obsahuje statické metody <xref:System.Threading.WaitHandle.SignalAndWait%2A> a <xref:System.Threading.WaitHandle.WaitAll%2A> , jsou užitečné při práci se všemi typy obslužné rutiny čekání.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Základy dělení na spravovaná vlákna](../../../docs/standard/threading/managed-threading-basics.md)
