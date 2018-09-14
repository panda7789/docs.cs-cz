---
title: 'Postupy: Určení stupně paralelního zpracování v bloku toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b597cf93cdf249936a34b2c07b38d000c96333f
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520623"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Postupy: Určení stupně paralelního zpracování v bloku toku dat
Tento dokument popisuje, jak nastavit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> vlastností pro povolení z bloku toku dat provádění zpracovávat více zpráv najednou. To je užitečné, když máte bloku toku dat, který provádí dlouho běžící výpočetní a využívat zpracování zpráv s paralelně. V tomto příkladu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> třídy provádět více operací toku dat současně, ale, můžete určit maximální míru paralelismu v jakýkoli z typů předdefinovaných provedení bloku, které poskytuje Knihovna TPL datového toku <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad provádí dvě výpočty toku dat a vytiskne uplynulého času, který je požadován pro každý výpočet. První výpočtu určuje maximální volnost paralelismu 1, což je výchozí hodnota. Maximální volnost paralelismu 1 způsobí, že blok toku dat ke zpracování zpráv sériově. Druhé výpočet vypadá podobně jako první, s tím rozdílem, že určuje maximální volnost paralelismu, který je roven počet dostupných procesorů. To umožňuje bloku toku dat pro paralelní provádění více operací.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` v jazyce Visual Basic), a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**  
  
 Visual Basic  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
 Ve výchozím nastavení každý blok toku dat předdefinované šíří zprávy v pořadí, ve kterém jsou zprávy přijímány.  I když více zpráv souběžně zpracování při zadávání maximální volnost paralelismu, který je větší než 1, že jsou stále šířen mimo v pořadí, ve kterém jsou přijímány.  
  
 Vzhledem k tomu, <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost představuje maximální volnost paralelismu, bloku toku dat může spustit s menší stupně paralelního zpracování, než jste určili. Blok toku dat můžete použít menší stupeň paralelismu, jeho funkční požadavky nebo aby se zohlednily nedostatek systémových prostředků. Blok toku dat nikdy zvolí vyšší stupeň paralelismu než zadáte.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
