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
ms.openlocfilehash: 284be7789b6411055a6421fd07cc1b0605f6ea0c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73139868"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>Postupy: Vytvoření kanálu toku dat
Přestože můžete <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType>použít <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> a metody pro příjem zpráv ze zdrojových bloků, můžete také připojit bloky zpráv k vytvoření *kanálu toku dat*. Kanál toku dat je řada součástí nebo *bloků toku dat*, z nichž každý provádí konkrétní úkol, který přispívá k většímu cíli. Každý blok toku dat v kanálu toku dat provádí práci, když obdrží zprávu z jiného bloku toku dat. Analogií k tomu je montážní linka pro výrobu automobilů. Jak každé vozidlo prochází montážní linkou, jedna stanice montuje rám, další nainstaluje motor a tak dále. Vzhledem k tomu, že montážní linka umožňuje montáž více vozidel současně, poskytuje lepší propustnost než montáž kompletních vozidel po jednom.

 Tento dokument demonstruje kanál toku dat, který stáhne knihu *Iliad of Homer z* webu a prohledá text tak, aby odpovídal jednotlivým slovům se slovy, která obrátí znaky prvního slova. Vytvoření kanálu toku dat v tomto dokumentu se skládá z následujících kroků:  
  
1. Vytvořte bloky toku dat, které se účastní kanálu.  
  
2. Připojte každý blok toku dat k dalšímu bloku v kanálu. Každý blok obdrží jako vstup výstup předchozího bloku v kanálu.  
  
3. Pro každý blok toku dat vytvořte úlohu pokračování, která nastaví další blok do dokončeného stavu po dokončení předchozího bloku.  
  
4. Zaúčtuj data do vedoucího potrubí.  
  
5. Označte vedoucího potrubí jako dokončeného.  
  
6. Počkejte na dokončení všech prací kanálu.  
  
## <a name="prerequisites"></a>Požadavky  
 Před spuštěním tohoto návodu si přečtěte [tok dat.](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)  
  
## <a name="creating-a-console-application"></a>Vytvoření konzolové aplikace  
 V sadě Visual Studio vytvořte projekt aplikace Visual C# nebo Visual Basic Console. Nainstalujte balíček System.Threading.Tasks.Dataflow NuGet.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Přidejte do projektu následující kód a vytvořte základní aplikaci.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Vytváření bloků toku dat  
 Přidejte následující kód `Main` k metodě k vytvoření bloků toku dat, které se účastní kanálu. Následující tabulka shrnuje roli každého člena kanálu.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Člen|Typ|Popis|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Stáhne text knihy z webu.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Odděluje text knihy do pole slov.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Odstraní krátká slova a duplikáty z pole slov.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Vyhledá všechna slova v kolekci filtrovaného pole slov, jejichž obrácení se vyskytuje také v poli slov.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí slova a odpovídající obrácená slova ke konzole.|  
  
 I když můžete kombinovat více kroků v kanálu toku dat v tomto příkladu do jednoho kroku, příklad ilustruje koncept skládání více nezávislých úloh toku dat k provedení větší úlohy. Příklad používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> povolit každý člen kanálu provést operaci na jeho vstupní data a odeslat výsledky k dalšímu kroku v kanálu. Člen `findReversedWords` kanálu je objekt, <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> protože vytváří více nezávislých výstupů pro každý vstup. Ocas kanálu , `printReversedWords`je <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, protože provádí akci na jeho vstup a nevytváří výsledek.  
  
## <a name="forming-the-pipeline"></a>Vytvoření potrubí  
 Přidejte následující kód pro připojení každého bloku k dalšímu bloku v kanálu.  
  
 Když zavoláte <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metodu pro připojení bloku zdrojového toku dat k cílovému bloku toku dat, blok toku zdrojových dat rozšíří data do cílového bloku, jakmile budou data k dispozici. Pokud také <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> poskytnete <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> nastavenou na hodnotu true, úspěšné nebo neúspěšné dokončení jednoho bloku v kanálu způsobí dokončení dalšího bloku v kanálu.
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>Zaúčtování dat do kanálu  
 Přidejte následující kód pro odeslání adresy URL knihy *Iliad of Homer* do čela kanálu datového toku.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Tento příklad <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> používá synchronně odesílat data do vedoucího kanálu. Metodu <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> použijte, když je nutné asynchronně odesílat data do uzlu toku dat.  
  
## <a name="completing-pipeline-activity"></a>Dokončení aktivity kanálu  
 Přidejte následující kód k označení vedoucího kanálu jako dokončeného. Vedoucí kanálu šíří jeho dokončení po zpracování všech zpráv ve vyrovnávací paměti.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Tento příklad odešle jednu adresu URL prostřednictvím kanálu toku dat, který má být zpracován. Pokud odešlete více než jeden vstup <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> prostřednictvím kanálu, volání metody po odeslání všech vstupů. Tento krok můžete vynechat, pokud vaše aplikace nemá žádný dobře definovaný bod, ve kterém již nejsou k dispozici data nebo aplikace nemusí čekat na dokončení kanálu.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Čekání na dokončení kanálu  
 Přidejte následující kód a počkejte na dokončení kanálu. Celková operace je dokončena po dokončení koncovky.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Můžete počkat na dokončení toku dat z libovolného vlákna nebo z více vláken současně.  
  
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje úplný kód pro tento návod.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad odešle jednu adresu URL ke zpracování prostřednictvím kanálu toku dat. Pokud odešlete více než jednu vstupní hodnotu prostřednictvím kanálu, můžete do aplikace zavést formu paralelismu, která se podobá tomu, jak se díly mohou pohybovat v automobilce. Když první člen kanálu odešle svůj výsledek druhému členu, může zpracovat jinou položku paralelně, když druhý člen zpracuje první výsledek.  
  
 Paralelismus, kterého je dosaženo pomocí kanálu toku dat, se označuje jako *hrubozrnný paralelismus,* protože se obvykle skládá z menšího počtu větších úloh. Můžete také použít *více jemně odstupňované paralelismu* menší, krátkodobé úlohy v kanálu toku dat. V tomto příkladu `findReversedWords` člen kanálu používá [PLINQ](parallel-linq-plinq.md) ke zpracování více položek v pracovním seznamu paralelně. Použití jemnozrnného paralelismu v hrubozrnném potrubí může zlepšit celkovou propustnost.  
  
 Můžete také připojit zdrojový blok toku dat k více cílovým blokům a vytvořit *síť toku dat*. Přetížená verze <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metody přebírá <xref:System.Predicate%601> objekt, který definuje, zda cílový blok přijímá každou zprávu na základě její hodnoty. Většina typů bloků toku dat, které fungují jako zdroje, nabízí zprávy všem připojeným cílovým blokům v pořadí, ve kterém byly připojeny, dokud jeden z bloků tuto zprávu nepřijme. Pomocí tohoto mechanismu filtrování můžete vytvořit systémy připojených bloků toku dat, které směrují určitá data prostřednictvím jedné cesty a další data jinou cestou. Příklad, který používá filtrování k vytvoření sítě toku dat, najdete v [tématu Návod: Použití toku dat v aplikaci Windows Forms](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Viz také

- [Tok dat](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
