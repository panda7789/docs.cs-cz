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
ms.openlocfilehash: 665490601cad9ccd7881042aed576b95bbc07115
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139725"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Postupy: Použití Parallel.Invoke k vykonávání paralelních operací

Tento příklad ukazuje, jak paralelizovat operace pomocí <xref:System.Threading.Tasks.Parallel.Invoke%2A> v Task Parallel Library. Ve sdíleném zdroji dat se provádí tři operace. Vzhledem k tomu, že žádná operace nemění zdroj, dají se provádět paralelně způsobem.

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Příklad

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Všimněte si, že u <xref:System.Threading.Tasks.Parallel.Invoke%2A>jednoduše vyjadřujte, které akce chcete spustit souběžně, a modul runtime zpracovává všechny podrobnosti plánování vláken, včetně automatického škálování na počet jader v hostitelském počítači.

V tomto příkladu se parallelizes operace, nikoli data. Jako alternativní přístup můžete paralelizovat dotazy LINQ pomocí PLINQ a spouštět dotazy sekvenčně. Alternativně můžete data paralelizovat pomocí PLINQ. Další možností je paralelizovat dotazy i úkoly. I když výsledná režie může snížit výkon na hostitelských počítačích s relativně malým počtem procesorů, bude se mnohem lépe škálovat na počítačích s mnoha procesory.

## <a name="compile-the-code"></a>Kompilovat kód

Celý příklad zkopírujte a vložte do projektu Microsoft Visual Studio a stiskněte klávesu **F5**.

## <a name="see-also"></a>Viz také:

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Postupy: Zrušení úlohy a podřízených elementů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
