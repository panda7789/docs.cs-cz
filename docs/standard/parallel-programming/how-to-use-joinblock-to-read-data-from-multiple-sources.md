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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139740"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock
Tento dokument vysvětluje, jak <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> použít třídu k provedení operace, pokud jsou data k dispozici z více zdrojů. Také ukazuje, jak používat nechamtivý režim povolit více bloků spojení pro efektivnější sdílení zdroje dat.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad definuje tři typy `NetworkResource` `FileResource`prostředků `MemoryResource`, , a , a provádí operace, když jsou k dispozici prostředky. Tento příklad `NetworkResource` vyžaduje `MemoryResource` a pár k provedení první `FileResource` `MemoryResource` operace a a a pár k provedení druhé operace. Chcete-li povolit tyto operace dojít, když jsou <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> k dispozici všechny požadované prostředky, tento příklad používá třídu. Když <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekt přijímá data ze všech zdrojů, šíří tato data do svého cíle, což je v tomto příkladu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt. Oba <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty číst ze `MemoryResource` sdíleného fondu objektů.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Chcete-li povolit efektivní `MemoryResource` využití sdíleného fondu <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> objektů, tento <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> příklad `False` určuje <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekt, který má vlastnost nastavenou na vytváření objektů, které fungují v nechamtivém režimu. Blok nehladového spojení odloží všechny příchozí zprávy, dokud není z každého zdroje k dispozici jedna. Pokud některé z odložené zprávy byly přijaty jiným blokem, blok spojení restartuje proces. Nechamtivý režim umožňuje spojit bloky, které sdílejí jeden nebo více zdrojových bloků, aby se pokročilo vpřed, protože ostatní bloky čekají na data. V tomto příkladu `MemoryResource` pokud je `memoryResources` objekt přidán do fondu, první blok spojení přijímat jeho druhý zdroj dat může provést pokrok vpřed. Pokud by tento příklad používal režim hladovění, který je výchozí, jeden blok spojení může převzít `MemoryResource` objekt a čekat na dostupnost druhého prostředku. Pokud však má druhý blok spojení k dispozici druhý zdroj `MemoryResource` dat, nemůže provést postup vpřed, protože objekt byl převzat jiným blokem spojení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Použití nechamtivých spojení vám může také pomoci zabránit zablokování v aplikaci. V softwarové aplikaci dojde k *zablokování,* když dva nebo více procesů každý obsahovat prostředek a vzájemně čekat na jiný proces uvolnit jiný prostředek. Zvažte aplikaci, <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> která definuje dva objekty. Oba objekty každý číst data ze dvou sdílených zdrojových bloků. V režimu hladový, pokud jeden blok spojení čte z prvního zdroje a druhý blok spojení čte z druhého zdroje, aplikace může zablokování, protože oba bloky spojení vzájemně čekat na druhé uvolnit svůj prostředek. V nehladovém režimu každý blok spojení čte ze svých zdrojů pouze v případě, že jsou k dispozici všechna data, a proto je eliminováno riziko zablokování.  
  
## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
