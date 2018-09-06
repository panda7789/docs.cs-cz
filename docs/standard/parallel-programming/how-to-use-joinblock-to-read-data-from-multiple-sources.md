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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c49f7ad5162c9e2759ec8afed217451b4bcf04ff
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43892649"
---
# <a name="how-to-use-joinblock-to-read-data-from-multiple-sources"></a>Postupy: Načítání dat z více zdrojů pomocí třídy JoinBlock
Tento dokument popisuje, jak používat <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> třídy provádět operace, když jsou k dispozici data z různých zdrojů. Také ukazuje, jak použít bez metody greedy režim povolit více bloků spojení sdílet zdroje dat efektivněji.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

## <a name="example"></a>Příklad  
 Následující příklad definuje tři typy prostředků, `NetworkResource`, `FileResource`, a `MemoryResource`a provádí operace, až budou dostupné prostředky. Tento příklad vyžaduje `NetworkResource` a `MemoryResource` pár, aby bylo možné provést první operaci a `FileResource` a `MemoryResource` pár, aby bylo možné provést druhou operaci. Pokud chcete povolit tyto operace nastat, když jsou k dispozici všechny požadované prostředky, v tomto příkladu <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> třídy. Když <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objektu přijímá data ze všech zdrojů, rozšíří tato data k cíli, který v tomto příkladu je <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu. Obě <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> přečíst objekty z sdílený fond `MemoryResource` objekty.  
  
 [!code-csharp[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_nongreedyjoin/cs/nongreedyjoin.cs#1)]
 [!code-vb[TPLDataflow_NonGreedyJoin#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_nongreedyjoin/vb/nongreedyjoin.vb#1)]  
  
 Umožňuje efektivní využití sdílený fond `MemoryResource` objekty, tento příklad určuje <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions> objekt, který má <xref:System.Threading.Tasks.Dataflow.GroupingDataflowBlockOptions.Greedy%2A> vlastnost nastavena na hodnotu `False` vytvořit <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty, které fungují v režimu bez metody greedy. Spojení typu non-greedy blok odloží všechny příchozí zprávy, dokud je k dispozici z každého zdroje. Pokud některý z odložených zprávy byly přijaty jiným blokem, restartuje blokovat připojení k procesu. Bez metody greedy režim umožňuje spojení bloky, které sdílejí jeden nebo více zdrojových bloků tak postup směrem vpřed, jak se bloky čekat na data. V tomto příkladu Pokud `MemoryResource` objekt přidán do `memoryResources` fondu, spojení první blok obdržet svůj druhý zdroj dat můžete provést postup směrem vpřed. Pokud v tomto příkladu byly pro použití režimu greedy, což je výchozí hodnota, jeden blok připojení může trvat, než `MemoryResource` objektu a počkejte, druhý prostředků k dispozici. Nicméně, pokud jiné spojení blok má svůj druhý zdroj dat k dispozici, nemůže vytvořit postup směrem vpřed protože `MemoryResource` objektu je už zabraný jiných spojení blokem.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Zkopírujte ukázkový kód a vložte ho do projektu sady Visual Studio nebo vložit do souboru s názvem `DataflowNonGreedyJoin.cs` (`DataflowNonGreedyJoin.vb` v jazyce Visual Basic), a pak spusťte následující příkaz v okně Příkazový řádek sady Visual Studio.  
  
 Visual C#  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.cs**  
  
 Visual Basic  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll DataflowNonGreedyJoin.vb**  
  
## <a name="robust-programming"></a>Robustní programování  
 Použití spojení typu non-greedy také vám může pomoct zabránit zablokování ve vaší aplikaci. V případě aplikace softwaru *zablokování* nastane, pokud dva nebo více procesů jednotlivých uložení prostředku a vzájemně počkat na jiný proces uvolnit jiný prostředek. Vezměte v úvahu aplikace, která definuje dva <xref:System.Threading.Tasks.Dataflow.JoinBlock%602> objekty. Oba objekty každý číst data ze dvou bloků sdílené zdroje. V režimu greedy Pokud jeden spojení blok čte z prvního zdroje a druhý spojení blok čte z druhého zdroje, aplikace může způsobila zablokování, protože obě spojení bloky vzájemně počkejte dalších vydat jeho prostředků. V režimu bez metody greedy každý blok spojení čtení záznamů z jeho zdroje pouze v případě, že všechna data jsou k dispozici a proto riziku zablokování je Odstraněná.  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
