---
title: 'Návod: Vytvoření kanálu toku dat'
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
ms.openlocfilehash: cfe3296815dc344b0d9d1f7bad1ab4a130380e2b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284608"
---
# <a name="walkthrough-creating-a-dataflow-pipeline"></a>Návod: Vytvoření kanálu toku dat
I když můžete použít <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Receive%2A?displayProperty=nameWithType> metody, <xref:System.Threading.Tasks.Dataflow.DataflowBlock.ReceiveAsync%2A?displayProperty=nameWithType> a <xref:System.Threading.Tasks.Dataflow.DataflowBlock.TryReceive%2A?displayProperty=nameWithType> pro příjem zpráv ze zdrojových bloků, můžete také připojit bloky zpráv pro vytvoření *kanálu toku*dat. Kanál toku dat je řada komponent neboli *bloků toku*dat, z nichž každý provádí konkrétní úkol, který přispívá k většímu cíli. Každý blok toku dat v kanálu toku dat provádí práci, když obdrží zprávu z jiného bloku toku dat. Analogie k tomuto je montážní čára pro výrobu automobilu. Vzhledem k tomu, že každá vozidlo prochází přes čáru sestavení, jedna stanice sestaví rámec, druhý instaluje modul a tak dále. Vzhledem k tomu, že čára sestavení umožňuje sestavovat více vozidel současně, poskytuje lepší propustnost než sestavování celé vozidlo v jednom okamžiku.

 Tento dokument ukazuje kanál toku dat, který stáhne knihu *Iliad Homer* z webu a vyhledá text tak, aby se shodoval s jednotlivými slovy, která vrátí slova, která budou vracet první znaky slova. Vytváření kanálu toku dat v tomto dokumentu se skládá z následujících kroků:  
  
1. Vytvořte bloky toku dat, které se účastní kanálu.  
  
2. Připojte každý blok toku dat k dalšímu bloku v kanálu. Každý blok přijímá jako vstup výstup předchozího bloku v kanálu.  
  
3. Pro každý blok toku dat vytvořte úlohu pokračování, která nastaví další blok na stav dokončeno po dokončení předchozího bloku.  
  
4. Publikujte data na hlavu kanálu.  
  
5. Označte vedoucí kanál jako dokončený.  
  
6. Počkejte, až kanál dokončí veškerou práci.  
  
## <a name="prerequisites"></a>Požadavky  
 Před zahájením tohoto návodu Přečtěte [tok](dataflow-task-parallel-library.md) dat.  
  
## <a name="creating-a-console-application"></a>Vytvoření konzolové aplikace  
 V aplikaci Visual Studio vytvořte projekt konzolové aplikace Visual C# nebo Visual Basic. Nainstalujte balíček NuGet System. Threading. Tasks. Dataflow.

