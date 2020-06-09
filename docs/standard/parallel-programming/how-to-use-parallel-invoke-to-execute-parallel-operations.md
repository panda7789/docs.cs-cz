---
title: 'Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací'
description: Podívejte se, jak použít metodu Parallel. Invoke v Task Parallel Library (TPL), která provádí paralelní operace se sdíleným zdrojem dat v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
ms.openlocfilehash: 084ade48b1406d23a11eb311739525f35ac973df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596342"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Postupy: Použití algoritmu Parallel.Invoke k provádění paralelních operací

Tento příklad ukazuje, jak paralelizovat operace pomocí nástroje <xref:System.Threading.Tasks.Parallel.Invoke%2A> v Task Parallel Library. Ve sdíleném zdroji dat se provádí tři operace. Operace lze provádět paralelně, protože žádný z nich neupravuje zdroj.

> [!NOTE]
> Tato dokumentace používá k definování delegátů v TPL lambda výrazy. Pokud nejste obeznámeni s lambda výrazy v jazyce C# nebo Visual Basic, přečtěte si téma [lambda výrazy v PLINQ a TPL](lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Příklad

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Pomocí nástroje <xref:System.Threading.Tasks.Parallel.Invoke%2A> jednoduše vyjádřete, které akce chcete spustit souběžně, a modul runtime zpracovává všechny podrobnosti plánování vláken, včetně automatického škálování na počet jader v hostitelském počítači.

V tomto příkladu se parallelizes operace, nikoli data. Jako alternativní přístup můžete paralelizovat dotazy LINQ pomocí PLINQ a spouštět dotazy sekvenčně. Alternativně můžete data paralelizovat pomocí PLINQ. Další možností je paralelizovat dotazy i úkoly. I když výsledná režie může snížit výkon na hostitelských počítačích s relativně malým počtem procesorů, škáluje se lépe na počítačích s mnoha procesory.

## <a name="compile-the-code"></a>Kompilovat kód

Celý příklad zkopírujte a vložte do projektu Microsoft Visual Studio a stiskněte klávesu **F5**.

## <a name="see-also"></a>Viz také

- [Paralelní programování](index.md)
- [Postupy: Zrušení úlohy a podřízených elementů](how-to-cancel-a-task-and-its-children.md)
- [Paralelní LINQ (PLINQ)](introduction-to-plinq.md)
