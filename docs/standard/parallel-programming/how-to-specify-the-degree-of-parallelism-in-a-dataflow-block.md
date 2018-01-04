---
title: "Postupy: Určení stupně paralelního zpracování v bloku toku dat"
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
- dataflow block, specifying parallelism in TPL
- Task Parallel Library, dataflows
- TPL dataflow library, specifying parallelism
ms.assetid: e4088541-ee05-40db-95f5-147cfe62fde7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: bca80e2ad3081d610a5e89d1dc7e778eadb58119
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-specify-the-degree-of-parallelism-in-a-dataflow-block"></a>Postupy: Určení stupně paralelního zpracování v bloku toku dat
Tento dokument popisuje, jak nastavit <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A?displayProperty=nameWithType> vlastnost umožňující bloku toku dat provádění zpracovat více než jeden zprávu najednou. To je užitečné, když máte bloku toku dat, který provádí výpočet dlouho běžící a využívat zpracování zpráv paralelně. Tento příklad používá <xref:System.Threading.Tasks.Dataflow.ActionBlock%601?displayProperty=nameWithType> třídy k provedení více operací toku dat současně, ale, můžete zadat maximální stupně paralelního zpracování v některém z předdefinovaných provádění bloku typy, které poskytuje knihovna toku dat TPL, <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>, <xref:System.Threading.Tasks.Dataflow.TransformBlock%602?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602?displayProperty=nameWithType>.  
  
> [!TIP]
>  Knihovna toku dat TPL ( <xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> oboru názvů) není distribuované s [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. K instalaci <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online `Microsoft.Tpl.Dataflow` balíčku.  
  
## <a name="example"></a>Příklad  
 Následující příklad provede výpočty dvě toku dat a vytiskne uplynulý čas, která je požadována pro každý výpočetní. První výpočet určuje maximální stupně paralelního zpracování 1, který je výchozí. Maximální stupeň paralelismu 1 způsobí, že bloku toku dat ke zpracování zpráv sériově. Druhý výpočet se podobá první, s tím rozdílem, že určuje maximální stupně paralelního zpracování, které se rovná počet dostupných procesorů. To umožňuje bloku toku dat k provedení více operací paralelně.  
  
 [!code-csharp[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_degreeofparallelism/cs/dataflowdegreeofparallelism.cs#1)]
 [!code-vb[TPLDataflow_DegreeOfParallelism#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_degreeofparallelism/vb/dataflowdegreeofparallelism.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowDegreeOfParallelism.cs` (`DataflowDegreeOfParallelism.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowDegreeOfParallelism.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
 Ve výchozím nastavení každého bloku toku dat předdefinované rozšíří na zprávy v pořadí, ve kterém jsou přijaté zprávy.  I když více zpráv zpracovávají současně, když zadáte maximálního stupně paralelního zpracování, který je větší než 1, se stále rozšířeny se v pořadí, ve kterém jsou přijaty.  
  
 Protože <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions.MaxDegreeOfParallelism%2A> vlastnost představuje maximální stupně paralelního zpracování, bloku toku dat může spustit s nižší úrovní stupně paralelního zpracování, než jste určili. Bloku toku dat můžete použít v menší míře paralelismus jeho funkční splnění nebo aby se zohlednily nedostatek dostupné prostředky systému. Blok toku dat nikdy zvolí větší stupně paralelního zpracování, než jste určili.  
  
## <a name="see-also"></a>Viz také  
 [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
