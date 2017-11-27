---
title: "Postupy: Vytvoření kanálu toku dat"
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
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d63fb872382bfc0a3ba3b8637c7357ab65c58fbf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>Postupy: Vytvoření kanálu toku dat
Přestože je možné použít <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> metody pro příjem zpráv z zdroje bloky, bloky zpráv může připojit i k formuláře *kanálu toku dat*. Kanálu toku dat je několika komponent, nebo *bloků toku dat*, z nichž každá provádí konkrétní úlohu, která přispívá ke větší cíl. Každý bloku toku dat v kanálu toku dat provede práci při přijetí zprávy z jiného bloku toku dat. Analogie k tomuto je sestavení pro automobilů výrobní. Při každém vehicle průchodu řádku sestavení, jedné stanici sestaví rámečku, dalšímu nainstaluje modul a tak dále. Vzhledem sestavení řádku umožňuje více vozidel pro sestavení ve stejnou dobu, poskytuje lepší propustnost než ty dokončení vozidel jeden najednou.  
  
> [!TIP]
>  Knihovna toku dat TPL (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> oboru názvů) není distribuované s [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. K instalaci <xref:System.Threading.Tasks.Dataflow> obor názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z nabídky projektu a vyhledejte online `Microsoft.Tpl.Dataflow` balíčku.  
  
 Tento dokument ukazuje, kanálů toku dat, což seznam *Iliad Homer* z webu a hledání text tak, aby odpovídaly jednotlivých slov s slova tohoto zpětného znaků první slova. Vytvoření kanálu toku dat v tomto dokumentu se skládá z následujících kroků:  
  
1.  Vytvořte bloků toku dat, které se účastní v kanálu.  
  
2.  Připojení každého bloku toku dat k další blok v kanálu. Každý blok přijme jako vstup výstupu k předchozímu bloku v kanálu.  
  
3.  Pro každého bloku toku dat vytvořte pokračování úlohu, která nastaví další blok do stavu dokončení, po dokončení k předchozímu bloku.  
  
4.  Odesílání dat na head kanálu.  
  
5.  Označení hlavního kanálu jako dokončenou.  
  
6.  Počkejte, než pro kanál pro dokončení veškeré práce.  
  
## <a name="prerequisites"></a>Požadavky  
 Čtení [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) před spuštěním tohoto průvodce.  
  
## <a name="creating-a-console-application"></a>Vytvoření aplikace konzoly  
 V [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], vytvoření [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] nebo [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] projekt konzolové aplikace. Přidáte odkaz na System.Threading.Tasks.Dataflow.dll.  
  
 Alternativně vytvořte soubor s názvem `ReverseWords.cs` (`ReverseWords.vb` pro [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), a poté spusťte následující příkaz v okně příkazového řádku Visual Studia kompilace projektu.  
  
 [!INCLUDE[csprcs](../../../includes/csprcs-md.md)]  
  
 **csc.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.cs**  
  
 [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]  
  
 **Vbc.exe /r:System.Threading.Tasks.Dataflow.dll ReverseWords.vb**  
  
 Přidejte následující kód do projektu pro vytvoření základní aplikace.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Vytváření bloků toku dat  
 Přidejte následující kód, který `Main` metodu pro vytvoření bloků toku dat, které se účastní v kanálu. Následující tabulky shrnuje roli každý člen kanálu.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Člen|Typ|Popis|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Stáhne kniha text z webu.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Do pole slova odděluje text adresáře.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Odebere z slovo krátká slova pole, objednávky výsledné slova abecedně a odeberte duplicitní položky.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Vyhledá všechny slova v kolekci filtrované word pole, jejichž zpětného dochází také v poli aplikace word.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí slova a odpovídající zpětného vyhledávání do konzoly.|  
  
 I když můžete sloučit více kroků v kanálu toku dat v tomto příkladu do jeden krok, příklad ukazuje, koncept skládání více nezávislých toku dat úlohy musíte provést úlohu větší. Tento příklad používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> aby každý člen kanálu pro provádění operací na jeho vstupních dat a odesílání výsledky na další krok v kanálu. `findReversedWords` Člen kanálu <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekt, protože vytváří několik nezávislých výstupů pro každý vstupní. Tail kanálu `printReversedWords`, je <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, protože vstupní provádí akce a nevytváří výsledku.  
  
## <a name="forming-the-pipeline"></a>Které tvoří kanálu  
 Přidejte následující kód k připojení každého bloku k další blok v kanálu.  
  
 Při volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metoda pro připojení k cílové bloku toku dat bloku toku dat zdroj bloku toku dat zdroj rozšíří dat na cílový blok, jakmile data k dispozici.  
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="creating-the-completion-tasks"></a>Vytvoření úlohy dokončení  
 Přidejte následující kód k povolení jednotlivých bloků toku dat k provedení konečné akce, poté, co zpracuje všechna data.  
  
 [!code-csharp[TPLDataflow_Palindromes#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#5)]
 [!code-vb[TPLDataflow_Palindromes#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#5)]  
  
 Každý úkol dokončení potřebný k šíření dokončení prostřednictvím kanálu, nastaví další blok toku dat stavu dokončení. Například pokud head kanálu je nastaven na stavu dokončení, ho zpracovává všechny zbývající zprávy ve vyrovnávací paměti a pak spustí jeho dokončení úkolu, který nastaví druhý člen kanálu stavu dokončení. Druhý člen kanálu zase zpracovává všechny zbývající zprávy ve vyrovnávací paměti a poté spustí jeho dokončení úkolu, který nastaví třetí člena kanálu do stavu dokončení. Tento proces pokračuje, dokud nedokončí všichni členové kanálu. Tento příklad používá `delegate` – klíčové slovo (`Function` v [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) k definování úloh pokračování.  
  
## <a name="posting-data-to-the-pipeline"></a>Odesílání dat do kanálu  
 Přidejte následující kód o vystavení adresy URL knihy *Iliad Homer* do hlavního kanálu toku dat.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Tento příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> synchronně posílat data do hlavního kanálu. Použití <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metoda při asynchronně musíte odesílat data do toku dat uzlu.  
  
## <a name="completing-pipeline-activity"></a>Dokončení aktivity kanálu  
 Přidejte následující kód k označení hlavního kanálu jako dokončenou. Head kanálu spustí úkolu pokračování po zpracovává všechny uložené ve vyrovnávací paměti zpráv. Tato úloha pokračování rozšíří stavu dokončení prostřednictvím kanálu.  
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Tento příklad odešle jednu adresu URL prostřednictvím kanálu toku dat mají být zpracovány. Pokud odešlete více než jeden vstup prostřednictvím kanálu, zavolejte <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> metoda po odeslání veškerý vstup. Tento krok můžete vynechat, pokud vaše aplikace nemá žádný dobře definovaný bod, ve kterém dat již není k dispozici nebo není nutné čekat na kanálu ukončíte aplikace.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Čekání na kanálu, který má být dokončit  
 Přidejte následující kód čekat kanálu ukončíte. Protože tento příklad používá úloh pokračování potřebný k šíření dokončení prostřednictvím kanálu, celkový operace je dokončena po dokončení tail kanálu.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Můžete počkat na dokončení toku dat z libovolného vlákna nebo z více vláken ve stejnou dobu.  
  
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód v tomto návodu.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad odešle jednu adresu URL prostřednictvím kanálu toku dat zpracovat. Odešlete více než jednu vstupní hodnotu prostřednictvím kanálu, lze do aplikace, který vypadá takto: jak může částí pohyb objekt pro vytváření automobilů zavádět formuláře paralelního zpracování. Při prvním členem kanálu odešle svůj výsledek na druhý člen, může zpracovat jiné položce paralelně jako druhý člen zpracovává první výsledku.  
  
 Paralelismus, které je dosaženo pomocí kanály toku dat se označuje jako *hrubý paralelismus* vzhledem k tomu, že se obvykle skládá z méně, větší úlohy. Můžete také dalších *podrobných paralelismus* menší, krátce běžící úlohy v kanálu toku dat. V tomto příkladu `findReversedWords` člen kanálu používá <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> metoda zpracovat více položek v seznamu pracovní paralelně. Použití podrobného paralelismu v hrubý kanálu lze vylepšit celkovou propustnost.  
  
 Zdroj bloku toku dat může připojit i k více bloků cíl k vytvoření *toku dat sítě*. Přetížené verze <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metoda trvá <xref:System.Predicate%601> objekt, který definuje, zda cílový blok přijímá každou zprávu na základě jeho hodnoty. Většina bloku typů toku dat, které se chovají jako zdroje nabízejí zprávy na všech připojených cíl bloky, v pořadí, ve kterém byli připojeni, dokud jeden bloků přijímá zprávy. Když použijete tento filtrování mechanismus, můžete vytvořit systémy bloků toku dat připojené, které budou řídit určitá data prostřednictvím jednu cestu a další data prostřednictvím jiné cesty. Příklad, který používá filtrování vytvořit síť toku dat, naleznete v části [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Viz také  
 [Toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
