---
title: CountdownEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9f953f6477abf1f4e0d6aaf79e67005172ff1144
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>je synchronizace primitivní, který odblokuje jeho vláken čekání po jejím signalizovala stanovený počet. <xref:System.Threading.CountdownEvent>je určen pro scénáře, ve kterých by jinak musíte použít <xref:System.Threading.ManualResetEvent> nebo <xref:System.Threading.ManualResetEventSlim> a ručně snížení proměnné před signalizace události. Například v případě rozvětvení/spojení právě vytvořením <xref:System.Threading.CountdownEvent> má signál počet 5, a poté spuštění pět pracovních položek ve vlákně fondu a mít každý pracovní položka volání <xref:System.Threading.CountdownEvent.Signal%2A> po dokončení operace. Každé volání <xref:System.Threading.CountdownEvent.Signal%2A> snižuje počet signál o 1. Na hlavní vlákno volání <xref:System.Threading.CountdownEvent.Wait%2A> se zablokuje, dokud se počet signál je nula.  
  
> [!NOTE]
>  Pro kód, který nemá k interakci se starší verze rozhraní .NET Framework synchronizace rozhraní API, zvažte použití <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty nebo <xref:System.Threading.Tasks.Parallel.Invoke%2A> metoda bylo ještě jednodušší způsob vyjádření paralelismus rozvětvení spojení.  
  
 <xref:System.Threading.CountdownEvent>má tyto funkce:  
  
-   Zrušit lze pomocí tokenů zrušení operace čekání.  
  
-   Po vytvoření instance se zvýší počet jeho signál.  
  
-   Instance lze opětovně použít po <xref:System.Threading.CountdownEvent.Wait%2A> vrátila voláním <xref:System.Threading.CountdownEvent.Reset%2A> metoda.  
  
-   Instance vystavit <xref:System.Threading.WaitHandle> pro integraci v rámci jiné rozhraní .NET Framework synchronizace rozhraní API, jako <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Základní informace o využití  
 Následující příklad ukazuje, jak používat <xref:System.Threading.CountdownEvent> s <xref:System.Threading.ThreadPool> pracovní položky.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent s zrušení  
 Následující příklad ukazuje, jak zrušit operace čekání na <xref:System.Threading.CountdownEvent> pomocí tokenu zrušení. Základní vzor odpovídá modelu pro jednotné zrušení, který byl představen v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Další informace najdete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Všimněte si, že operace čekání nezruší vláken, která jsou signalizace. Obvykle zrušení se použije pro logický provoz a který může obsahovat čekání na událost, jakož i všechny pracovní položky, které se nesynchronizují čekání. V tomto příkladu je každý pracovní položka předán kopii stejný token zrušení, aby mohli odpovídat na žádost o zrušení.  
  
## <a name="see-also"></a>Viz také  
 [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
