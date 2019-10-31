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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141650"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Postupy: Určení stupně paralelního zpracování v bloku toku dat
Tento dokument popisuje, jak nastavit vlastnost <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> tak, aby povolovala spuštění bloku toku dat pro zpracování více zpráv v jednom okamžiku. To je užitečné v případě, že máte blok toku dat, který provádí dlouhodobě běžící výpočet a může využívat paralelní zpracování zpráv. Tento příklad používá třídu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> k souběžnému provádění více operací toku dat; Můžete však určit maximální stupeň paralelismu v některém z předdefinovaných typů bloku spuštění, které poskytuje knihovna Dataflow v TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad provádí dva výpočty toku dat a tiskne uplynulý čas, který je požadován pro každý výpočet. První výpočet určuje maximální stupeň paralelismu typu 1, což je výchozí hodnota. Maximální stupeň paralelismus z hodnoty 1 způsobí, že blok toku dat zpracovává zprávy sériově. Druhý výpočet se podobá první, s tím rozdílem, že určuje maximální stupeň paralelismu, který se rovná počtu procesorů, které jsou k dispozici. To umožňuje, aby blok toku dat prováděl paralelní provádění více operací.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Ve výchozím nastavení každý předdefinovaný blok toku dat šíří zprávy v pořadí, ve kterém jsou zprávy přijímány.  I když je souběžně zpracováno více zpráv, když zadáte maximální stupeň paralelismu, který je větší než 1, jsou nadále šířeny v pořadí, ve kterém jsou přijaty.  
  
 Vzhledem k tomu, že vlastnost <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> představuje maximální stupeň paralelismu, může být blok toku dat proveden s menším stupněm paralelismu, než určíte. Blok toku dat může využít menší stupeň paralelismu k splnění jeho funkčních požadavků nebo k vytvoření účtu nedostatku dostupných systémových prostředků. Blok toku dat nikdy nevolí větší stupeň paralelismu, než zadáte.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
