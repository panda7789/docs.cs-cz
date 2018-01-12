---
title: "Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock"
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- TPL dataflow library, joining blocks in
- dataflow blocks, joining in TPL
ms.assetid: e9c1ada4-ac57-4704-87cb-2f5117f8151d
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f7d4e552404f99580bceafe7f900db4607201c3d
ms.sourcegitcommit: 6a9030eb5bd0f00e1d144f81958adb195cfb1f6f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock
Tento dokument vysvětluje, jak používat <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> třída k provedení určité operace, pokud jsou k dispozici data z více zdrojů. Také ukazuje, jak povolit více připojení k bloků efektivněji sdílet zdroje dat pomocí typu non-greedy režimu.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 V následujícím příkladu definuje tři typy prostředků, `NetworkResource`, `FileResource`, a `MemoryResource`a provádí operace, kdy prostředky k dispozici. Tento příklad vyžaduje, `NetworkResource` a `MemoryResource` pár, aby bylo možné provést operaci první a `FileResource` a `MemoryResource` pár, aby bylo možné provést operaci druhý. Pokud chcete povolit tyto operace nastat, když všechny požadované prostředky jsou k dispozici, v tomto příkladu <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> třídy. Když <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekt přijímá data ze všech zdrojů, se rozšíří dat k cíli, která v tomto příkladu je <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. Obě <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objektů číst z sdílenému fondu `MemoryResource` objekty.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Povolit efektivní využití sdílený fond `MemoryResource` objekty, tento příklad určuje <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> vlastnost nastavena na hodnotu `False` k vytvoření <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty, které fungují v režimu typu non-greedy. Spojení typu non-greedy blok odloží všechny příchozí zprávy, dokud je dostupný z každého zdroje. Pokud některý z odložených zpráv byly přijaty jiného bloku, blok spojení restartuje proces. Typu non-greedy režim umožňuje připojení k bloky, které sdílejí jeden či více bloků zdroj chcete provést postup směrem vpřed, jako ostatní bloky počkejte dat. V tomto příkladu Pokud `MemoryResource` objekt přidá do `memoryResources` fond, toto spojení provádět bloku přijímat zdrojem dat pro druhý postup směrem vpřed. Pokud v tomto příkladu byly použití typu greedy režimu, který je výchozí, jeden blok připojení může trvat `MemoryResource` objektu a počkat na druhý prostředek k dispozici. Ale pokud k připojení k bloku má svůj druhý zdroj dat dostupný, nemůže vytvořit postup směrem vpřed protože `MemoryResource` objekt které byly použity k připojení k bloku.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Příklad kódu zkopírujte a vložte ji do projektu sady Visual Studio nebo ho vložte v souboru, který je pojmenován `DataflowNonGreedyJoin.cs` (`DataflowNonGreedyJoin.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
 Použití spojení typu non-greedy také vám pomůže předejít zablokování v aplikaci. V aplikaci softwaru *zablokování* nastane, když minimálně dva procesy každý uložení prostředku a vzájemně čekat na jiný proces k uvolnění jiný prostředek. Zvažte aplikaci, která definuje dvě <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty. Oba objekty každý přečíst data z dva bloky sdílené zdroje. V typu greedy režimu Pokud jeden spojení blok čte z zdroji první a druhý bloku spojení načítá druhý zdroje, aplikace může zablokování, protože obě připojení bloky vzájemně Čekejte na další vydat jeho prostředků. V typu non-greedy režimu každého bloku spojení čtení z její zdroje jenom v případě, že je k dispozici všechna data a proto riziko vzájemného zablokování je eliminovat.  
  
## <a name="see-also"></a>Viz také  
 [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
