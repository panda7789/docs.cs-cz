---
title: Model objektu regulárního výrazu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- searching with regular expressions, backreferences
- Regex class
- Match class
- pattern-matching with regular expressions, backreferences
- .NET Framework regular expressions, classes
- CaptureCollection class
- Group class
- characters [.NET Framework], backreferences
- substrings
- .NET Framework regular expressions, backreferences
- searching with regular expressions, classes
- backreferences
- Capture class
- repeating groups of characters
- MatchCollection class
- parsing text with regular expressions, backreferences
- regular expressions [.NET Framework]
- characters [.NET Framework], regular expressions
- classes [.NET Framework], regular expression
- regular expressions [.NET Framework], classes
- characters [.NET Framework], metacharacters
- metacharacters, regular expression classes
- metacharacters, backreferences
- parsing text with regular expressions, classes
- regular expressions [.NET Framework], backreferences
- strings [.NET Framework], regular expressions
- pattern-matching with regular expressions, classes
- GroupCollection class
ms.assetid: 49a21470-64ca-4b5a-a889-8e24e3c0af7e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14402b56a765fc8fe57f40e9c5c44f500267e266
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579857"
---
# <a name="the-regular-expression-object-model"></a>Model objektu regulárního výrazu
<a name="introduction"></a> Toto téma popisuje objektový model použít v práci s regulární výrazy rozhraní .NET. Obsahuje následující oddíly:  
  
