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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137939"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání
Následující příklad ukazuje, jak použít objekt <xref:System.Threading.SpinWait?displayProperty=nameWithType> k implementaci dvoufázové operace čekání. V první fázi se objekt synchronizace, `Latch`, rozpíná několik cyklů, zatímco kontroluje, zda je zámek k dispozici. Pokud je zámek k dispozici ve druhé fázi, `Wait` metoda vrátí bez použití <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> k provedení čekání; v opačném případě `Wait` provede čekání.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje velmi základní implementaci primitiva synchronizace západ. Tuto datovou strukturu můžete použít, pokud se očekává, že čekací časy budou velmi krátké. Tento příklad je určen pouze pro demonstrační účely. Pokud v programu požadujete funkce typu západ, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Západ používá objekt <xref:System.Threading.SpinWait> k rozmístění pouze do chvíle, kdy další volání `SpinOnce` způsobí, že <xref:System.Threading.SpinWait> zaznamená časový úsek vlákna. V tomto okamžiku západ vyvolá svůj vlastní kontextový přepínač voláním <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> a předáním zbývající část hodnoty časového limitu.  
  
 Výstup protokolování ukazuje, jak často byla západ moci zvýšit výkon tím, že získá zámek bez použití <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Viz také:

- [SpinWait](../../../docs/standard/threading/spinwait.md)
- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
