---
title: 'Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SpinWait, how to synchronize two-phase wait
ms.assetid: b2ac4e4a-051a-4f65-b4b9-f8e103aff195
ms.openlocfilehash: 5bac174660177fd47e1f345e64581e35ae4c0ffc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73137939"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání
Následující příklad ukazuje, jak <xref:System.Threading.SpinWait?displayProperty=nameWithType> použít objekt k implementaci dvoufázové operace čekání. V první fázi, objekt synchronizace `Latch`, se točí po dobu několika cyklů, zatímco zkontroluje, zda zámek je k dispozici. Ve druhé fázi, pokud zámek k `Wait` dispozici, pak <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> metoda vrátí bez použití provést jeho čekání; v `Wait` opačném případě provede čekání.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje velmi základní implementaci primitivní synchronizace zámku. Tuto datovou strukturu můžete použít, když se očekává, že čekací doby budou velmi krátké. Tento příklad je pouze pro demonstrační účely. Pokud v programu požadujete funkci typu zámku, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>aplikace .  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Západka používá <xref:System.Threading.SpinWait> objekt točit na místě pouze `SpinOnce` do <xref:System.Threading.SpinWait> další volání způsobí, že výnos časový úsek vlákna. V tomto okamžiku západka způsobí vlastní <xref:System.Threading.WaitHandle.WaitOne%2A> přepínač <xref:System.Threading.ManualResetEvent> kontextu voláním a předání mj.  
  
 Výstup protokolování ukazuje, jak často západka byla schopna zvýšit <xref:System.Threading.ManualResetEvent>výkon získáním zámku bez použití .  
  
## <a name="see-also"></a>Viz také

- [SpinWait](../../../docs/standard/threading/spinwait.md)
- [Objekty a prvky zřetězení](../../../docs/standard/threading/threading-objects-and-features.md)
