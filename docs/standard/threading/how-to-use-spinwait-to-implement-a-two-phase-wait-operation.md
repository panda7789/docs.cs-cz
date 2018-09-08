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
ms.openlocfilehash: dcb2fbf5e0a310156fdc6fac5fe736692e8ec133
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44209209"
---
# <a name="how-to-use-spinwait-to-implement-a-two-phase-wait-operation"></a>Postupy: Použití objektu SpinWait pro implementaci dvoufázové operace čekání
Následující příklad ukazuje způsob použití <xref:System.Threading.SpinWait?displayProperty=nameWithType> objektu pro implementaci dvoufázové operace čekání. V první fázi synchronizační objekt `Latch`, otáčí pro několik cyklů při kontrole, jestli má zámek k dispozici. Ve druhé fázi, pokud zámek přestane být k dispozici pak bude `Wait` metoda vrátí bez použití <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> provádět jeho čekání; v opačném případě `Wait` provádí čekání.  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje velmi základní implementaci zámek synchronizace primitivní. Tato struktura dat můžete použít při velmi krátké očekávané době čekání. V tomto příkladu je pouze pro demonstrační účely. Pokud vyžadujete funkce západkou typu ve svém programu, zvažte použití <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>.  
  
 [!code-csharp[CDS_SpinWait#03](../../../samples/snippets/csharp/VS_Snippets_Misc/cds_spinwait/cs/spinwait03.cs#03)]
 [!code-vb[CDS_SpinWait#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_spinwait/vb/spinwait2.vb#03)]  
  
 Používá zámek <xref:System.Threading.SpinWait> objektu, abyste mohli spustit na místě pouze až do příštího volání metody `SpinOnce` způsobí, že <xref:System.Threading.SpinWait> výnosu časovém intervalu vlákna. V tomto okamžiku západku způsobí, že vlastní přepnutí kontextu voláním <xref:System.Threading.WaitHandle.WaitOne%2A> na <xref:System.Threading.ManualResetEvent> a předávání do zbývající část hodnoty časového limitu.  
  
 Protokolování výstupu ukazuje, jak často se podařilo a zvyšuje výkon získání zámku bez použití Zámek <xref:System.Threading.ManualResetEvent>.  
  
## <a name="see-also"></a>Viz také:

- [SpinWait](../../../docs/standard/threading/spinwait.md)  
- [Funkce a objekty dělení na vlákna](../../../docs/standard/threading/threading-objects-and-features.md)
