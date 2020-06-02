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
ms.openlocfilehash: 4b2bc79a7b652c34334d5a78d9c9af328993ff44
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279203"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání
Následující příklad ukazuje, jak použít <xref:System.Threading.SpinWait?displayProperty=nameWithType> objekt k implementaci dvoufázové operace čekání. V první fázi se synchronizační objekt, a `Latch` , se rozpíná za několik cyklů, zatímco kontroluje, zda je zámek k dispozici. Ve druhé fázi, pokud je zámek k dispozici, pak `Wait` Metoda vrátí bez použití <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> k provedení čekání; v opačném případě `Wait` provede čekání.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje velmi základní implementaci primitiva synchronizace západ. Tuto datovou strukturu můžete použít, pokud se očekává, že čekací časy budou velmi krátké. Tento příklad je určen pouze pro demonstrační účely. Pokud v programu požadujete funkce typu západ, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> .  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Západku používá <xref:System.Threading.SpinWait> objekt k rozmístění pouze do dalšího volání, které způsobí, že by se vyvolal `SpinOnce` <xref:System.Threading.SpinWait> časový úsek vlákna. V tomto okamžiku západ vyvolá svůj vlastní kontextový přepínač voláním metody <xref:System.Threading.WaitHandle.WaitOne%2A> <xref:System.Threading.ManualResetEvent> a procházející zbytkem hodnoty časového limitu.  
  
 Výstup protokolování ukazuje, jak často bylo západ moci zvýšit výkon tím, že získá zámek bez použití <xref:System.Threading.ManualResetEvent> .  
  
## <a name="see-also"></a>Viz také

- [SpinWait](spinwait.md)
- [Dělení objektů a funkcí](threading-objects-and-features.md)
