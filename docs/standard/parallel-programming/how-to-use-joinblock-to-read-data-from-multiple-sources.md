---
title: 'Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
ms.openlocfilehash: 66fd7ed7a98b8be8f88f65ecb52710a1e40af778
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139740"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock
Tento dokument vysvětluje, jak použít třídu <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> k provedení operace, když jsou data dostupná z více zdrojů. Ukazuje také použití nehladového režimu pro povolení více bloků spojení pro efektivnější sdílení zdroje dat.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad definuje tři typy prostředků, `NetworkResource`, `FileResource`a `MemoryResource`a provádí operace, když budou prostředky k dispozici. Tento příklad vyžaduje dvojici `NetworkResource` a `MemoryResource`, aby bylo možné provést první operaci a dvojici `FileResource` a `MemoryResource`, aby bylo možné provést druhou operaci. Chcete-li povolit tyto operace, když jsou k dispozici všechny požadované prostředky, v tomto příkladu se používá třída <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Když objekt <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> obdrží data ze všech zdrojů, šíří tato data do cíle, což je v tomto příkladu objekt <xref:System.Threading.Tasks.Dataflow.ActionBlock%601>. Oba <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty čteny ze sdíleného fondu `MemoryResource` objektů.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Chcete-li povolit efektivní použití sdíleného fondu `MemoryResource` objektů, v tomto příkladu určuje <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> objekt, který má vlastnost <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> nastavenou na `False` pro vytváření <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objektů, které fungují v nehladovém režimu. Blok spojení bez vizuálního připojení odloží všechny příchozí zprávy, dokud není z každého zdroje k dispozici. Pokud byla kterákoli z odložených zpráv přijata jiným blokem, blok spojení tento proces restartuje. Nehladový režim umožňuje, aby bloky spojení sdílely jeden nebo více zdrojových bloků, aby bylo možné postupovat i v případě, že ostatní bloky čekají na data. Pokud se v tomto příkladu do fondu `memoryResources` přidá objekt `MemoryResource`, první spojovací blok, který obdrží svůj druhý zdroj dat, může předávat svůj postup. Pokud by byl v tomto příkladu použit hladový režim, což je výchozí, jeden blok spojení může převzít objekt `MemoryResource` a počkat, až bude k dispozici druhý zdroj. Pokud má však druhý blok spojení k dispozici druhý zdroj dat, nemůže dodávat průběh, protože objekt `MemoryResource` byl vybraný jiným blokem spojení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Použití nehladových spojení vám také může pomáhat zabránit zablokování aplikace. V softwarové aplikaci dochází k *vzájemnému zablokování* , když dva nebo více procesů každý z nich podrží určitý prostředek a zároveň čekají na další proces pro uvolnění nějakého jiného prostředku. Zvažte aplikaci, která definuje dva objekty <xref:System.Threading.Tasks.Dataflow.JoinBlock%602>. Oba objekty čtou data ze dvou sdílených zdrojových bloků. V režimu hladce, pokud jeden blok spojení čte z prvního zdroje a druhý blok spojení čte z druhého zdroje, může aplikace zablokovat, protože oba bloky spojení vzájemně čekají na uvolnění svého prostředku. V nehladovém režimu každý z nich přečte z jeho zdrojů pouze v případě, že jsou k dispozici všechna data, a proto je riziko zablokování eliminováno.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
