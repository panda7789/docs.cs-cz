---
title: 'Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock'
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
ms.openlocfilehash: cd2f5c65f45d83ef23643dcc747a748bb8ba89d9
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290821"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock
Tento dokument vysvětluje, jak použít <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> třídu k provedení operace, když jsou data k dispozici z více zdrojů. Ukazuje také použití nehladového režimu pro povolení více bloků spojení pro efektivnější sdílení zdroje dat.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad definuje tři typy prostředků,, `NetworkResource` `FileResource` a `MemoryResource` , a provádí operace, když budou prostředky k dispozici. Tento příklad vyžaduje `NetworkResource` dvojici a, aby `MemoryResource` bylo možné provést první operaci a `FileResource` dvojici a, aby `MemoryResource` bylo možné provést druhou operaci. Chcete-li povolit tyto operace, když jsou k dispozici všechny požadované prostředky, tento příklad používá <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> třídu. Když <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekt obdrží data ze všech zdrojů, šíří tato data do cíle, což je v tomto příkladu <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt. Oba <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty jsou čteny ze sdíleného fondu `MemoryResource` objektů.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Chcete-li povolit efektivní použití sdíleného fondu `MemoryResource` objektů, tento příklad určuje <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> vlastnost nastavenou na `False` k vytvoření <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objektů, které fungují v nehladovém režimu. Blok spojení bez vizuálního připojení odloží všechny příchozí zprávy, dokud není z každého zdroje k dispozici. Pokud byla kterákoli z odložených zpráv přijata jiným blokem, blok spojení tento proces restartuje. Nehladový režim umožňuje, aby bloky spojení sdílely jeden nebo více zdrojových bloků, aby bylo možné postupovat i v případě, že ostatní bloky čekají na data. V tomto příkladu, pokud `MemoryResource` je objekt přidán do `memoryResources` fondu, může být prvním spojovacím blokem, který obdrží svůj druhý zdroj dat, schopen předávat svůj průběh. Pokud byl v tomto příkladu použit hladový režim, což je výchozí, jeden blok spojení může převzít `MemoryResource` objekt a počkat na zpřístupnění druhého prostředku. Pokud má však druhý blok spojení k dispozici druhý zdroj dat, nemůže dodávat průběh, protože objekt byl vytvořen `MemoryResource` jiným blokem spojení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Použití nehladových spojení vám také může pomáhat zabránit zablokování aplikace. V softwarové aplikaci dochází k *vzájemnému zablokování* , když dva nebo více procesů každý z nich podrží určitý prostředek a zároveň čekají na další proces pro uvolnění nějakého jiného prostředku. Zvažte aplikaci, která definuje dva <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty. Oba objekty čtou data ze dvou sdílených zdrojových bloků. V režimu hladce, pokud jeden blok spojení čte z prvního zdroje a druhý blok spojení čte z druhého zdroje, může aplikace zablokovat, protože oba bloky spojení vzájemně čekají na uvolnění svého prostředku. V nehladovém režimu každý z nich přečte z jeho zdrojů pouze v případě, že jsou k dispozici všechna data, a proto je riziko zablokování eliminováno.  
  
## <a name="see-also"></a>Viz také

- [Tok dat](dataflow-task-parallel-library.md)