-   [Modul regulárních výrazů](#Engine)  
  
-   [MatchCollection a shoda objekty](#Match_and_MCollection)  
  
-   [Kolekce skupin](#GroupCollection)  
  
-   [Zaznamenané skupiny](#the_captured_group)  
  
-   [Kolekce zachycení](#CaptureCollection)  
  
-   [Jednotlivé zachytávání](#the_individual_capture)  
  
<a name="Engine"></a>   
## <a name="the-regular-expression-engine"></a>Modul regulárních výrazů  
 Modul regulárních výrazů v .NET je reprezentována <xref:System.Text.RegularExpressions.Regex> třídy. Modul regulární výraz je zodpovědný za analýzu a kompilaci regulární výraz a pro provádění akcí, které se shodují se vzorem regulárního výrazu se vstupním řetězcem. Modul je ústřední součást ve model objektu regulárního výrazu rozhraní .NET.  
  
 Můžete použít modul regulárních výrazů v některém ze dvou způsobů:  
  
-   Při volání statických metod <xref:System.Text.RegularExpressions.Regex> třídy. Parametry metody zahrnují vstupní řetězec a regulární výraz. Modul regulárních výrazů ukládá do mezipaměti regulární výrazy, které se používají v statickou metodu volání, aby opakovaná volání metody statické regulárních výrazů, které používají stejný regulární výraz poskytují poměrně dobrý výkon.  
  
-   Po vytvoření instance <xref:System.Text.RegularExpressions.Regex> objekt, a to pomocí předání regulární výraz konstruktoru třídy. V takovém případě <xref:System.Text.RegularExpressions.Regex> objekt se nedá změnit (jen pro čtení) a představuje modul regulární výraz, který je úzce spojeny s jediným regulárním výrazem. Protože regulární výrazy používá <xref:System.Text.RegularExpressions.Regex> instancí se neukládají do mezipaměti, nevytvoří instanci <xref:System.Text.RegularExpressions.Regex> objekt vícekrát s stejný regulární výraz.  
  
 Můžete volat metody <xref:System.Text.RegularExpressions.Regex> třídy provádět následující operace:  
  
-   Určí, zda řetězec odpovídá regulárnímu výrazu.  
  
-   Extrahování jedné shody nebo na první shodu.  
  
-   Extrahujte všechny shody.  
  
-   Nahraďte odpovídající dílčí řetězec.  
  
-   Rozdělte jednoho řetězce na pole řetězců.  
  
 Tyto operace jsou popsané v následujících částech.  
  
### <a name="matching-a-regular-expression-pattern"></a>Odpovídající vzor regulárního výrazu  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> Metoda vrátí `true` Pokud řetězec odpovídá vzoru, nebo `false` Pokud neexistuje. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> Metoda se často používá k ověření řetězce na vstupu. Následující kód například zaručí, že řetězec odpovídá platné číslo sociálního pojištění ve Spojených státech amerických.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Regulární výraz `^\d{3}-\d{2}-\d{4}$` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Odpovídat na začátek vstupní řetězec.|  
|`\d{3}`|Porovná tři desítkové číslice.|  
|`-`|Porovná pomlčku.|  
|`\d{2}`|Porovná dvě desítková číslice.|  
|`-`|Porovná pomlčku.|  
|`\d{4}`|Porovná čtyři desítková číslice.|  
|`$`|Porovná konec vstupního řetězce.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Extrahování jedné shody nebo na první shodu  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> Metoda vrátí <xref:System.Text.RegularExpressions.Match> objekt, který obsahuje informace o první dílčí řetězec, který odpovídá regulárnímu výrazu. Pokud `Match.Success` vlastnost vrátí `true`, která udává, že byla nalezena shoda, můžete načíst informace o dalších odpovídá voláním <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metoda. Tato metoda volání můžete pokračovat, dokud nebudou `Match.Success` vlastnost vrátí `false`. Například následující kód používá <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody k vyhledání prvního výskytu duplicitního slova v řetězci. Potom zavolá <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody k vyhledání jakékoliv další události. V příkladu prověří `Match.Success` vlastnost po každém volání metody a určit, zda aktuální shoda byla úspěšná a zda volání <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metoda by měl následovat.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Regulární výraz `\b(\w+)\W+(\1)\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnávání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\W+`|Odpovídat jeden nebo více znaků aplikace word.|  
|`(\1)`|Porovná první zaznamenané řetězec. Toto je druhá zachytávající skupina.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
### <a name="extracting-all-matches"></a>Extrahování všechny shody  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda vrátí <xref:System.Text.RegularExpressions.MatchCollection> objekt, který obsahuje informace o všechny shody, které modul regulárních výrazů nacházejí ve vstupním řetězci. Například může být přepsána předchozí příklad pro volání <xref:System.Text.RegularExpressions.Regex.Matches%2A> metoda místo <xref:System.Text.RegularExpressions.Regex.Match%2A> a <xref:System.Text.RegularExpressions.Match.NextMatch%2A> metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Nahrazení odpovídajícího podřetězce  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> Metoda nahrazuje každý dílčí řetězec, který odpovídá vzorku regulárního výrazu se zadaný řetězec nebo vzor regulárního výrazu a vrátí celý vstupní řetězec s nahrazení. Následující kód například přidá symbol USA měny před desítkové číslo v řetězci.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Regulární výraz `\b\d+\.\d{2}\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`\.`|Porovná tečku.|  
|`\d{2}`|Porovná dvě desítková číslice.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor nahrazení `$$$&` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Náhradní řetězec|  
|-------------|------------------------|  
|`$$`|Znak dolaru ($).|  
|`$&`|Celý odpovídající podřetězec.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Rozdělení jediného řetězce na pole řetězců.  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> Metoda rozdělí vstupní řetězec v místech definovaných odpovídají regulárnímu výrazu. Následující kód například umístí položky v číslovaný seznam do pole řetězců.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Regulární výraz `\b\d{1,2}\.\s` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d{1,2}`|Odpovídat jedna nebo dvě desetinných míst.|  
|`\.`|Porovná tečku.|  
|`\s`|Porovná prázdný znak.|  
  
<a name="Match_and_MCollection"></a>   
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection a shoda objekty  
 Metody Regex vrací dva objekty, které jsou součástí model objektu regulárního výrazu: <xref:System.Text.RegularExpressions.MatchCollection> objekt a <xref:System.Text.RegularExpressions.Match> objektu.  
  
<a name="the_match_collection"></a>   
### <a name="the-match-collection"></a>Kolekce shod  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda vrátí <xref:System.Text.RegularExpressions.MatchCollection> objekt, který obsahuje <xref:System.Text.RegularExpressions.Match> objekty, které představují všechny shody, které modul regulárních výrazů nacházejí v pořadí, ve kterém nastávají ve vstupním řetězci. Pokud nejsou nalezeny žádné shody, vrátí metoda <xref:System.Text.RegularExpressions.MatchCollection> objektu bez členů. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> Vlastnost umožňuje přístup jednotlivé členy kolekce pomocí indexu z nula na jednu menší než hodnota <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> vlastnost. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A> je kolekce indexer (v jazyku C#) a výchozí vlastnost (v jazyce Visual Basic).  
  
 Ve výchozím nastavení, volání <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda používá k naplnění opožděné vyhodnocení <xref:System.Text.RegularExpressions.MatchCollection> objektu. Přístup k vlastnosti, které vyžadují plně naplněnou kolekci, například <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> , může mít snížení výkonu. V důsledku toho doporučujeme přistupovat ke kolekci pomocí <xref:System.Collections.IEnumerator> objekt, který je vrácený <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> metoda. Jednotlivé jazyky poskytují konstrukce, jako například `For``Each` v jazyce Visual Basic a `foreach` v jazyce C#, která zabalení kolekce <xref:System.Collections.IEnumerator> rozhraní.  
  
 Následující příklad používá <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> metoda k naplnění <xref:System.Text.RegularExpressions.MatchCollection> objekt s všech nalezených ve vstupním řetězci shod. V příkladu vytvoří výčet kolekce, shody jsou zkopírovány do pole řetězců a pozice znaků v matici celé číslo.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>   
### <a name="the-match"></a>Shody  
 <xref:System.Text.RegularExpressions.Match> Třída reprezentuje výsledek porovnání jeden regulární výraz. Dostanete <xref:System.Text.RegularExpressions.Match> objekty dvěma způsoby:  
  
-   Ve načítat z <xref:System.Text.RegularExpressions.MatchCollection> objekt, který je vrácený <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda. Načtení jednotlivých <xref:System.Text.RegularExpressions.Match> objekty, kolekci iteraci pomocí `foreach` (v jazyku C#) nebo `For Each`... `Next` (v jazyce Visual Basic) nebo použijte <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> vlastnost načíst konkrétní <xref:System.Text.RegularExpressions.Match> objektu podle indexu nebo podle názvu. Můžete také načíst jednotlivé <xref:System.Text.RegularExpressions.Match> objekty z kolekce podle iterace kolekce pomocí indexu z nula na jednu menší než počet objektů v kolekci. Však tato metoda nevyužívá opožděné vyhodnocení, protože přistupuje k <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> vlastnost.  
  
     Následující příklad načte jednotlivých <xref:System.Text.RegularExpressions.Match> objekty od <xref:System.Text.RegularExpressions.MatchCollection> objektu podle iterace v kolekci pomocí `foreach` nebo `For Each`... `Next` vytvořit. Regulární výraz jednoduše shoduje s řetězcem "abc" ve vstupním řetězci.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
-   Při volání <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metoda, která vrátí hodnotu <xref:System.Text.RegularExpressions.Match> objekt, který reprezentuje na první shodu v řetězci nebo část řetězce. Můžete určit, zda byla nalezena shoda načtením hodnotu `Match.Success` vlastnost. Načíst <xref:System.Text.RegularExpressions.Match> objekty, které představují následující shody, volání <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metoda opakovaně, dokud `Success` vlastnost vrácený <xref:System.Text.RegularExpressions.Match> objekt `false`.  
  
     Následující příklad používá <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody tak, aby odpovídaly řetězec "abc" ve vstupním řetězci.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Dvě vlastnosti <xref:System.Text.RegularExpressions.Match> třídy vracejí objekty kolekce:  
  
-   <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Vlastnost vrátí <xref:System.Text.RegularExpressions.GroupCollection> objekt, který obsahuje informace o dílčích řetězců, které odpovídají zaznamenávání skupiny ve regulární výraz.  
  
-   `Match.Captures` Vlastnost vrátí <xref:System.Text.RegularExpressions.CaptureCollection> objekt, který je omezené použití. Kolekce není vyplněný pro <xref:System.Text.RegularExpressions.Match> objekt, jehož `Success` vlastnost je `false`. Jinak, obsahuje jeden <xref:System.Text.RegularExpressions.Capture> objekt, který má stejné informace, jako <xref:System.Text.RegularExpressions.Match> objektu.  
  
 Další informace o těchto objektů najdete v tématu [kolekce skupin](#GroupCollection) a [Kolekce Capture](#CaptureCollection) části později v tomto tématu.  
  
 Dva další vlastnosti <xref:System.Text.RegularExpressions.Match> třída poskytnout informace o shodě. `Match.Value` Vlastnost vrátí dílčí řetězec ve vstupním řetězci, který odpovídá regulární výraz. `Match.Index` Vlastnost vrací nule počáteční pozici odpovídající řetězec ve vstupním řetězci.  
  
 <xref:System.Text.RegularExpressions.Match> Třída také obsahuje dvě metody porovnávání:  
  
-   <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> Metoda najde shodu po shodě reprezentované aktuální <xref:System.Text.RegularExpressions.Match> objekt a vrátí <xref:System.Text.RegularExpressions.Match> objekt, který reprezentuje, které odpovídají.  
  
-   <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Metoda provede zadanou operaci nahrazení na odpovídajícím řetězci a vrátí výsledek.  
  
 Následující příklad používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodu pro předřazení symbolu $ a mezery před každé číslo, které obsahuje dvě míst za desetinnou čárkou.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Regulární výraz `\b\d+(,\d{3})*\.\d{2}\b` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`(,\d{3})*`|Porovná nula nebo více výskytů středník a pomocí tří desetinných míst.|  
|`\.`|Porovná znak desetinné čárky.|  
|`\d{2}`|Porovná dvě desítková číslice.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor nahrazení `$$ $&` označuje, že odpovídající podřetězec by měl být nahrazen symbol dolaru ($) ( `$$` vzor), mezeru a hodnotou shody ( `$&` vzor).  
  
 [Zpět na začátek](#introduction)  
  
<a name="GroupCollection"></a>   
## <a name="the-group-collection"></a>Kolekce skupin  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Vlastnost vrátí <xref:System.Text.RegularExpressions.GroupCollection> objekt, který obsahuje <xref:System.Text.RegularExpressions.Group> objekty, které představují zachycené skupiny v jediné shodě. První <xref:System.Text.RegularExpressions.Group> objekt v kolekci (s indexem 0) představuje celou shodu. Každý objekt, který následuje představuje výsledky jediné zachytávající skupiny.  
  
 Je možné získat jednotlivé <xref:System.Text.RegularExpressions.Group> objektů v kolekcích s použitím <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> vlastnost. Můžete načíst nepojmenované skupiny pomocí jejich pořadového umístění v kolekci a podle názvu nebo podle pořadí načtení skupiny s názvem. Nepojmenované zachycení zobrazovat první v kolekci a jsou indexované zleva doprava v pořadí, ve kterém se zobrazují v regulární výraz. Pojmenovaná zachycení jsou indexována po nepojmenované zachycení zleva doprava v pořadí, ve kterém se zobrazují v regulární výraz. Pokud chcete zjistit, jaké číslem skupiny jsou k dispozici v kolekci pro konkrétní regulární výraz odpovídající metoda vrátí, můžete volat instance <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> metoda. Chcete-li zjistit, jaké s názvem skupiny jsou k dispozici v kolekci, můžete zavolat instanci <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> metoda. Obě metody jsou užitečné zejména v pro obecné účely rutin, které analyzovat odpovídá nalezena jakýkoli regulární výraz.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> Vlastnost je indexer kolekce v jazyce C# a objekt v kolekci výchozí vlastnost v jazyce Visual Basic. To znamená, že jednotlivé <xref:System.Text.RegularExpressions.Group> objektů můžete přistupovat pomocí indexu (nebo podle názvu, v případě pojmenovaných skupin) takto:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 V následujícím příkladu definuje regulární výraz, který používá seskupovací konstrukce pro zachycení měsíc, den a rok data.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Regulární výraz `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(\d{1,2})`|Odpovídat jedna nebo dvě desetinných míst. Toto je druhá zachytávající skupina.|  
|`,`|Porovná čárku.|  
|`\s`|Porovná prázdný znak.|  
|`(\d{4})`|Porovná čtyři desítková číslice. Toto je třetí zachytávající skupina.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 [Zpět na začátek](#introduction)  
  
<a name="the_captured_group"></a>   
## <a name="the-captured-group"></a>Zaznamenané skupiny  
 <xref:System.Text.RegularExpressions.Group> Třída reprezentuje výsledek z jediné zachytávající skupiny. Skupinu objektů, které představuje zachytávající skupiny definované v regulárním výrazu se vrátí pomocí <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> vlastnost <xref:System.Text.RegularExpressions.GroupCollection> objekt vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> Je vlastnost indexeru (v jazyku C#) a výchozí vlastnost (v jazyce Visual Basic) <xref:System.Text.RegularExpressions.Group> třídy. Můžete také načíst jednotlivé členy iterací v kolekci pomocí `foreach` nebo `For``Each` vytvořit. Příklad najdete v předchozí části.  
  
 Následující příklad používá vnořené seskupovací konstrukce pro zachycení dílčích řetězců do skupin. Regulární výraz `(a(b))c` shoduje s řetězcem "abc". Přiřadí podřetězec "ab" první skupinu zaznamenávání a dílčí řetězec "b" druhý zachycující skupiny.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 Následující příklad používá pojmenované seskupovací konstrukce k zachycení podřetězců z řetězec, který obsahuje data ve formátu "NAZEVDAT: hodnota", která rozdělí regulárnímu výrazu v dvojtečkou (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Regulární výraz `^(?<name>\w+):(?<value>\w+)` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`(?<name>\w+)`|Porovná jeden nebo více znaků slova. Je název této skupiny zaznamenávání `name`.|  
|`:`|Porovná dvojtečkou.|  
|`(?<value>\w+)`|Porovná jeden nebo více znaků slova. Je název této skupiny zaznamenávání `value`.|  
  
 Vlastnosti <xref:System.Text.RegularExpressions.Group> třída poskytnout informace o skupině zaznamenané: `Group.Value` vlastnost obsahuje zaznamenané dílčí řetězec, `Group.Index` vlastnost určuje počáteční pozici zachycené skupiny v vstupního textu `Group.Length` vlastnost obsahuje délka zachycený text a `Group.Success` vlastnost určuje, zda je dílčí řetězec odpovídá vzoru definována zachytávající skupině.  
  
 Použití kvantifikátory do skupiny (Další informace najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) upravuje vztah jednoho zachycení na zachytávající skupinu dvěma způsoby:  
  
-   Pokud `*` nebo `*?` kvantifikátor (který určuje nula nebo více shod) se použijí pro skupinu, zaznamenávání skupina nemusí mít odpovídající ve vstupním řetězci. Pokud není žádný zachycený text, vlastnosti <xref:System.Text.RegularExpressions.Group> objekt jsou nastaveny, jak je znázorněno v následující tabulce.  
  
    |Skupina vlastností|Hodnota|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     V následujícím příkladu je uvedena ukázka. V regulární výraz `aaa(bbb)*ccc`, první skupinu zaznamenávání (podřetězec "bbb") je možné porovnávat nula či více krát. Protože vstupní řetězec "aaaccc" odpovídá vzoru, zaznamenávání skupina nemá shody.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
-   Kvantifikátory může odpovídat více výskytů typů vzor, který je definován zachytávající skupinou. V takovém případě `Value` a `Length` vlastnosti <xref:System.Text.RegularExpressions.Group> objektu obsahují informace jenom o poslední zaznamenané dílčí řetězec. Například následující regulární výraz odpovídá jedné větě, která ukončen tečkou. Používá dvě seskupovací konstrukce: první zaznamená jednotlivých slov společně s prázdným znakem; druhý zaznamená jednotlivých slov. Jak ukazuje výstup z příkladu, i když regulární výraz uspěje v zachytávání celé věty, druhé zachytávající skupině zaznamená pouze poslední slovo.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Zpět na začátek](#introduction)  
  
<a name="CaptureCollection"></a>   
## <a name="the-capture-collection"></a>Kolekce zachycení  
 <xref:System.Text.RegularExpressions.Group> Obsahuje informace jenom o posledním zachycení. Celá sada zachycení provedené zachytávající skupiny je však stále k dispozici z <xref:System.Text.RegularExpressions.CaptureCollection> objekt, který je vrácený <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost. Každý ze členů kolekce <xref:System.Text.RegularExpressions.Capture> objekt, který reprezentuje zachycení provedené zachytávající skupinou v pořadí, ve kterém byly zachyceny (a tedy v pořadí, ve kterém byly zachycené řetězce porovnány zleva doprava ve vstupním řetězci). Je možné získat jednotlivé <xref:System.Text.RegularExpressions.Capture> objekty z kolekce v některém ze dvou způsobů:  
  
-   Podle iterace v rámci kolekce pomocí konstrukce, jako `foreach` (v jazyku C#) nebo `For``Each` (v jazyce Visual Basic).  
  
-   Pomocí <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> vlastnost k získání určitého objektu podle indexu. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> Vlastnost je <xref:System.Text.RegularExpressions.CaptureCollection> objektu výchozí vlastnost (v jazyce Visual Basic) nebo indexer (v jazyku C#).  
  
 Pokud není pro skupinu zachycení kvantifikátor <xref:System.Text.RegularExpressions.CaptureCollection> objekt obsahuje jeden <xref:System.Text.RegularExpressions.Capture> objekt, který je málo zájmu, protože poskytuje informace o shodě stejné jako jeho <xref:System.Text.RegularExpressions.Group> objektu. Pokud kvantifikátoru ke skupině zaznamenávání <xref:System.Text.RegularExpressions.CaptureCollection> objekt obsahuje všechny zachycení provedené zachytávající skupině a posledním členem kolekce představuje stejné zachycení jako <xref:System.Text.RegularExpressions.Group> objektu.  
  
 Například, pokud používáte regulární výraz `((a(b))c)+` (kde kvantifikátor + určuje jeden nebo více shod) k zachycení odpovídá řetězci "abcabcabc", <xref:System.Text.RegularExpressions.CaptureCollection> objekt pro každou <xref:System.Text.RegularExpressions.Group> objekt obsahuje tři členy.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Následující příklad používá regulární výraz `(Abc)+` najít jeden nebo více po sobě jdoucích výskytů řetězce "Abc" v řetězci "XYZAbcAbcAbcXYZAbcAb". Tento příklad ukazuje použití <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost vrátit několik skupin zachytit dílčích řetězců.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Zpět na začátek](#introduction)  
  
<a name="the_individual_capture"></a>   
## <a name="the-individual-capture"></a>Jednotlivé zachytávání  
 <xref:System.Text.RegularExpressions.Capture> Třída obsahuje výsledky z jediného zachycení podřetězce. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> Vlastnost obsahuje odpovídající text a <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> vlastnost udává pozice s nulovým základem ve vstupním řetězci, od kterého začíná odpovídající podřetězec.  
  
 V následujícím příkladu analyzuje vstupní řetězec pro teplota vybrané měst. Čárkou (",") slouží k oddělení města a jeho teploty a středník (";") slouží k oddělení dat pro každé město. Celý vstupní řetězec představuje jednu shodu. V regulární výraz `((\w+(\s\w+)*),(\d+);)+`, který slouží k analýze řetězec, název města přiřazen ke skupině druhý zaznamenávání a teplota je přiřazena čtvrtý zachycující skupiny.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`(\s\w+)*`|Porovná nula nebo více výskytů prázdný znak, za nímž následuje jeden nebo více znaků slova. Tento vzor odpovídá více word města názvy. Toto je třetí zachytávající skupina.|  
|`(\w+(\s\w+)*)`|Porovná jeden nebo více znaků slova následovaný nula nebo více výskytů prázdný znak a jeden nebo více znaků slova. Toto je druhá zachytávající skupina.|  
|`,`|Porovná čárku.|  
|`(\d+)`|Porovnává jeden nebo více číslic. Toto je čtvrtý zachycující skupina.|  
|`;`|Porovná středník.|  
|`((\w+(\s\w+)*),(\d+);)+`|Shodují se vzorem slovo, a všechny další slova následuje čárka, jednu nebo více číslic a středníkem, jeden či více krát. Toto je první zachytávající skupina.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Text.RegularExpressions>  
 [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
