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
ms.openlocfilehash: ac1f2283ad30499748511e6fed6d5ce98da7fd14
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960109"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>je primitiva synchronizace, která odblokuje čekající vlákna poté, co byla signalizována určitý počet opakování. <xref:System.Threading.CountdownEvent>je navržen pro scénáře, ve kterých byste jinak museli před signalizací <xref:System.Threading.ManualResetEventSlim> události použít <xref:System.Threading.ManualResetEvent> nebo ručně snížit proměnnou. Například ve scénáři rozvětvení/spojení můžete vytvořit <xref:System.Threading.CountdownEvent> pouze ty, které mají počet signálů 5, a potom spustit pět pracovních položek ve fondu vláken a při dokončení každé pracovní položky zavolat. <xref:System.Threading.CountdownEvent.Signal%2A> Každé volání <xref:System.Threading.CountdownEvent.Signal%2A> snižuje počet signálů o 1. V hlavním vlákně <xref:System.Threading.CountdownEvent.Wait%2A> bude volání zablokováno, dokud není počet signálů nula.  
  
> [!NOTE]
> Pro kód, který nemusí pracovat se staršími rozhraními API pro synchronizaci .NET Framework, <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> zvažte použití objektů <xref:System.Threading.Tasks.Parallel.Invoke%2A> nebo metody pro snazší snadnější přístup k paralelnímu rozvětvení spojení.  
  
 <xref:System.Threading.CountdownEvent>má tyto další funkce:  
  
- Operaci čekání lze zrušit pomocí tokenů zrušení.  
  
- Po vytvoření instance se dá zvýšit počet signálů.  
  
- Instance lze znovu použít poté, <xref:System.Threading.CountdownEvent.Wait%2A> co bylo vráceno <xref:System.Threading.CountdownEvent.Reset%2A> voláním metody.  
  
- Instance zveřejňují <xref:System.Threading.WaitHandle> integraci s jinými .NET Frameworkmi synchronizačními rozhraními <xref:System.Threading.WaitHandle.WaitAll%2A>API, jako je například.  
  
## <a name="basic-usage"></a>Základní využití  
 Následující příklad ukazuje, jak použít <xref:System.Threading.CountdownEvent> s <xref:System.Threading.ThreadPool> pracovními položkami.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent s zrušením  
 Následující příklad ukazuje, jak zrušit operaci čekání na <xref:System.Threading.CountdownEvent> pomocí tokenu zrušení. Základní vzor následuje model pro sjednocení zrušení, který je představený v .NET Framework 4. Další informace naleznete v tématu [zrušení ve spravovaných vláknech](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Všimněte si, že operace wait neruší vlákna, která ji signalizuje. Zrušení je obvykle použito pro logickou operaci a může zahrnovat čekání na událost a také všechny pracovní položky, které čeká na synchronizaci. V tomto příkladu je každé pracovní položce předána kopie stejného tokenu zrušení, aby mohla reagovat na žádost o zrušení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
