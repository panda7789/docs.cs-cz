---
title: "Postupy: Určení režimu spouštění v PLINQ"
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
helpviewer_keywords: PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c1c815131a1553001cdcf20e3c7408e472299677
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Postupy: Určení režimu spouštění v PLINQ
Tento příklad ukazuje, jak vynutit PLINQ obejití výchozí heuristiky a paralelní dotaz bez ohledu na tvar dotazu.  
  
> [!WARNING]
>  Tento příklad je určený k předvedení využití a nemusí být možné spustit rychleji, než ekvivalentní sekvenčních LINQ na objekty dotazu. Další informace o zrychlení najdete v tématu [porozumění zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ je navržen tak, aby využil příležitosti pro paralelizace. Ne všechny dotazy však těžit z paralelní provádění. Například pokud dotaz obsahuje delegát jednoho uživatele, který nemá uživatele příliš mnoho zásahů, se obvykle spustí dotaz rychleji postupně. Je to proto, že režie spojená s povolením paralelního spuštění je větší než zrychlení, který byl získán. Proto PLINQ není paralelní automaticky každých dotazu. Nejprve zkontroluje tvar dotazu a různé operátory, které ji tvoří. Na základě této analýzy PLINQ ve výchozím režimu zpracování rozhodnout postupně provést některé nebo všechny dotazu. Ale v některých případech může vědět více o dotazu než PLINQ je možné určit, ze své analýza. Můžete například vědět, že delegát je velmi náročná a aby dotaz výborný využívat paralelizace. V takových případech můžete použít <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> metoda a zadejte <xref:System.Linq.ParallelExecutionMode.ForceParallelism> hodnotu vždy spusťte dotaz paralelně.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vyjmout a vložit tento kód do [ukázková Data pro PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a volat metodu z `Main`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Linq.ParallelEnumerable.AsSequential%2A>  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
