---
title: 'Postupy: Určení režimu spouštění v PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to use execution mode
ms.assetid: e52ff26c-c5d3-4fab-9fec-c937fb387963
ms.openlocfilehash: f035dbcd5091d81a3cce3b9e9e683d836fe84bb7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635811"
---
# <a name="how-to-specify-the-execution-mode-in-plinq"></a>Postupy: Určení režimu spouštění v PLINQ

Tento příklad ukazuje, jak vynutit PLINQ obejít jeho výchozí heuristiky a paralelizovat dotaz bez ohledu na tvar dotazu.  
  
> [!NOTE]
> Tento příklad je určen k předvedení využití a nemusí běžet rychleji než ekvivalentní sekvenční LINQ na objekty dotazu. Další informace o zrychlení naleznete v [tématu Principy zrychlení v PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PLINQ#22](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#22)]
 [!code-vb[PLINQ#22](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#22)]  
  
 PLINQ je navržen tak, aby využíval příležitostí pro paralelizaci. Však ne všechny dotazy těžit z paralelního provádění. Například pokud dotaz obsahuje delegáta jednoho uživatele, který dělá málo práce, dotaz obvykle běží rychleji postupně. Sekvenční spuštění je rychlejší, protože režie, která se podílí na povolení paralelního spuštění, je dražší než získané zrychlení. Proto PLINQ není automaticky paralelizovat každý dotaz. Nejprve zkoumá tvar dotazu a různé operátory, které jej tvoří. Na základě této analýzy PLINQ ve výchozím režimu spuštění se může rozhodnout provést některé nebo všechny dotazu postupně. V některých případech však můžete vědět více o dotazu než PLINQ je schopen určit z jeho analýzy. Například můžete vědět, že delegát je nákladné a že dotaz bude určitě těžit z paralelizace. V takových případech můžete <xref:System.Linq.ParallelEnumerable.WithExecutionMode%2A> použít metodu <xref:System.Linq.ParallelExecutionMode.ForceParallelism> a zadat hodnotu pokyn PLINQ vždy spustit dotaz jako paralelní.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vyjmout a vložit tento kód do [ukázky dat PLINQ](../../../docs/standard/parallel-programming/plinq-data-sample.md) a volání metody z `Main`.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Linq.ParallelEnumerable.AsSequential%2A>
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
