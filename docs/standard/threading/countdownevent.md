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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73138114"
---
# <a name="countdownevent"></a>CountdownEvent
<xref:System.Threading.CountdownEvent?displayProperty=nameWithType>je synchronizační primitiv, který odblokuje jeho čekající vlákna poté, co byla signalizována určitý počet opakování. <xref:System.Threading.CountdownEvent>je určen pro scénáře, ve kterých <xref:System.Threading.ManualResetEvent> <xref:System.Threading.ManualResetEventSlim> byste jinak museli použít nebo nebo ručně dekrement proměnné před signalizací události. Například ve scénáři rozteč/spojení můžete <xref:System.Threading.CountdownEvent> pouze vytvořit, který má počet signálů 5 a potom spustit pět <xref:System.Threading.CountdownEvent.Signal%2A> pracovních položek ve fondu vláken a mít každé volání pracovní položky po dokončení. Každé volání <xref:System.Threading.CountdownEvent.Signal%2A> sníží počet signálů o 1. V hlavním vlákně <xref:System.Threading.CountdownEvent.Wait%2A> bude volání blokovat, dokud nebude počet signálů nula.  
  
> [!NOTE]
> Pro kód, který nemusí pracovat se staršími rozhraními API <xref:System.Threading.Tasks.Task?displayProperty=nameWithType> synchronizace <xref:System.Threading.Tasks.Parallel.Invoke%2A> rozhraní .NET Framework, zvažte použití objektů nebo metody pro ještě snadnější přístup k vyjádření paralelismu spojení vložky.  
  
 <xref:System.Threading.CountdownEvent>má tyto další funkce:  
  
- Operace čekání může být zrušena pomocí tokenů zrušení.  
  
- Jeho počet signálu může být po vytvoření instance zpřísněn.  
  
- Instance lze znovu použít <xref:System.Threading.CountdownEvent.Wait%2A> po vrácené <xref:System.Threading.CountdownEvent.Reset%2A> voláním metody.  
  
- Instance vystavit <xref:System.Threading.WaitHandle> pro integraci s jinými rozhraní mise <xref:System.Threading.WaitHandle.WaitAll%2A>.NET Framework synchronizace rozhraní API, jako je například .  
  
## <a name="basic-usage"></a>Základní použití  
 Následující příklad ukazuje, jak <xref:System.Threading.CountdownEvent> používat <xref:System.Threading.ThreadPool> s pracovní položky.  
  
 [!code-csharp[CDS_CountdownEvent#01](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#01)]
 [!code-vb[CDS_CountdownEvent#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/module1.vb#01)]  
  
## <a name="countdownevent-with-cancellation"></a>CountdownEvent se zrušením  
 Následující příklad ukazuje, jak zrušit <xref:System.Threading.CountdownEvent> operaci čekání na pomocí tokenu zrušení. Základní vzor následuje model pro jednotné zrušení, který je zaveden v rozhraní .NET Framework 4. Další informace naleznete [v tématu Zrušení v tématu Spravovaná vlákna](../../../docs/standard/threading/cancellation-in-managed-threads.md).  
  
 [!code-csharp[CDS_CountdownEvent#02](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_countdownevent/cs/countdownevent.cs#02)]
 [!code-vb[CDS_CountdownEvent#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_countdownevent/vb/canceleventwait.vb#02)]  
  
 Všimněte si, že operace čekání nezruší podprocesy, které jsou signalizace. Obvykle zrušení se použije na logické operace a to může zahrnovat čekání na událost, stejně jako všechny pracovní položky, které čekání synchronizuje. V tomto příkladu je každé pracovní položce předána kopie stejného tokenu zrušení tak, aby mohla reagovat na požadavek na zrušení.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Threading.Semaphore?displayProperty=nameWithType>
