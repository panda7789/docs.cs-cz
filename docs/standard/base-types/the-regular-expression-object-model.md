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
ms.openlocfilehash: 773c3ee1a82e8307d32750c7d055201c466707bc
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43560994"
---
# <a name="the-regular-expression-object-model"></a>Model objektu regulárního výrazu
<a name="introduction"></a> Toto téma popisuje objektový model používaný při práci s regulárními výrazy v rozhraní .NET. Obsahuje následující oddíly:  
  
-   [Modul regulárních výrazů](#Engine)  
  
-   [MatchCollection a porovnat objekty](#Match_and_MCollection)  
  
-   [Kolekce skupin](#GroupCollection)  
  
-   [Zachycené skupiny](#the_captured_group)  
  
-   [Kolekce zachytávání](#CaptureCollection)  
  
-   [Jednotlivé zachytávání](#the_individual_capture)  
  
<a name="Engine"></a>   
## <a name="the-regular-expression-engine"></a>Modul regulárních výrazů  
 Modul regulárních výrazů v .NET je reprezentována <xref:System.Text.RegularExpressions.Regex> třídy. Modul regulárních výrazů je odpovědný za analýzu a kompilaci regulárních výrazů a pro provádění operací, které odpovídají vzoru regulárního výrazu se vstupním řetězcem. Modul je ústřední součást v model objektu regulárního výrazu .NET.  
  
 Můžete použít modul regulárních výrazů v některém ze dvou způsobů:  
  
-   Zavoláním statické metody <xref:System.Text.RegularExpressions.Regex> třídy. Parametry metody zahrnují vstupního řetězce a vzor regulárního výrazu. Modul regulárních výrazů regulární výrazy, které se používají ve volání statické metody, takže opakovaná volání statické metody regulárních výrazů, které používají stejný regulární výraz nabízí relativně dobrého výkonu ukládá do mezipaměti.  
  
-   Po vytvoření instance <xref:System.Text.RegularExpressions.Regex> objekt předáním regulárního výrazu do konstruktoru třídy. V takovém případě <xref:System.Text.RegularExpressions.Regex> objektu je neměnný (jen pro čtení) a představuje modul regulárních výrazů, který je pevně spárován s jediným regulárním výrazem. Protože regulární výrazy používána <xref:System.Text.RegularExpressions.Regex> instancí se neukládají do mezipaměti, by neměl vytvořit instanci <xref:System.Text.RegularExpressions.Regex> objekt víckrát se stejným regulárním výrazem.  
  
 Můžete volat metody <xref:System.Text.RegularExpressions.Regex> třídy provádět následující operace:  
  
-   Určení, zda řetězec odpovídá vzoru regulárního výrazu.  
  
-   Extrahujte jediný výskyt shody nebo první shoda.  
  
-   Extrahujte všechny shody.  
  
-   Nahradí odpovídající podřetězec.  
  
-   Rozdělte jeden řetězec do pole řetězců.  
  
 Tyto operace jsou popsány v následujících částech.  
  
### <a name="matching-a-regular-expression-pattern"></a>Odpovídající vzor regulárního výrazu  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> Vrátí metoda `true` Pokud řetězec odpovídá vzoru, nebo `false` Pokud tomu tak není. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> Metody se často používá k ověření řetězce na vstupu. Například následující kód zajistí, že řetězec odpovídá platné číslo sociálního pojištění v USA.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Vzor regulárního výrazu `^\d{3}-\d{2}-\d{4}$` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Odpovídá začátku vstupního řetězce.|  
|`\d{3}`|Porovná tři desítkové číslice.|  
|`-`|Porovnává spojovník.|  
|`\d{2}`|Porovná dvě desetinné číslice.|  
|`-`|Porovnává spojovník.|  
|`\d{4}`|Porovná čtyři desítková čísla.|  
|`$`|Porovná konec vstupního řetězce.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Extrahování jediný výskyt shody nebo první shoda  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> Metoda vrátí hodnotu <xref:System.Text.RegularExpressions.Match> objekt, který obsahuje informace o první dílčí řetězec, který odpovídá vzoru regulárního výrazu. Pokud `Match.Success` vrátí vlastnost `true`, označující, že se najde shoda, můžete načíst informace o následných shod voláním <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metoda. Tato volání metody může pokračovat, dokud nebudou `Match.Success` vrátí vlastnost `false`. Například následující kód používá <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody k vyhledání prvního výskytu duplicitní slova v řetězci. Poté zavolá <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody k vyhledání žádné další výskyty. V příkladu prověří `Match.Success` vlastnost po každé volání metody k určení, zda aktuální shoda bylo úspěšné a zda volání <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody by měly dodržovat.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Vzor regulárního výrazu `\b(\w+)\W+(\1)\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\W+`|Porovná jeden nebo více znaků slova.|  
|`(\1)`|Porovná první zachycenou řetězec. Toto je druhá zachytávající skupina.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
### <a name="extracting-all-matches"></a>Extrahování všechny shody  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda vrátí hodnotu <xref:System.Text.RegularExpressions.MatchCollection> objekt, který obsahuje informace o shodách nacházející se modul regulárních výrazů ve vstupním řetězci. Například v předchozím příkladu může být přepsána pro volání <xref:System.Text.RegularExpressions.Regex.Matches%2A> metoda místo <xref:System.Text.RegularExpressions.Regex.Match%2A> a <xref:System.Text.RegularExpressions.Match.NextMatch%2A> metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Nahrazení odpovídající podřetězec  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> Metoda nahrazuje každý dílčí řetězec, který odpovídá vzoru regulárního výrazu se zadaný řetězec nebo vzor regulárního výrazu a vrátí celý vstupní řetězec s nahrazení. Například následující kód přidá symbol měny USA před desetinné číslo v řetězci.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Vzor regulárního výrazu `\b\d+\.\d{2}\b` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`\.`|Porovná tečku.|  
|`\d{2}`|Porovná dvě desetinné číslice.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor pro nahrazení `$$$&` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Řetězci pro nahrazení|  
|-------------|------------------------|  
|`$$`|Znak dolaru ($).|  
|`$&`|Celý odpovídající podřetězec.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Jeden řetězec do pole řetězců  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> Metoda rozdělí vstupní řetězec v místech určené shoda s regulárním výrazem. Například následující kód umístí položky číslovaný seznam do pole řetězců.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Vzor regulárního výrazu `\b\d{1,2}\.\s` interpretována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d{1,2}`|Porovná jednu nebo dvě desetinné číslice.|  
|`\.`|Porovná tečku.|  
|`\s`|Porovná prázdný znak.|  
  
<a name="Match_and_MCollection"></a>   
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection a porovnat objekty  
 Metody regulární výraz vrací dva objekty, které jsou součástí model objektu regulárního výrazu: <xref:System.Text.RegularExpressions.MatchCollection> objektu a <xref:System.Text.RegularExpressions.Match> objektu.  
  
<a name="the_match_collection"></a>   
### <a name="the-match-collection"></a>Kolekce shod  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> Metoda vrátí hodnotu <xref:System.Text.RegularExpressions.MatchCollection> objekt, který obsahuje <xref:System.Text.RegularExpressions.Match> objekty, které představují všechny shody, které se modul regulárních výrazů nacházejí v pořadí, ve kterém se objevují ve vstupním řetězci. Pokud nejsou nalezeny žádné shody, vrátí metoda <xref:System.Text.RegularExpressions.MatchCollection> objektu bez členů. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> Vlastnost umožňuje vám přístup k jednotlivým členům kolekce pomocí indexu z nula, pokud chcete jeden menší než hodnota <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> vlastnost. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A> je kolekce indexer (v jazyce C#) a výchozí vlastnosti (v jazyce Visual Basic).  
  
 Ve výchozím nastavení, volání <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metoda používá k naplnění opožděné vyhodnocení <xref:System.Text.RegularExpressions.MatchCollection> objektu. Přístup k vlastnostem, které vyžadují kolekci plně mají údaj vyplněný, jako <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> vlastnosti, může zahrnovat snížení výkonu. V důsledku toho doporučujeme pomocí přístup ke kolekci <xref:System.Collections.IEnumerator> objekt, který je vrácený <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> metody. Jednotlivé jazyky poskytují konstrukce, jako například `For Each` v jazyce Visual Basic a `foreach` v jazyce C#, které obalují kolekce <xref:System.Collections.IEnumerator> rozhraní.  
  
 V následujícím příkladu <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> metoda k naplnění <xref:System.Text.RegularExpressions.MatchCollection> objekt s všechny shody nalezen ve vstupním řetězci. V příkladu vytvoří výčet kolekce, zkopíruje shody na pole řetězců a zaznamenává pozice znaku v celočíselné pole.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>   
### <a name="the-match"></a>Ke shodě  
 <xref:System.Text.RegularExpressions.Match> Třída reprezentuje výsledek porovnání jedné regulární výraz. Můžete přistupovat <xref:System.Text.RegularExpressions.Match> objekty dvěma způsoby:  
  
-   Načtením z <xref:System.Text.RegularExpressions.MatchCollection> objekt, který je vrácený <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody. Chcete-li získat jednotlivé <xref:System.Text.RegularExpressions.Match> objekty, iterujte pomocí kolekce `foreach` (v jazyce C#) nebo `For Each`... `Next` (v jazyce Visual Basic) nebo použijte <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> vlastnost pro načtení konkrétní <xref:System.Text.RegularExpressions.Match> objekt index nebo název. Můžete také načíst jednotlivé <xref:System.Text.RegularExpressions.Match> objekty z kolekce iterací kolekce pomocí indexu z nula, pokud chcete jeden menší než počet objektů v kolekci. Ale tato metoda nevyužívá opožděné vyhodnocení, protože přistupuje <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> vlastnost.  
  
     Následující příklad načte jednotlivé <xref:System.Text.RegularExpressions.Match> objekty z <xref:System.Text.RegularExpressions.MatchCollection> objekt iterací pomocí kolekce `foreach` nebo `For Each`... `Next` vytvořit. Regulární výraz, odpovídá řetězci "abc" ve vstupním řetězci.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
-   Při volání <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metoda, která vrátí <xref:System.Text.RegularExpressions.Match> objekt, který představuje první shodu v řetězci nebo část řetězce. Můžete určit, zda byla nalezena shoda načtením hodnoty `Match.Success` vlastnost. K načtení <xref:System.Text.RegularExpressions.Match> objekty, které představují následných shod, volání <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> – metoda opakovaně, dokud `Success` vlastnosti vráceného <xref:System.Text.RegularExpressions.Match> objekt je `false`.  
  
     V následujícím příkladu <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody tak, aby odpovídaly řetězec "abc" ve vstupním řetězci.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Dvě vlastnosti <xref:System.Text.RegularExpressions.Match> třídy vracejí objekty kolekce:  
  
-   <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Vrátí vlastnost <xref:System.Text.RegularExpressions.GroupCollection> skupiny, který obsahuje informace o dílčích řetězců, které odpovídají zachycení ve vzoru regulárního výrazu.  
  
-   `Match.Captures` Vrátí vlastnost <xref:System.Text.RegularExpressions.CaptureCollection> objekt, který má omezené používání. Kolekce není vyplněný pro <xref:System.Text.RegularExpressions.Match> jehož `Success` vlastnost `false`. V opačném případě obsahuje jediný <xref:System.Text.RegularExpressions.Capture> objekt, který má stejné informace jako <xref:System.Text.RegularExpressions.Match> objektu.  
  
 Další informace o těchto objektů najdete v tématu [kolekce skupin](#GroupCollection) a [Kolekce Capture](#CaptureCollection) částech dále v tomto tématu.  
  
 Dvě další vlastnosti <xref:System.Text.RegularExpressions.Match> třídy poskytují informace o zjištěné shodě. `Match.Value` Vlastnost vrátí podřetězec ve vstupním řetězci, který odpovídá vzoru regulárního výrazu. `Match.Index` Vlastnost vrací založený na nule počáteční pozici odpovídající řetězec ve vstupním řetězci.  
  
 <xref:System.Text.RegularExpressions.Match> Třída také obsahuje dvě metody porovnávání vzorků:  
  
-   <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> Metoda najde shodu po shodě reprezentované aktuální <xref:System.Text.RegularExpressions.Match> objekt a vrátí <xref:System.Text.RegularExpressions.Match> objekt, který reprezentuje, které odpovídají.  
  
-   <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> Metoda provede zadanou operaci nahrazení na odpovídající řetězec a vrátí výsledek.  
  
 V následujícím příkladu <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metoda předřaďte $ symbol a mezera před každé číslo, které zahrnuje dvě desetinné číslice.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Vzor regulárního výrazu `\b\d+(,\d{3})*\.\d{2}\b` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`(,\d{3})*`|Porovná žádný nebo několik výskytů čárkou následovanou třemi desítkovými číslicemi.|  
|`\.`|Odpovídá znaku desetinné čárky.|  
|`\d{2}`|Porovná dvě desetinné číslice.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor pro nahrazení `$$ $&` vyjadřuje, že odpovídající podřetězec by měl být nahrazen symbol dolaru ($) ( `$$` vzor), mezeru a hodnotu shody ( `$&` vzor).  
  
 [Zpět na začátek](#introduction)  
  
<a name="GroupCollection"></a>   
## <a name="the-group-collection"></a>Kolekce skupin  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> Vrátí vlastnost <xref:System.Text.RegularExpressions.GroupCollection> objekt, který obsahuje <xref:System.Text.RegularExpressions.Group> objekty, které představují zachycené skupiny v jediný výskyt shody. První <xref:System.Text.RegularExpressions.Group> objektu v kolekci (na pozici 0) představuje celkovou shodu. Každý objekt, který následuje představuje výsledky jednoho zachytávající skupinu.  
  
 Je možné získat jednotlivé <xref:System.Text.RegularExpressions.Group> objekty v kolekci pomocí <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> vlastnost. Můžete načíst nepojmenované skupiny podle jejich pořadí v kolekci a načíst pojmenované skupiny podle názvu nebo podle pořadí. Nepojmenované zachycení se zobrazí první v kolekci a indexovaných zleva doprava v pořadí, v jakém jsou uvedeny ve vzoru regulárního výrazu. Pojmenované zachycení jsou indexována po nepojmenované zachycení, zleva doprava v pořadí, v jakém jsou uvedeny ve vzoru regulárního výrazu. Pokud chcete zjistit, jaké číslované skupiny jsou k dispozici v kolekci vrácené pro konkrétní metodu shody regulárních výrazů, můžete volat instanci <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> metody. Pokud chcete zjistit, jaké pojmenované skupiny jsou k dispozici v kolekci, můžete volat instanci <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> metody. Obě metody jsou zvláště užitečné při pro obecné účely rutiny, které analyzují nenašly žádné regulárními výrazy shody.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> Je vlastnost indexer kolekce v jazyce C# a výchozí vlastnosti objektu kolekce v jazyce Visual Basic. To znamená, že tato osoba <xref:System.Text.RegularExpressions.Group> objektům můžete přistupovat pomocí indexu (nebo podle názvu, v případě pojmenované skupiny) následujícím způsobem:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 Následující příklad definuje regulární výraz, který používá seskupovací konstrukce k zachycení odkazu měsíc, den a rok data.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Vzor regulárního výrazu `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(\d{1,2})`|Porovná jednu nebo dvě desetinné číslice. Toto je druhá zachytávající skupina.|  
|`,`|Porovná čárku.|  
|`\s`|Porovná prázdný znak.|  
|`(\d{4})`|Porovná čtyři desítková čísla. Toto je třetí zachytávající skupina.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 [Zpět na začátek](#introduction)  
  
<a name="the_captured_group"></a>   
## <a name="the-captured-group"></a>Zachycené skupiny  
 <xref:System.Text.RegularExpressions.Group> Třída reprezentuje výsledek z jednoho zachytávající skupinu. Skupiny objektů, které představuje zachytávající skupiny definované v regulárním výrazu jsou vráceny pomocí <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> vlastnost <xref:System.Text.RegularExpressions.GroupCollection> vrácený <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastnost. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> Je vlastnost indexeru (v jazyce C#) a výchozí vlastnost (v jazyce Visual Basic) <xref:System.Text.RegularExpressions.Group> třídy. Můžete také načíst jednotlivé členy podle iterace pomocí kolekce `foreach` nebo `For Each` vytvořit. Příklad najdete v předchozí části.  
  
 Následující příklad používá vnořené seskupovací konstrukce k zachytávání podřetězců do skupin. Vzor regulárního výrazu `(a(b))c` shoduje s řetězcem "abc". Přiřadí podřetězec "ab" první zachytávající skupina a podřetězec "b" pro druhou zachytávající skupinu.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 Následující příklad používá pojmenovanou seskupovací konstrukce k zachytávání podřetězců z řetězce, který obsahuje data ve formátu "NAZEVDAT: hodnota", které rozdělí regulárních výrazů v dvojtečkou (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Vzor regulárního výrazu `^(?<name>\w+):(?<value>\w+)` je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`(?<name>\w+)`|Porovná jeden nebo více znaků slova. Je název zachytávající skupiny `name`.|  
|`:`|Porovná dvojtečka.|  
|`(?<value>\w+)`|Porovná jeden nebo více znaků slova. Je název zachytávající skupiny `value`.|  
  
 Vlastnosti <xref:System.Text.RegularExpressions.Group> třídy poskytují informace o zachycenou skupinou: `Group.Value` vlastnost obsahuje zachycené podřetězce `Group.Index` vlastnost určuje počáteční pozici zachycené skupině ve vstupním textu `Group.Length` vlastnost obsahuje délka zachycený text a `Group.Success` vlastnost určuje, zda je dílčí řetězec shoduje se vzorem určené zachytávající skupina.  
  
 Použití kvantifikátory do skupiny (Další informace najdete v tématu [kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) upraví vztah jednoho zachycení za zachytávající skupinou dvěma způsoby:  
  
-   Pokud `*` nebo `*?` kvantifikátor (který určuje žádnou nebo více shod) se použijí pro skupinu, skupinu zachycení nemusí mít shody ve vstupním řetězci. Pokud neexistuje žádný zachycený text vlastnosti <xref:System.Text.RegularExpressions.Group> objektu jsou nastaveny, jak je znázorněno v následující tabulce.  
  
    |Vlastnosti skupiny|Hodnota|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     V následujícím příkladu je uvedena ukázka. Ve vzoru regulárního výrazu `aaa(bbb)*ccc`, první zachytávající skupina (podřetězec "bbb"), mohou odpovídat nulakrát nebo vícekrát. Vzhledem k tomu, že vstupní řetězec "aaaccc" odpovídá vzoru, zachytávající skupina nemá shoda.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
-   Kvantifikátory může odpovídat více výskytů typů vzor, který je definován zachytávající skupina. V takovém případě `Value` a `Length` vlastnosti <xref:System.Text.RegularExpressions.Group> objekt obsahovat informace pouze o poslední zachycené podřetězce. Například následující regulární výraz odpovídá jedné věty, které končí tečkou. Používá dva seskupovací konstrukce: první zachycuje jednotlivá slova spolu s prázdný znak; Druhá zachytává jednotlivých slov. Jak výstup z příkladu ukazuje, i když proběhne úspěšně regulárních výrazů v zachytávání celé věty, druhá zachytávající skupina zaznamená pouze poslední slovo.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Zpět na začátek](#introduction)  
  
<a name="CaptureCollection"></a>   
## <a name="the-capture-collection"></a>Kolekce zachytávání  
 <xref:System.Text.RegularExpressions.Group> Objekt obsahuje informace pouze o poslední zachycení. Ale je stále k dispozici z celá sada provedené zachytávající skupinou zachycení <xref:System.Text.RegularExpressions.CaptureCollection> objekt, který je vrácený <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost. Každý člen kolekce <xref:System.Text.RegularExpressions.Capture> objekt, který reprezentuje zachycení provedené zachycující skupina, v pořadí, ve kterém byly zachyceny (a tedy v pořadí, ve kterém byly zachycené řetězce porovnány zleva doprava ve vstupním řetězci). Je možné získat jednotlivé <xref:System.Text.RegularExpressions.Capture> objekty z kolekce v některém ze dvou způsobů:  
  
-   Iterací pomocí konstrukce jako například kolekci `foreach` (v jazyce C#) nebo `For Each` (v jazyce Visual Basic).  
  
-   S použitím <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> vlastnost pro načtení konkrétní objekt podle indexu. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> Vlastnost <xref:System.Text.RegularExpressions.CaptureCollection> (v jazyce Visual Basic) výchozí vlastnost nebo indexer (v jazyce C#) objektu.  
  
 Pokud není použit kvantifikátor zachycující skupiny <xref:System.Text.RegularExpressions.CaptureCollection> objekt obsahuje jediný <xref:System.Text.RegularExpressions.Capture> objekt, který je malý relevantní, protože poskytuje informace o zjištěné shodě stejné jako jeho <xref:System.Text.RegularExpressions.Group> objektu. Pokud byl použit kvantifikátor zachycující skupiny <xref:System.Text.RegularExpressions.CaptureCollection> objekt obsahuje všechna zachycení provedené zachytávající skupinou a poslední člen kolekce představuje stejné zachycení jako <xref:System.Text.RegularExpressions.Group> objektu.  
  
 Například, pokud používáte vzor regulárního výrazu `((a(b))c)+` (kde + kvantifikátor určuje jednu nebo více shod) k zachycení odpovídá řetězci "abcabcabc", <xref:System.Text.RegularExpressions.CaptureCollection> objekt pro každou <xref:System.Text.RegularExpressions.Group> objekt obsahuje tři členy.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Následující příklad používá regulární výraz `(Abc)+` najít jeden nebo více po sobě jdoucích spuštění řetězce "Abc" v řetězci "XYZAbcAbcAbcXYZAbcAb". Tento příklad ukazuje použití <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnost vrátit více skupin zachycené podřetězce.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Zpět na začátek](#introduction)  
  
<a name="the_individual_capture"></a>   
## <a name="the-individual-capture"></a>Jednotlivé zachytávání  
 <xref:System.Text.RegularExpressions.Capture> Třída obsahuje výsledky z funkce capture jeden dílčí výraz. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> Vlastnost obsahuje odpovídající text a <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> vlastnost určuje, pozice s nulovým základem ve vstupním řetězci, od které odpovídající podřetězec začíná.  
  
 Následující příklad analyzuje vstupní řetězec pro teplotu ve vybraných městech. Čárkou (",") se používá k oddělení Město a jeho teploty a středníkem (";") se používá k oddělení dat pro každé město. Celý vstupní řetězec představuje jediný výskyt shody. Ve vzoru regulárního výrazu `((\w+(\s\w+)*),(\d+);)+`, který se používá pro analýzu řetězce, druhá zachytávající skupina je přiřazen název města a teplota je přiřazena čtvrtý zachytávající skupina.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Regulární výraz je definován, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`(\s\w+)*`|Porovná žádný nebo několik výskytů prázdným znakem, za nímž následuje jedna nebo více znaků slova. Tento vzor odpovídá více slov měst. Toto je třetí zachytávající skupina.|  
|`(\w+(\s\w+)*)`|Porovná jeden nebo více znaků slova následovaných nula nebo více výskytů znaku prázdný znak a jednu nebo více znaků slova. Toto je druhá zachytávající skupina.|  
|`,`|Porovná čárku.|  
|`(\d+)`|Porovná jeden nebo více číslic. Toto je čtvrtý zachytávající skupina.|  
|`;`|Shodovat středníku.|  
|`((\w+(\s\w+)*),(\d+);)+`|Porovná vzor slovo následované žádná další slova, za nímž následuje čárka, jeden nebo více číslic a středník, jednou nebo vícekrát. Toto je první zachytávající skupina.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Text.RegularExpressions>  
 [Regulárních výrazů .NET](../../../docs/standard/base-types/regular-expressions.md)  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