[!INCLUDE [tpl-install-instructions](../../../includes/tpl-install-instructions.md)]

 Přidejte do projektu následující kód, který vytvoří základní aplikaci.  
  
 [!code-csharp[TPLDataflow_Palindromes#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#2)]
 [!code-vb[TPLDataflow_Palindromes#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromesemptymain.vb#2)]  
  
## <a name="creating-the-dataflow-blocks"></a>Vytváření bloků toku dat  
 Do metody přidejte následující kód `Main` , který vytvoří bloky toku dat, které se účastní kanálu. Následující tabulka shrnuje role jednotlivých členů kanálu.  
  
 [!code-csharp[TPLDataflow_Palindromes#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#3)]
 [!code-vb[TPLDataflow_Palindromes#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#3)]  
  
|Člen|Typ|Popis|  
|------------|----------|-----------------|  
|`downloadString`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Stáhne z webu text knihy.|  
|`createWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Odděluje text knihy do pole slov.|  
|`filterWordList`|<xref:System.Threading.Tasks.Dataflow.TransformBlock%602>|Odstraní krátká slova a duplicitní hodnoty z pole slov.|  
|`findReversedWords`|<xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602>|Najde všechna slova ve filtrované kolekci polí slov, u kterých se v poli Wordu obrátí také.|  
|`printReversedWords`|<xref:System.Threading.Tasks.Dataflow.ActionBlock%601>|Zobrazí slova a odpovídající zpětná slova pro konzolu.|  
  
 I když v tomto příkladu můžete zkombinovat více kroků v tomto příkladu do jednoho kroku, ukazuje tento příklad koncept sestavování více nezávislých úloh toku dat, aby bylo možné provést větší úlohu. Tento příklad používá <xref:System.Threading.Tasks.Dataflow.TransformBlock%602> k tomu, aby každý člen kanálu mohl provést operaci se vstupními daty a odeslat výsledky do dalšího kroku kanálu. `findReversedWords`Členem kanálu je <xref:System.Threading.Tasks.Dataflow.TransformManyBlock%602> objekt, protože pro každý vstup vytváří více nezávislých výstupů. Zakončením kanálu `printReversedWords` je <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objekt, protože provádí akci na jeho vstupu a nevytváří výsledek.  
  
## <a name="forming-the-pipeline"></a>Vytvoření kanálu  
 Přidejte následující kód pro připojení každého bloku k dalšímu bloku v kanálu.  
  
 Když zavoláte <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metodu pro připojení zdrojového bloku toku dat k cílovému bloku toku dat, zdrojový blok toku dat rozšíří data do cílového bloku, protože data budou k dispozici. Pokud zadáte také <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions> s <xref:System.Threading.Tasks.Dataflow.DataflowLinkOptions.PropagateCompletion> nastavením na hodnotu true, úspěšné nebo neúspěšné dokončení jednoho bloku v kanálu způsobí dokončení dalšího bloku v kanálu.
  
 [!code-csharp[TPLDataflow_Palindromes#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#4)]
 [!code-vb[TPLDataflow_Palindromes#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#4)]  
  
## <a name="posting-data-to-the-pipeline"></a>Odesílání dat do kanálu  
 Přidejte následující kód, který odešle adresu URL knihy *Iliad Homer* na hlavu kanálu toku dat.  
  
 [!code-csharp[TPLDataflow_Palindromes#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#6)]
 [!code-vb[TPLDataflow_Palindromes#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#6)]  
  
 Tento příklad používá <xref:System.Threading.Tasks.Dataflow.DataflowBlock.Post%2A?displayProperty=nameWithType> k synchronnímu posílání dat do hlavního kanálu. Použijte <xref:System.Threading.Tasks.Dataflow.DataflowBlock.SendAsync%2A?displayProperty=nameWithType> metodu, pokud je nutné asynchronně odesílat data do uzlu toku dat.  
  
## <a name="completing-pipeline-activity"></a>Dokončuje se aktivita kanálu.  
 Přidejte následující kód, který označí vedoucí kanál jako dokončený. Vedoucí kanálu rozšíří své dokončení poté, co zpracuje všechny zprávy ve vyrovnávací paměti.
  
 [!code-csharp[TPLDataflow_Palindromes#7](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#7)]
 [!code-vb[TPLDataflow_Palindromes#7](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#7)]  
  
 Tento příklad pošle jednu adresu URL prostřednictvím kanálu toku dat ke zpracování. Pokud odešlete více než jeden vstup prostřednictvím kanálu, zavolejte <xref:System.Threading.Tasks.Dataflow.IDataflowBlock.Complete%2A?displayProperty=nameWithType> metodu po odeslání veškerého vstupu. Tento krok můžete vynechat, pokud vaše aplikace nemá přesně definovaný bod, na kterém data již nejsou k dispozici, nebo aplikace nemusí čekat na dokončení kanálu.  
  
## <a name="waiting-for-the-pipeline-to-finish"></a>Čeká se na dokončení kanálu.  
 Přidejte následující kód, který čeká na dokončení kanálu. Celková operace je dokončena, jakmile bude konec kanálu dokončen.  
  
 [!code-csharp[TPLDataflow_Palindromes#8](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#8)]
 [!code-vb[TPLDataflow_Palindromes#8](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#8)]  
  
 Můžete počkat na dokončení toku dat z libovolného vlákna nebo z více vláken současně.  
  
## <a name="the-complete-example"></a>Kompletní příklad  
 Následující příklad ukazuje kompletní kód pro tento návod.  
  
 [!code-csharp[TPLDataflow_Palindromes#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_palindromes/cs/dataflowpalindromes.cs#1)]
 [!code-vb[TPLDataflow_Palindromes#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_palindromes/vb/dataflowpalindromes.vb#1)]  
  
## <a name="next-steps"></a>Další kroky  
 Tento příklad pošle jednu adresu URL pro zpracování prostřednictvím kanálu toku dat. Pokud prostřednictvím kanálu odesíláte více než jednu vstupní hodnotu, můžete do své aplikace začlenit formu paralelismu, která se podobá způsobu, jakým se můžou části pohybovat v továrně automobilu. Když první člen kanálu pošle svůj výsledek druhému členovi, může zpracovat další položku paralelně, protože druhý člen zpracuje první výsledek.  
  
 Paralelismus, které jsou dosaženy pomocí kanálů toku dat, se označují jako *hrubá paralelismues* , protože obvykle se skládá z méně většího počtu úkolů. V kanálu toku dat můžete také použít přesnější *paralelismuy* s menšími, krátkými běžícími úkoly. V tomto příkladu `findReversedWords` člen kanálu používá [PLINQ](introduction-to-plinq.md) ke zpracování více položek v pracovním seznamu paralelně. Použití jemně odstupňovaného paralelismu v hrubém kanálu může zlepšit celkovou propustnost.  
  
 Můžete také propojit zdrojový blok toku dat s více cílovými bloky a vytvořit tak *síť toku*dat. Přetížená verze <xref:System.Threading.Tasks.Dataflow.DataflowBlock.LinkTo%2A> metody přebírá <xref:System.Predicate%601> objekt, který definuje, zda cílový blok akceptuje každou zprávu na základě její hodnoty. Většina typů bloků toku dat, které fungují jako zdroje, nabízí zprávy všem připojeným cílovým blokům v pořadí, ve kterém byly připojeny, dokud některý z těchto bloků tuto zprávu nepřijme. Pomocí tohoto mechanismu filtrování můžete vytvořit systémy propojených bloků toku dat, které směrují určitá data prostřednictvím jedné cesty a dalších dat prostřednictvím jiné cesty. Příklad, který používá filtrování k vytvoření sítě toku dat, naleznete v tématu [Návod: použití toku dat v aplikaci model Windows Forms](walkthrough-using-dataflow-in-a-windows-forms-application.md).  
  
## <a name="see-also"></a>Viz také

- [Tok dat](dataflow-task-parallel-library.md)
