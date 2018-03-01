---
title: "Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ"
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
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 20b1be451e53a81dd0631a89310a5b884aa83166
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Postupy: Vytvoření a provedení jednoduchého dotazu PLINQ
Následující příklad ukazuje, jak vytvořit jednoduchý dotaz paralelní LINQ pomocí <xref:System.Linq.ParallelEnumerable.AsParallel%2A> rozšiřující metody na zdrojové sekvence a provádění dotazu s použitím <xref:System.Linq.ParallelEnumerable.ForAll%2A> metoda.  
  
> [!NOTE]
>  Tato dokumentace používá k definování delegátů v PLINQ výrazy lambda. Pokud nejste obeznámeni s výrazy lambda v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Tento příklad ukazuje základní vzor pro vytváření a spouštění jakýkoli dotaz paralelní LINQ při řazení výsledků pořadí není důležité. Neseřazený dotazy jsou obecně rychlejší než seřazené dotazy. Dotaz oddíly zdroje do úlohy, které se spustí asynchronně na více vláken. Pořadí, ve kterém je každý úkol dokončí závisí nejen na objem práce související zpracovat elementy v oddílu, ale také na externí faktorech, například jak operačního systému plánuje každé vlákno. Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Další informace o tom, jak zachovat řazení elementů v dotazu najdete v tématu [postupy: řízení řazení v PLINQ dotazu](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Viz také  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
