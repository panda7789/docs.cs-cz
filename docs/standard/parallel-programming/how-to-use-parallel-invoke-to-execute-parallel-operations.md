---
title: "Postupy: Použití Parallel.Invoke k vykonávání paralelních operací"
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
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a51f180a394c1baa2ecb0620279ea15c62e1edc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Postupy: Použití Parallel.Invoke k vykonávání paralelních operací
Tento příklad ukazuje, jak operace paralelními pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A> v knihovně Task Parallel Library. Na sdílený zdroj dat je třeba udělat tři operace. Protože žádná operace, které upraví zdroj, se mohou být provedeny souběžně přehledné způsobem.  
  
> [!NOTE]
>  Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s výrazy lambda v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 Všimněte si, že s <xref:System.Threading.Tasks.Parallel.Invoke%2A>, jednoduše express které akce, kterou chcete spustit souběžně a modul runtime zpracovává všechny podrobnosti, včetně změny automaticky počet jader na hostitelském počítači plánování vláken.  
  
 Tento příklad parallelizes operace, ne data. Alternativní způsob můžete paralelními dotazů LINQ pomocí PLINQ a spouštět dotazy postupně. Alternativně můžete může paralelními data pomocí PLINQ. Další možností je učinit paralelní dotazy a úlohy. I když výsledná režie může snížit výkon na hostitelských počítačích s relativně malý počet procesorů, by měl být nárůst mnohem lepší na počítačích s více procesory.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkopírujte a vložte celý příklad do projektu Microsoft Visual Studio 2010 a stisknutím klávesy F5.  
  
## <a name="see-also"></a>Viz také  
 [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
 [Postupy: zrušení úlohy a její podřízené položky](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
