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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139725"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Postupy: Použití Parallel.Invoke k vykonávání paralelních operací

Tento příklad ukazuje, jak paralelizovat <xref:System.Threading.Tasks.Parallel.Invoke%2A> operace pomocí v paralelní knihovně úloh. Tři operace jsou prováděny na sdíleném zdroji dat. Vzhledem k tomu, že žádná z operací upravuje zdroj, mohou být provedeny paralelně přímočarým způsobem.

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, naleznete [lambda výrazy v PLINQ a TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Příklad

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Všimněte <xref:System.Threading.Tasks.Parallel.Invoke%2A>si, že s , jednoduše vyjádřit, které akce, které chcete spustit souběžně a modul runtime zpracovává všechny podrobnosti plánování vláken, včetně škálování automaticky na počet jader v hostitelském počítači.

Tento příklad paralelizuje operace, nikoli data. Jako alternativní přístup můžete paralelizovat linq dotazy pomocí PLINQ a spouštět dotazy postupně. Případně můžete paralelizovat data pomocí PLINQ. Další možností je paralelizovat dotazy i úkoly. Přestože výsledná režie může snížit výkon v hostitelských počítačích s relativně málo procesory, by škálovat mnohem lépe v počítačích s mnoha procesory.

## <a name="compile-the-code"></a>Kompilace kódu

Zkopírujte a vložte celý příklad do projektu aplikace Microsoft Visual Studio a stiskněte **klávesu F5**.

## <a name="see-also"></a>Viz také

- [Paralelní programování](../../../docs/standard/parallel-programming/index.md)
- [Postupy: Zrušení úlohy a podřízených elementů](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
