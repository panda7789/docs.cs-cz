---
title: AutoResetEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- threading [.NET Framework], AutoResetEvent class
- AutoResetEvent class
ms.assetid: 6d39c48d-6b37-4a9b-8631-f2924cfd9c18
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 69d16e8c6491b4c66ab5a5452762e73172ebbb77
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="autoresetevent"></a>AutoResetEvent
<xref:System.Threading.AutoResetEvent> Třída reprezentuje událost popisovač místní čekání, která automaticky obnoví při signál po vydání jedním vláknem a čekání. Tato třída reprezentuje ve speciálním případě její základní třída <xref:System.Threading.EventWaitHandle>. Najdete v článku [EventWaitHandle](../../../docs/standard/threading/eventwaithandle.md) rámcová dokumentace pro použití a funkce automatického vynulování události.  
  
 <xref:System.Threading.AutoResetEvent> Objektu se automaticky změní na jiný signál, v systému po vydala jedním vláknem a čekání. Pokud nejsou žádná vlákna čekají, zůstane signalizovaného stav události objektu. <xref:System.Threading.AutoResetEvent>odpovídá Win32 `CreateEvent` volání, zadání `false` pro `bManualReset` argument.  
  
 Pro příklad, který používá <xref:System.Threading.AutoResetEvent>, najdete v části [monitorování](http://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Monitor>  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
 [Dělení na vlákna](../../../docs/standard/threading/index.md)  
 [Dělení na vlákna objektů a funkcí](../../../docs/standard/threading/threading-objects-and-features.md)  
 [Obslužné rutiny čekání](http://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)
