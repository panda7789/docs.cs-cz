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
ms.openlocfilehash: 628d6a96606117d447c61d01595d13dd4a957ce4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138114"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType> je synchronizační primitiv, která odblokuje své čekající vlákna poté, co byla signalizována určitý počet opakování. <xref:System.Threading.CountdownEvent> je navržený pro scénáře, ve kterých byste jinak museli použít <xref:System.Threading.ManualResetEvent> nebo <xref:System.Threading.ManualResetEventSlim> a ručně snížit proměnnou před signalizací události. Například ve scénáři rozvětvení/spojení můžete vytvořit <xref:System.Threading.CountdownEvent>, která má počet signálů 5, a potom spustit pět pracovních položek ve fondu vláken a nechat <xref:System.Threading.CountdownEvent.Signal%2A> volání pracovní položky, když je dokončí. Každé volání <xref:System.Threading.CountdownEvent.Signal%2A> sníží počet signálů o 1. V hlavním vlákně se volání <xref:System.Threading.CountdownEvent.Wait%2A> zablokuje, dokud není počet signálů nula.  
  
> [!NOTE]
> Pro kód, který nemusí pracovat se staršími rozhraními API pro synchronizaci .NET Framework, zvažte použití objektů <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> nebo <xref:System.Threading.Tasks.Parallel.Invoke%2A> metody pro snazší přístup k paralelnímu přístupu rozvětvení.  
  
 <xref:System.Threading.CountdownEvent> má tyto další funkce:  
  
- Operaci čekání lze zrušit pomocí tokenů zrušení.  
  
- Po vytvoření instance se dá zvýšit počet signálů.  
  
- Instance lze znovu použít po vrácení <xref:System.Threading.CountdownEvent.Wait%2A> voláním metody <xref:System.Threading.CountdownEvent.Reset%2A>.  
  
- Instance zpřístupňují <xref:System.Threading.WaitHandle> pro integraci s jinými .NET Frameworkmi synchronizačními rozhraními API, jako je například <xref:System.Threading.WaitHandle.WaitAll%2A>.  
  
## <a name="basic-usage"></a>Základní využití  
 Následující příklad ukazuje, jak použít <xref:System.Threading.CountdownEvent> s pracovními položkami <xref:System.Threading.ThreadPool>.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent s zrušením  
 Následující příklad ukazuje, jak zrušit operaci čekání na <xref:System.Threading.CountdownEvent> pomocí tokenu zrušení. Základní vzor následuje model pro sjednocení zrušení, který je představený v .NET Framework 4. Další informace naleznete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Všimněte si, že operace wait neruší vlákna, která ji signalizuje. Zrušení je obvykle použito pro logickou operaci a může zahrnovat čekání na událost a také všechny pracovní položky, které čeká na synchronizaci. V tomto příkladu je každé pracovní položce předána kopie stejného tokenu zrušení, aby mohla reagovat na žádost o zrušení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
