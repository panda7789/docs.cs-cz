---
title: 'Postupy: Vytvoření kanálu toku dat'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dataflow pipelines, creating with TPL
- Task Parallel Library, dataflows
- TPL dataflow library, creating dataflow pipeline
ms.assetid: 69308f82-aa22-4ac5-833d-e748533b58e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b74e60daced88050413855070c880cd6c1cebfb1
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44272548"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>Postupy: Vytvoření kanálu toku dat
Přestože lze použít <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> metody pro příjem zpráv ze zdroje bloky, můžete také připojit blokům zpráv do formuláře *kanálu toku dat*. Kanálu toku dat je řada komponent, nebo *bloků toku dat*, z nichž každý provádí konkrétní úlohu, která přispívá k větší cíl. Každý blok toku dat v kanálu toku dat provádí práci, když přijme zprávu z jiného bloku toku dat. Obdobně to je montážní linky u automobilů výroby. Každý vozidla prochází montážní linky, jedné stanice sestaví rámce, dalším objektem nainstaluje modul a tak dále. Protože montážní linky umožňuje více vozidel pro sestavení ve stejnou dobu, poskytuje lepší propustnost než sestavení kompletní vozidel jeden po druhém.

 Tento dokument vysvětluje kanálu toku dat, která stahuje knihu *Iliad Homer* z webu a hledání text tak, aby odpovídaly jednotlivých slov s slova tohoto zpětného první slovo znaků. Vytvoření kanálu toku dat v tomto dokumentu se skládá z následujících kroků:  
  
1.  Vytvoření bloků toku dat, které se účastní v kanálu.  
  
2.  Připojení každého bloku toku dat k další blok v kanálu. Každý blok přijímá jako vstup výstup předchozího bloku v kanálu.  
  
3.  Pro každý blok toku dat vytvoří se úkol pokračování, který nastaví další blok do dokončeného stavu po dokončení předchozího bloku.  
  
4.  Odesílání dat na začátku profilace.  
  
5.  Hlavní kanál označte jako dokončený.  
  
6.  Vyčkat, než kanál dokončit veškerou práci.  
  
## <a name="prerequisites"></a>Požadavky  
 Čtení [toku dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md) před zahájením tohoto návodu.  
  
## <a name="creating-a-console-application"></a>Vytvoření konzolové aplikace  
 V sadě Visual Studio vytvořte projekt Visual C# nebo Visual Basic konzolové aplikace. Nainstalujte balíček System.Threading.Tasks.Dataflow NuGet.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Přidejte následující kód do vašeho projektu, chcete-li vytvořit základní aplikaci.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Vytvoření bloků toku dat  
 Přidejte následující kód, který `Main` metodu pro vytvoření bloků toku dat, které se účastní v kanálu. Následující tabulka shrnuje role každého člena kanálu.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Člen|Typ|Popis|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Stáhne textu knihy z webu.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Odděluje knihy text do pole slova.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Odebere krátká slova a duplicitní hodnoty z pole aplikace word.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Najde všechna slova v kolekci pole filtrované slovo jehož zpětného také dochází v poli word.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí slova a odpovídající zpětného vyhledávání do konzoly.|  
  
 I když můžete zkombinovat více kroků v rámci kanálu toku dat v tomto příkladu do jednoho kroku, tento příklad znázorňuje konceptu vytváření více nezávislých toku dat úloh na větší úlohu provést. V příkladu <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> aby každý člen kanálu provádění operací na svoje vstupní data a odesílala výsledky do dalšího kroku v kanálu. `findReversedWords` Člen kanálu <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objektu, protože vytváří několik nezávislých výstupů pro každou vstup. Konec kanálu `printReversedWords`, je <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objektu, protože provádí akci ve vzorci a nevytváří výsledek.  
  
## <a name="forming-the-pipeline"></a>Které tvoří kanál  
 Přidejte následující kód k připojení každého bloku k další blok v kanálu.  
  
 Při volání <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metody pro připojení zdroje dat do bloku toku do bloku toku dat cílový blok toku dat zdroje šíří dat na cílový blok, jak budou data k dispozici. Pokud zadáte také <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> s <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> nastavenou na hodnotu true, úspěšné nebo neúspěšné dokončení jeden blok v kanálu způsobí dokončení další blok v kanálu.
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>Odesílání dat do kanálu  
 Přidejte následující kód o vystavení adresy URL knihy *Iliad Homer* na jednoho kanálu toku dat.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Tento příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> synchronně odesílat data do hlavní kanál. Použití <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metody asynchronně musíte odesílat data do uzlu datového toku.  
  
## <a name="completing-pipeline-activity"></a>Dokončení aktivity kanálu  
 Přidejte následující kód do hlavní kanál označit jako dokončený. Vedoucí kanálu rozšíří jeho dokončení po zpracování všech ve vyrovnávací paměti zpráv.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Tento příklad odešle jednu adresu URL prostřednictvím kanálu toku dat ke zpracování. Pokud odesíláte více než jeden vstup prostřednictvím kanálu, zavolejte <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> metoda po odeslání veškerý vstup. Tento krok můžete vynechat, pokud aplikace nemá žádný jasně definovaných bod, ve kterém datového již není k dispozici nebo aplikace nebude muset čekat kanálu na Dokončit.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Čekání na kanál pro dokončení  
 Přidejte následující kód čekat kanálu na Dokončit. Po dokončení funkce tail kanálu dokončení celé operace.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Můžete počkat na dokončení toku dat z libovolného vlákna nebo z více vláken současně.  
  
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód v tomto návodu.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad odešle jednu adresu URL ke zpracování toku dat kanálem. Pokud odešlete více než jeden vstupní hodnota prostřednictvím kanálu, můžou představovat určitou formu paralelismu na aplikace, která se podobá, jak může prostřednictvím automobilů factory přesunout částí. Při prvním členem kanálu odešle svůj výsledek na druhý člen, dokáže zpracovat jiná položka paralelně, jako druhý člen zpracuje první výsledek.  
  
 Paralelismus, které můžete dosáhnout použitím kanály toku dat, se nazývá *paralelismu hrubých* vzhledem k tomu, že se obvykle skládá menšího počtu větších úloh. Můžete také použít více *dosáhnout jemně odstupňovaného paralelismu* menší, krátce běžící úlohy v kanálu toku dat. V tomto příkladu `findReversedWords` člen kanál používá [PLINQ](parallel-linq-plinq.md) zpracování více položek v seznamu pracovních paralelně. Použití jemně odstupňovaného paralelismu hrubých kanálu můžete vylepšit celkovou propustnost.  
  
 Zdroj dat do bloku toku můžete také připojit k více cílovými bloky pro vytváření *toku dat sítě*. Přetížené verze <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> přijímá metodu <xref:System.Predicate%601> objekt, který definuje, jestli cílový blok přijímá každé zprávy na základě jeho hodnoty. Většina toku dat typů bloků, které se chovají jako zdroje nabízí zpráv do všech připojených cílovým blokům, v pořadí, ve kterém byli připojeni, dokud jeden bloků přijme tuto zprávu. Když použijete tento mechanismus filtrování, můžete vytvořit systémy bloků toku dat připojených, které budou řídit určitá data prostřednictvím jednu cestu a další data prostřednictvím jinou cestu. Příklad, který používá filtrování vytvoření toku dat sítě, naleznete v tématu [návod: použití toku dat ve formulářové aplikaci Windows](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Viz také:

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
