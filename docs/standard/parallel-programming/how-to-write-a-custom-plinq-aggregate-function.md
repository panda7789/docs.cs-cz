---
title: "Postupy: Psaní vlastní agregační funkce pro PLINQ"
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
helpviewer_keywords: PLINQ queries, how to create aggregate function
ms.assetid: 5a70dd49-ab2a-4798-b551-196ee7042b1a
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8b098f21e29d0d59cd99ddbb64af6246d9953a3a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-custom-plinq-aggregate-function"></a>Postupy: Psaní vlastní agregační funkce pro PLINQ
Tento příklad ukazuje způsob použití <xref:System.Linq.ParallelEnumerable.Aggregate%2A> metodu chcete použít vlastní agregační funkce pro zdrojové sekvence.  
  
> [!WARNING]
>  Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad vypočítá směrodatnou odchylku posloupnost celých čísel.  
  
 [!code-csharp[PLINQ#31](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#31)]
 [!code-vb[PLINQ#31](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#31)]  
  
 Tento příklad používá přetížení operátoru agregační standardní dotazu, které jsou jedinečné pro PLINQ. Toto přetížení trvá Další <xref:System.Func%603?displayProperty=nameWithType> třetí vstupní parametr. Tento delegát kombinuje výsledky z všechna vlákna, než provede konečný výpočet na agregované výsledky. V tomto příkladu přidáme společně součtů ze všech vláken.  
  
 Všimněte si, že pokud lambda výraz sestává z jediného výrazu, vrátí hodnotu, která <xref:System.Func%602?displayProperty=nameWithType> delegáta je hodnota výrazu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.ParallelEnumerable>  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
