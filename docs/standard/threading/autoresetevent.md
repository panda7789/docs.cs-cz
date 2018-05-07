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
ms.openlocfilehash: a4ab06993eed4b39746875a6ef3ebfad5edbd2e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Třída reprezentuje událost popisovač místní čekání, která automaticky obnoví při signál po vydání jedním vláknem a čekání. Tato třída reprezentuje ve speciálním případě její základní třída <xref:System.Threading.EventWaitHandle>. Najdete v článku [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) rámcová dokumentace pro použití a funkce automatického vynulování události.  
  
 <xref:System.Threading.AutoResetEvent> Objektu se automaticky změní na jiný signál, v systému po vydala jedním vláknem a čekání. Pokud nejsou žádná vlákna čekají, zůstane signalizovaného stav události objektu. <xref:System.Threading.AutoResetEvent> odpovídá Win32 `CreateEvent` volání, zadání `false` pro `bManualReset` argument.  
  
 Pro příklad, který používá <xref:System.Threading.AutoResetEvent>, najdete v části [monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Obslužné rutiny čekání](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
