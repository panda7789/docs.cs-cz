---
title: 'Postupy: Použití Parallel.Invoke k vykonávání paralelních operací'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d0870d23c5606fbdd8b4a2f78c4d8b9f4ddc93e
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259633"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Postupy: Použití Parallel.Invoke k vykonávání paralelních operací
Tento příklad ukazuje, jak pomocí paralelní zpracování operace <xref:System.Threading.Tasks.Parallel.Invoke%2A> v knihovně Task Parallel Library. Na sdílený zdroj dat provádějí tři operace. Protože žádná z operací upraví zdroj, mohou být provedeny souběžně v přímočarým způsobem.  
  
> [!NOTE]
>  Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [výrazy Lambda v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 Všimněte si, že se <xref:System.Threading.Tasks.Parallel.Invoke%2A>, jednoduše express akce, které chcete spouštět souběžně a modul runtime zpracovává všechny podrobnosti, včetně automatické škálování počtu jader v hostitelském počítači plánování vláken.  
  
 V tomto příkladu parallelizes operace, ne data. Jako alternativní přístup můžete pomocí PLINQ paralelizovat dotazů LINQ a dotazy spouští sekvenčně. Alternativně může paralelizovat data s využitím PLINQ. Další možností je paralelní dotazy a úlohy. Ačkoli výsledný režii může snížit výkon na hostitelském počítači s relativně malý počet procesorů, ho případném vertikálním mnohem lepší na počítačích s více procesory.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Zkopírujte a vložte do projektu sadu Microsoft Visual Studio 2010 celý příklad a stiskněte klávesu F5.  
  
## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)  
- [Postupy: Zrušení úlohy a podřízených elementů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
