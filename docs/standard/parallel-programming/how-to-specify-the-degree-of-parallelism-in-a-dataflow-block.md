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
ms.openlocfilehash: 50399d6cd32fe310089395ac8c660b08151ba808
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141650"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Postupy: Určení stupně paralelního zpracování v bloku toku dat
Tento dokument popisuje, jak <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> nastavit vlastnost povolit spuštění bloku toku dat pro zpracování více než jednu zprávu najednou. To je užitečné, pokud máte blok toku dat, který provádí dlouhotrvající výpočty a může využívat paralelní zpracování zpráv. Tento příklad <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> používá třídu k provádění více operací toku dat současně; můžete však určit maximální stupeň paralelismu v libovolném z předdefinovaných typů bloků <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>spuštění, <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>které poskytuje knihovna toku dat TPL, , a .

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad provede dva výpočty toku dat a vytiskne uplynulý čas, který je vyžadován pro každý výpočt. První výpočtu určuje maximální stupeň paralelismu 1, což je výchozí. Maximální stupeň paralelismu 1 způsobí, že blok toku dat zpracovává zprávy sériově. Druhý výpočt se podobá první, s tím rozdílem, že určuje maximální stupeň paralelismu, který se rovná počtu dostupných procesorů. To umožňuje bloku toku dat provádět více operací paralelně.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Ve výchozím nastavení každý předdefinovaný blok toku dat šíří zprávy v pořadí, ve kterém jsou zprávy přijímány.  Přestože více zpráv jsou zpracovány současně při zadání maximální stupeň paralelismu, který je větší než 1, jsou stále šířeny v pořadí, ve kterém jsou přijaty.  
  
 Vzhledem <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> k tomu, že vlastnost představuje maximální stupeň paralelismu, blok toku dat může spustit s menším stupněm paralelismu, než zadáte. Blok toku dat můžete použít menší stupeň paralelismu ke splnění jeho funkční požadavky nebo účet pro nedostatek dostupných systémových prostředků. Blok toku dat nikdy nezvolí větší stupeň paralelismu, než zadáte.  
  
## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
