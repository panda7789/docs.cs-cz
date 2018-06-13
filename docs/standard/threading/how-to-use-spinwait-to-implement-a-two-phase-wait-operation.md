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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af6e4e8d0d754b97478788422b4dd84eeddc6491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583276"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání
Následující příklad ukazuje, jak používat <xref:System.Threading.SpinWait?displayProperty=nameWithType> objektu k implementaci dvoufázové operace čekání. V první fázi objekt synchronizace `Latch`, otáčí po několik cyklů při zkontroluje, jestli má k dispozici zámek. V druhé fázi, pokud zámek k dispozici pak se `Wait` metoda vrátí bez použití <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> čekání; provést, jinak hodnota `Wait` provádí čekání.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje velmi základní implementace synchronizace západky primitivní. Tato struktura dat můžete použít při očekávané velmi krátké době čekání. V tomto příkladu je pouze pro demonstrační účely. Pokud budete potřebovat západkou typu funkce v programu, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Používá zámek <xref:System.Threading.SpinWait> objekt, který chcete číselníku zavedené pouze do další volání `SpinOnce` způsobí, že <xref:System.Threading.SpinWait> k yield časového intervalu vlákna. V tomto bodě zámek způsobí vlastní přepnutí kontextu voláním <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> a předání ve zbývající části hodnoty časového limitu.  
  
 Protokolování výstupu ukazuje, jak často se zámek a zvyšuje výkon získávání zámek bez použití <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Viz také  
 [SpinWait](../../../docs/standard/threading/spinwait.md)  
 [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
