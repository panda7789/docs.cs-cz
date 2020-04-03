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
ms.openlocfilehash: c4cd75e55aabb551e5951a902ea6394a5659c9ee
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635856"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ

Příklad v tomto článku ukazuje, jak vytvořit jednoduchý paralelní jazyk integrovaný <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=nameWithType> dotaz (LINQ) dotaz pomocí metody rozšíření <xref:System.Linq.ParallelEnumerable.ForAll%2A?displayProperty=nameWithTyp> na zdrojové sekvence a provádění dotazu pomocí metody.  
  
> [!NOTE]
> Tato dokumentace používá lambda výrazy definovat delegáty v PLINQ. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Tento příklad ukazuje základní vzor pro vytváření a provádění jakékoli paralelní LINQ dotazu při řazení pořadí výsledek sekvence není důležité. Neuspořádané dotazy jsou obecně rychlejší než objednané dotazy. Dotaz rozdělí zdroj do úloh, které jsou spouštěny asynchronně ve více vláknech. Pořadí, ve kterém každý úkol dokončí závisí nejen na množství práce spojené se zpracováním prvků v oddílu, ale také na externí faktory, jako je například plánování operačního systému každé vlákno. Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu. Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Další informace o tom, jak zachovat řazení prvků v dotazu, naleznete v tématu [How to: Control Ordering in a PLINQ Query](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také

- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
