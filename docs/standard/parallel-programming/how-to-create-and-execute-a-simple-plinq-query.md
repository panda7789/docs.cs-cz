---
title: 'Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 472304dff23e92620dd461e8bc43c3093431ddc4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962521"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ
Následující příklad ukazuje, jak vytvořit jednoduchý paralelní dotaz LINQ pomocí <xref:System.Linq.ParallelEnumerable.AsParallel%2A> metody rozšíření zdrojové sekvence a provedení dotazu <xref:System.Linq.ParallelEnumerable.ForAll%2A> pomocí metody.  
  
> [!NOTE]
> Tato dokumentace používá lambda výrazy k definování delegátů v PLINQ. Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Tento příklad ukazuje základní vzor pro vytvoření a spuštění paralelního dotazu LINQ, pokud pořadí výsledků není důležité. neuspořádané dotazy jsou všeobecně rychlejší než seřazené dotazy. Dotaz rozdělí zdroj na úlohy, které se provádějí asynchronně ve více vláknech. Pořadí, ve kterém jednotlivé úlohy dokončí, závisí nejen na množství práce, která je součástí zpracování prvků v oddílu, ale také na vnějších faktorech, jako je například způsob, jakým operační systém naplánuje jednotlivá vlákna. Tento příklad je určený k předvedení používání a nemusí běžet rychleji než ekvivalentní sekvenční LINQ to Objects dotaz. Další informace o zrychlení naleznete v tématu [Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Další informace o tom, jak zachovat řazení prvků v dotazu, naleznete v tématu [How to: Řazení ovládacích prvků v dotazu](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md)PLINQ.  
  
## <a name="see-also"></a>Viz také:

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
