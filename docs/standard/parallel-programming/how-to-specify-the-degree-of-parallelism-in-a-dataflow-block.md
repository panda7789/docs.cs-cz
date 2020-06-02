---
title: 'Postupy: Určení stupně paralelního zpracování v bloku toku dat'
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
ms.openlocfilehash: 75302c98177a92b921996944f2862298fc612f31
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288105"
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Postupy: Určení stupně paralelního zpracování v bloku toku dat
Tento dokument popisuje, jak nastavit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> vlastnost tak, aby umožňovala zpracování bloku toku dat spouštění více zpráv najednou. To je užitečné v případě, že máte blok toku dat, který provádí dlouhodobě běžící výpočet a může využívat paralelní zpracování zpráv. V tomto příkladu se používá <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> třída pro souběžné provádění více operací toku dat. můžete však určit maximální stupeň paralelismu v jakémkoli z předdefinovaných typů bloku spuštění, které poskytuje knihovna Dataflow v TPL,, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType> .

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad provádí dva výpočty toku dat a tiskne uplynulý čas, který je požadován pro každý výpočet. První výpočet určuje maximální stupeň paralelismu typu 1, což je výchozí hodnota. Maximální stupeň paralelismus z hodnoty 1 způsobí, že blok toku dat zpracovává zprávy sériově. Druhý výpočet se podobá první, s tím rozdílem, že určuje maximální stupeň paralelismu, který se rovná počtu procesorů, které jsou k dispozici. To umožňuje, aby blok toku dat prováděl paralelní provádění více operací.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Ve výchozím nastavení každý předdefinovaný blok toku dat šíří zprávy v pořadí, ve kterém jsou zprávy přijímány.  I když je souběžně zpracováno více zpráv, když zadáte maximální stupeň paralelismu, který je větší než 1, jsou nadále šířeny v pořadí, ve kterém jsou přijaty.  
  
 Vzhledem k tomu, že <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost představuje maximální stupeň paralelismu, může být blok toku dat proveden s menším stupněm paralelismu, než určíte. Blok toku dat může využít menší stupeň paralelismu k splnění jeho funkčních požadavků nebo k vytvoření účtu nedostatku dostupných systémových prostředků. Blok toku dat nikdy nevolí větší stupeň paralelismu, než zadáte.  
  
## <a name="see-also"></a>Viz také

- [Tok dat](dataflow-task-parallel-library.md)
