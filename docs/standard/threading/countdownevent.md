---
title: CountdownEvent
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- synchronization primitives, CountdownEvent
ms.assetid: eec3812a-e20f-4ecd-bfef-6921d508b708
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b01fdd14d1adfe0480f93150ab6e996aa84dee
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44336846"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> je primitiv synchronizace, která byla odblokuje jeho čekajících vláken signalizován s určitým počtem opakování. <xref:System.Threading.CountdownEvent> určený pro scénáře, ve kterých je byste jinak museli používat <xref:System.Threading.ManualResetEvent> nebo <xref:System.Threading.ManualResetEventSlim> a ručně dekrementace proměnné před signalizace události. Například ve scénáři rozvětvení/spojení, stačí vytvořit <xref:System.Threading.CountdownEvent> , který má signálu počet 5, a pak start pěti pracovních položek ve vláknu fondu a každé pracovní položky pro volání <xref:System.Threading.CountdownEvent.Signal%2A> po dokončení. Každé volání <xref:System.Threading.CountdownEvent.Signal%2A> sníží počet signál o 1. Na hlavním vlákně, volání <xref:System.Threading.CountdownEvent.Wait%2A> bude blokovat, dokud počet signálu je nula.  
  
> [!NOTE]
>  Pro kód, který nemá pro interakci s starší verze rozhraní .NET Framework synchronizací rozhraní API, zvažte použití <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> objekty nebo <xref:System.Threading.Tasks.Parallel.Invoke%2A> metoda ještě jednodušší přístup k vyjádření forku spojení paralelismu.  
  
 <xref:System.Threading.CountdownEvent> má tyto dodatečné funkce:  
  
-   S použitím tokenů zrušení se dá zrušit operaci čekání.  
  
-   Po vytvoření instance se zvýší počet jeho signálu.  
  
-   Instance je možné využít znovu po <xref:System.Threading.CountdownEvent.Wait%2A> vrátila voláním <xref:System.Threading.CountdownEvent.Reset%2A> metody.  
  
-   Instance vystavit <xref:System.Threading.WaitHandle> pro integraci v rámci jiné rozhraní .NET Framework synchronizací rozhraní API, jako <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Základní informace o využití  
 Následující příklad ukazuje, jak používat <xref:System.Threading.CountdownEvent> s <xref:System.Threading.ThreadPool> pracovní položky.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent pomocí zrušení  
 Následující příklad ukazuje, jak zrušit operaci čekání na <xref:System.Threading.CountdownEvent> pomocí tokenu zrušení. Základní vzor řídí modelem jednotné zrušení, který je uveden v [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]. Další informace najdete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Všimněte si, že operace čekání nezruší vláken, která jsou signalizace. Obvykle zrušení se použije pro logické operace, a, který může obsahovat čekání na událost, jakož i všechny pracovní položky, které provádí synchronizaci čekání. V tomto příkladu se každé pracovní položce předá kopii stejný token zrušení tak, že můžete odpovědět na požadavek na zrušení.  
  
## <a name="see-also"></a>Viz také:

- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)
