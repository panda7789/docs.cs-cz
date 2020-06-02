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
ms.openlocfilehash: ad7957fd555c1de8fe47c092d3eb399a803fb1fb
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290899"
---
# <a name="the-regular-expression-object-model"></a>Model objektu regulárního výrazu
<a name="introduction"></a>Toto téma popisuje objektový model používaný při práci s regulárními výrazy .NET. Obsahuje následující oddíly:  
  
- [Modul regulárních výrazů](#Engine)  
  
- [Objekty MatchCollection a matched](#Match_and_MCollection)  
  
- [Kolekce skupin](#GroupCollection)  
  
- [Zachycená skupina](#the_captured_group)  
  
- [Kolekce Capture](#CaptureCollection)  
  
- [Individuální zachycení](#the_individual_capture)  
  
<a name="Engine"></a>
## <a name="the-regular-expression-engine"></a>Modul regulárních výrazů  
 Modul regulárních výrazů v rozhraní .NET je reprezentován <xref:System.Text.RegularExpressions.Regex> třídou. Modul regulárních výrazů zodpovídá za analýzu a kompilování regulárního výrazu a pro provádění operací, které odpovídají vzoru regulárního výrazu se vstupním řetězcem. Modul je centrální součástí v modelu objektu regulárních výrazů .NET.  
  
 Modul regulárních výrazů lze použít jedním ze dvou způsobů:  
  
- Voláním statických metod <xref:System.Text.RegularExpressions.Regex> třídy. Parametry metody zahrnují vstupní řetězec a vzor regulárního výrazu. Modul regulárních výrazů ukládá do mezipaměti regulární výrazy, které jsou používány ve volání statických metod, takže opakovaná volání statických metod regulárních výrazů, které používají stejný regulární výraz, nabízejí poměrně dobrý výkon.  
  
- Vytvořením <xref:System.Text.RegularExpressions.Regex> konstruktoru objektu předáním regulárního výrazu konstruktoru třídy. V tomto případě <xref:System.Text.RegularExpressions.Regex> je objekt neměnný (jen pro čtení) a představuje modul regulárních výrazů, který je úzce spojen s jedním regulárním výrazem. Vzhledem k tomu, že regulární výrazy používané <xref:System.Text.RegularExpressions.Regex> instancemi nejsou uloženy v mezipaměti, neměli byste instanci <xref:System.Text.RegularExpressions.Regex> objektu vytvářet vícekrát se stejným regulárním výrazem.  
  
 Můžete zavolat metody <xref:System.Text.RegularExpressions.Regex> třídy k provedení následujících operací:  
  
- Určí, zda řetězec odpovídá vzoru regulárního výrazu.  
  
- Extrahuje jednu shodu nebo první shodu.  
  
- Extrahujte všechny shody.  
  
- Nahraďte odpovídající podřetězec.  
  
- Rozdělit jeden řetězec do pole řetězců.  
  
 Tyto operace jsou popsány v následujících částech.  
  
### <a name="matching-a-regular-expression-pattern"></a>Porovnávání se vzorem regulárního výrazu  
 <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType>Metoda vrátí `true` , zda řetězec odpovídá vzoru, nebo `false` Pokud není. <xref:System.Text.RegularExpressions.Regex.IsMatch%2A>Metoda se často používá k ověření vstupu řetězce. Například následující kód zajišťuje, že řetězec odpovídá platnému rodnému číslu v USA.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Vzor regulárního výrazu `^\d{3}-\d{2}-\d{4}$` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Odpovídá začátku vstupního řetězce.|  
|`\d{3}`|Porovná tři desítkové číslice.|  
|`-`|Porovnává pomlčku.|  
|`\d{2}`|Porovnává dvě desítkové číslice.|  
|`-`|Porovnává pomlčku.|  
|`\d{4}`|Porovnává čtyři desítkové číslice.|  
|`$`|Porovná konec vstupního řetězce.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Extrakce jedné shody nebo první shody  
 <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType>Metoda vrátí <xref:System.Text.RegularExpressions.Match> objekt, který obsahuje informace o prvním podřetězci, který odpovídá vzoru regulárního výrazu. Pokud se `Match.Success` vrátí vlastnost `true` , která označuje, že byla nalezena shoda, můžete načíst informace o dalších shodách voláním <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody. Tato volání metody mohou pokračovat, dokud se `Match.Success` vlastnost nevrátí `false` . Například následující kód používá <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodu k nalezení prvního výskytu duplicitního slova v řetězci. Pak zavolá <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodu pro vyhledání jakýchkoli dalších výskytů. Příklad prověřuje `Match.Success` vlastnost po každém volání metody a určí, zda byla aktuální shoda úspěšná a zda <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> by mělo následovat volání metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Vzor regulárního výrazu `\b(\w+)\W+(\1)\b` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Zahajte shodu na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\W+`|Porovnává jeden nebo více znaků, které nejsou v textu.|  
|`(\1)`|Porovnává s prvním zachyceným řetězcem. Toto je druhá zachytávající skupina.|  
|`\b`|Ukončí porovnávání na hranici slova.|  
  
### <a name="extracting-all-matches"></a>Extrakce všech shod  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>Metoda vrátí <xref:System.Text.RegularExpressions.MatchCollection> objekt, který obsahuje informace o všech shodách, které modul regulárních výrazů našel ve vstupním řetězci. Například předchozí příklad může být přepsán pro volání <xref:System.Text.RegularExpressions.Regex.Matches%2A> metody namísto <xref:System.Text.RegularExpressions.Regex.Match%2A> <xref:System.Text.RegularExpressions.Match.NextMatch%2A> metod a.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Nahrazení odpovídajícího podřetězce  
 <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>Metoda nahradí každý podřetězec odpovídající vzoru regulárního výrazu se zadaným řetězcem nebo vzorem regulárního výrazu a vrátí celý vstupní řetězec s nahrazeními. Například následující kód přidá symbol měny v USA před desítkovým číslem v řetězci.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Vzor regulárního výrazu `\b\d+\.\d{2}\b` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`\.`|Odpovídá tečkě.|  
|`\d{2}`|Porovnává dvě desítkové číslice.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor pro nahrazení `$$$&` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Řetězec pro nahrazení|  
|-------------|------------------------|  
|`$$`|Znak dolaru ($)|  
|`$&`|Celý odpovídající podřetězec.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Rozdělení jednoho řetězce do pole řetězců  
 <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType>Metoda rozdělí vstupní řetězec na pozice definované regulárním výrazem. Například následující kód umístí položky do číslovaného seznamu do pole řetězce.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Vzor regulárního výrazu `\b\d{1,2}\.\s` je interpretován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d{1,2}`|Porovnává jednu nebo dvě desítkové číslice.|  
|`\.`|Odpovídá tečkě.|  
|`\s`|Porovná prázdný znak.|  
  
<a name="Match_and_MCollection"></a>
## <a name="the-matchcollection-and-match-objects"></a>Objekty MatchCollection a matched  
 Metody Regex vrací dva objekty, které jsou součástí modelu objektu regulárního výrazu: <xref:System.Text.RegularExpressions.MatchCollection> objekt a <xref:System.Text.RegularExpressions.Match> objekt.  
  
<a name="the_match_collection"></a>
### <a name="the-match-collection"></a>Kolekce shod  
 <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>Metoda vrátí <xref:System.Text.RegularExpressions.MatchCollection> objekt, který obsahuje <xref:System.Text.RegularExpressions.Match> objekty, které představují všechny shody nalezené modulem regulárních výrazů, v pořadí, ve kterém se vyskytují ve vstupním řetězci. Pokud neexistují žádné shody, metoda vrátí objekt bez <xref:System.Text.RegularExpressions.MatchCollection> členů. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType>Vlastnost umožňuje přístup k jednotlivým členům kolekce pomocí indexu, od nuly po hodnotu menší než hodnota <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> Vlastnosti. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A>je indexerem kolekce (v jazyce C#) a výchozí vlastností (v Visual Basic).  
  
 Ve výchozím nastavení volání <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody používá opožděné vyhodnocení k naplnění <xref:System.Text.RegularExpressions.MatchCollection> objektu. V případě přístupu k vlastnostem, které vyžadují plně naplněnou kolekci, jako jsou například <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> vlastnosti a, může dojít ke snížení výkonu. V důsledku toho doporučujeme přistupovat ke kolekci pomocí <xref:System.Collections.IEnumerator> objektu, který je vrácen <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> metodou. Jednotlivé jazyky poskytují konstrukce, jako například `For Each` v Visual Basic a `foreach` v jazyce C#, které zabalí rozhraní kolekce <xref:System.Collections.IEnumerator> .  
  
 Následující příklad používá <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> metodu k naplnění <xref:System.Text.RegularExpressions.MatchCollection> objektu se všemi shodami nalezenými ve vstupním řetězci. Tento příklad vytvoří výčet kolekce, zkopíruje shody do pole řetězců a zaznamená pozice znaků v celočíselném poli.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>
### <a name="the-match"></a>Shoda  
 <xref:System.Text.RegularExpressions.Match>Třída představuje výsledek jedné shody regulárního výrazu. Přístup k <xref:System.Text.RegularExpressions.Match> objektům lze získat dvěma způsoby:  
  
- Jejich načtením z <xref:System.Text.RegularExpressions.MatchCollection> objektu vráceného <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metodou. Chcete-li načíst jednotlivé <xref:System.Text.RegularExpressions.Match> objekty, Iterovat kolekci pomocí `foreach` (v jazyce C#) nebo `For Each` ... `Next` (v Visual Basic) konstrukce nebo použijte <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> vlastnost pro načtení konkrétního <xref:System.Text.RegularExpressions.Match> objektu buď podle indexu, nebo podle názvu. Můžete také načíst jednotlivé <xref:System.Text.RegularExpressions.Match> objekty z kolekce iterací kolekce podle indexu, od nuly po jednu, která je menší, než je počet objektů v kolekci. Tato metoda však nevyužívá opožděné vyhodnocení, protože přistupuje k <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> Vlastnosti.  
  
     Následující příklad načte jednotlivé <xref:System.Text.RegularExpressions.Match> objekty z <xref:System.Text.RegularExpressions.MatchCollection> objektu iterací kolekce pomocí `foreach` `For Each` konstrukce or... `Next` . Regulární výraz jednoduše odpovídá řetězci "ABC" ve vstupním řetězci.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
- Voláním <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody, která vrací <xref:System.Text.RegularExpressions.Match> objekt, který představuje první shodu v řetězci nebo část řetězce. Můžete určit, zda byla shoda nalezena, načtením hodnoty `Match.Success` Vlastnosti. Chcete-li načíst <xref:System.Text.RegularExpressions.Match> objekty, které reprezentují následné shody, zavolejte <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodu opakovaně, dokud `Success` vlastnost vráceného <xref:System.Text.RegularExpressions.Match> objektu není `false` .  
  
     Následující příklad používá <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody a pro spárování řetězce "ABC" ve vstupním řetězci.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Dvě vlastnosti <xref:System.Text.RegularExpressions.Match> objektů kolekce vrácených třídou:  
  
- <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>Vlastnost vrátí <xref:System.Text.RegularExpressions.GroupCollection> objekt, který obsahuje informace o podřetězcích, které se shodují se zachytávající skupinou ve vzoru regulárního výrazu.  
  
- `Match.Captures`Vlastnost vrátí <xref:System.Text.RegularExpressions.CaptureCollection> objekt, který je omezeného použití. Kolekce není naplněna pro <xref:System.Text.RegularExpressions.Match> objekt, jehož `Success` vlastnost je `false` . V opačném případě obsahuje jeden <xref:System.Text.RegularExpressions.Capture> objekt, který má stejné informace jako <xref:System.Text.RegularExpressions.Match> objekt.  
  
 Další informace o těchto objektech naleznete v části [kolekce skupin](#GroupCollection) a [kolekce Capture](#CaptureCollection) dále v tomto tématu.  
  
 Dvě další vlastnosti <xref:System.Text.RegularExpressions.Match> třídy poskytují informace o shodě. `Match.Value`Vlastnost vrátí podřetězec ve vstupním řetězci, který odpovídá vzoru regulárního výrazu. `Match.Index`Vlastnost vrací počáteční pozici odpovídajícího řetězce ve vstupním řetězci na základě nuly.  
  
 <xref:System.Text.RegularExpressions.Match>Třída má také dvě metody porovnávání vzorů:  
  
- <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType>Metoda najde shodu po shodě reprezentované aktuálním <xref:System.Text.RegularExpressions.Match> objektem a vrátí <xref:System.Text.RegularExpressions.Match> objekt, který představuje shodu.  
  
- <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType>Metoda provede určenou operaci nahrazení na odpovídajícím řetězci a vrátí výsledek.  
  
 Následující příklad používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodu k předřadí symbol $ a mezeru před každým číslem, který obsahuje dvě zlomkové číslice.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Vzor regulárního výrazu `\b\d+(,\d{3})*\.\d{2}\b` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`(,\d{3})*`|Porovná žádný nebo více výskytů čárky následovaný třemi desítkovými číslicemi.|  
|`\.`|Porovnává se znakem desetinné čárky.|  
|`\d{2}`|Porovnává dvě desítkové číslice.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor pro nahrazení `$$ $&` označuje, že odpovídající podřetězec by měl být nahrazen symbolem dolaru ($) ( `$$` vzor), mezerou a hodnotou shody ( `$&` vzorek).  
  
 [Zpět na začátek](#introduction)  
  
<a name="GroupCollection"></a>
## <a name="the-group-collection"></a>Kolekce skupin  
 <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>Vlastnost vrátí <xref:System.Text.RegularExpressions.GroupCollection> objekt, který obsahuje <xref:System.Text.RegularExpressions.Group> objekty, které reprezentují zachycené skupiny v jedné shodě. První <xref:System.Text.RegularExpressions.Group> objekt v kolekci (na indexu 0) představuje celou shodu. Každý objekt, který následuje, představuje výsledky jedné zachytávající skupiny.  
  
 Jednotlivé <xref:System.Text.RegularExpressions.Group> objekty v kolekci lze načíst pomocí <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> Vlastnosti. V kolekci můžete načíst nepojmenované skupiny podle jejich pořadového umístění a načíst pojmenované skupiny buď podle názvu nebo podle pořadového čísla. Nepojmenovaná zachycení se v kolekci zobrazí jako první a jsou indexována zleva doprava v pořadí, ve kterém jsou uvedena ve vzoru regulárního výrazu. Pojmenovaná zachycení jsou indexována po nepojmenovaných zachyceních zleva doprava v pořadí, ve kterém jsou uvedena ve vzoru regulárního výrazu. Chcete-li určit, které číslované skupiny jsou k dispozici v kolekci vrácené pro určitou metodu pro porovnání regulárního výrazu, můžete zavolat <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> metodu instance. Chcete-li zjistit, jaké pojmenované skupiny jsou k dispozici v kolekci, můžete zavolat <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> metodu instance. Obě metody jsou zvláště užitečné v rutinách pro obecné účely, které analyzují shody zjištěné jakýmkoli regulárním výrazem.  
  
 <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType>Vlastnost je indexerem kolekce v jazyce C# a výchozí vlastností objektu kolekce v Visual Basic. To znamená, že <xref:System.Text.RegularExpressions.Group> k jednotlivým objektům lze v případě pojmenovaných skupin přicházet pomocí indexu (nebo podle názvu) následujícím způsobem:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 Následující příklad definuje regulární výraz, který používá seskupovací konstrukce pro zachycení měsíce, dne a roku data.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Vzor regulárního výrazu `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(\d{1,2})`|Porovnává jednu nebo dvě desítkové číslice. Toto je druhá zachytávající skupina.|  
|`,`|Porovnává čárku.|  
|`\s`|Porovná prázdný znak.|  
|`(\d{4})`|Porovnává čtyři desítkové číslice. Toto je třetí zachytávající skupina.|  
|`\b`|Ukončí porovnávání na hranici slova.|  
  
 [Zpět na začátek](#introduction)  
  
<a name="the_captured_group"></a>
## <a name="the-captured-group"></a>Zachycená skupina  
 <xref:System.Text.RegularExpressions.Group>Třída představuje výsledek z jedné zachytávající skupiny. Objekty skupiny, které představují zachytávající skupiny definované v regulárním výrazu, jsou vráceny <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> vlastností <xref:System.Text.RegularExpressions.GroupCollection> objektu vráceného <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastností. <xref:System.Text.RegularExpressions.GroupCollection.Item%2A>Vlastnost je indexerem (v jazyce C#) a výchozí vlastností (v Visual Basic) <xref:System.Text.RegularExpressions.Group> třídy. Můžete také načíst jednotlivé členy iterací kolekce pomocí `foreach` `For Each` konstrukce nebo. Příklad najdete v předchozí části.  
  
 Následující příklad používá vnořené seskupovací konstrukce pro zachycení podřetězců do skupin. Vzor regulárního výrazu `(a(b))c` odpovídá řetězci "ABC". Přiřadí podřetězec "AB" první zachytávající skupině a dílčí řetězec "b" do druhé zachytávající skupiny.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 Následující příklad používá pojmenované seskupovací konstrukce pro zachycení podřetězců z řetězce, který obsahuje data ve formátu "DATA: hodnota", který je regulární výraz rozdělen na dvojtečku (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Vzor regulárního výrazu `^(?<name>\w+):(?<value>\w+)` je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`(?<name>\w+)`|Porovná jeden nebo více znaků slova. Název této zachytávající skupiny je `name` .|  
|`:`|Porovnává dvojtečku.|  
|`(?<value>\w+)`|Porovná jeden nebo více znaků slova. Název této zachytávající skupiny je `value` .|  
  
 Vlastnosti <xref:System.Text.RegularExpressions.Group> třídy poskytují informace o zachycené skupině: `Group.Value` vlastnost obsahuje zachycený podřetězec, `Group.Index` vlastnost indikuje počáteční pozici zachycené skupiny ve vstupním textu, `Group.Length` vlastnost obsahuje délku zachyceného textu a `Group.Success` vlastnost označuje, zda se podřetězec shodoval se vzorem definovaným zachycující skupinou.  
  
 Použití kvantifikátorů na skupinu (Další informace naleznete v části [kvantifikátory](quantifiers-in-regular-expressions.md)) upravuje vztah jednoho zachycení na skupinu zachycení dvěma způsoby:  
  
- Pokud `*` `*?` je pro skupinu použit kvantifikátor nebo (který určuje nula nebo více shod), zachytávající skupina nesmí mít shodu ve vstupním řetězci. Pokud není k dispozici žádný zachycený text, vlastnosti <xref:System.Text.RegularExpressions.Group> objektu jsou nastaveny tak, jak je uvedeno v následující tabulce.  
  
    |Group – vlastnost|Hodnota|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     V následujícím příkladu je uvedena ukázka. Ve vzorku regulárního výrazu `aaa(bbb)*ccc` může být první zachytávající skupina (podřetězec "BBB") shodná s nula nebo vícekrát. Vzhledem k tomu, že vstupní řetězec "aaaccc" odpovídá vzoru, zachytávající skupina nemá shodu.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
- Kvantifikátory mohou odpovídat více výskytům vzoru, který je definován zachycenou skupinou. V tomto případě `Value` `Length` vlastnosti a <xref:System.Text.RegularExpressions.Group> objektu obsahují informace pouze o posledním zachyceném podřetězci. Například následující regulární výraz odpovídá jedné větě, která končí tečkou. Používá dvě seskupovací konstrukce: První zachytává jednotlivá slova spolu s prázdným znakem; Druhá zachytává jednotlivá slova. Jak ukazuje výstup z příkladu, přestože regulární výraz uspěje při zachycení celé věty, druhá zachytávající skupina zachytí pouze poslední slovo.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Zpět na začátek](#introduction)  
  
<a name="CaptureCollection"></a>
## <a name="the-capture-collection"></a>Kolekce Capture  
 <xref:System.Text.RegularExpressions.Group>Objekt obsahuje informace pouze o posledním zachycení. Nicméně celá sada zachycení vytvořená zachycující skupinou je stále k dispozici z <xref:System.Text.RegularExpressions.CaptureCollection> objektu, který je vrácen <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastností. Každý člen kolekce je <xref:System.Text.RegularExpressions.Capture> objekt, který představuje zachycení vytvořené touto zachytávající skupinou v pořadí, v jakém byly zachyceny (a proto v pořadí, ve kterém byly zachycené řetězce porovnány zleva doprava ve vstupním řetězci). Jednotlivé <xref:System.Text.RegularExpressions.Capture> objekty z kolekce lze načíst jedním ze dvou způsobů:  
  
- Pomocí iterace v kolekci pomocí konstrukce, jako je například `foreach` (v jazyce C#) nebo `For Each` (v Visual Basic).  
  
- Pomocí <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> vlastnosti pro načtení konkrétního objektu podle indexu. <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A>Vlastnost je <xref:System.Text.RegularExpressions.CaptureCollection> výchozí vlastnost objektu (v Visual Basic) nebo indexer (v jazyce C#).  
  
 Pokud kvantifikátor není aplikován na zachytávající skupinu, <xref:System.Text.RegularExpressions.CaptureCollection> objekt obsahuje jeden <xref:System.Text.RegularExpressions.Capture> objekt, který je o něco důležité, protože poskytuje informace o stejné shodě jako jeho <xref:System.Text.RegularExpressions.Group> objekt. Pokud je kvantifikátor použit pro zachytávající skupinu, <xref:System.Text.RegularExpressions.CaptureCollection> objekt obsahuje všechna zachycení vytvořená zachycující skupinou a poslední člen kolekce představuje stejné zachycení jako <xref:System.Text.RegularExpressions.Group> objekt.  
  
 Například pokud použijete vzor regulárního výrazu `((a(b))c)+` (kde + kvantifikátor Určuje jednu nebo více shod) pro zachycení shody z řetězce "abcabcabc", <xref:System.Text.RegularExpressions.CaptureCollection> objekt pro každý <xref:System.Text.RegularExpressions.Group> objekt obsahuje tři členy.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Následující příklad používá regulární výraz `(Abc)+` k vyhledání jednoho nebo více po sobě jdoucích spuštění řetězce "ABC" v řetězci "XYZAbcAbcAbcXYZAbcAb". Příklad znázorňuje použití <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vlastnosti pro vrácení více skupin zachycených podřetězců.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Zpět na začátek](#introduction)  
  
<a name="the_individual_capture"></a>
## <a name="the-individual-capture"></a>Individuální zachycení  
 <xref:System.Text.RegularExpressions.Capture>Třída obsahuje výsledky jednoho zachycení dílčího výrazu. <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType>Vlastnost obsahuje odpovídající text a <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> vlastnost označuje pozici s nulovým základem ve vstupním řetězci, na kterém je začátek odpovídajícího podřetězce.  
  
 Následující příklad analyzuje vstupní řetězec pro teplotu vybraných měst. Čárka (",") se používá k oddělení města a jeho teploty a středník (";") slouží k oddělení dat jednotlivých měst. Celý vstupní řetězec představuje jednu shodu. Ve vzoru regulárního výrazu `((\w+(\s\w+)*),(\d+);)+` , který se používá k analýze řetězce, je název města přiřazen druhé zachytávající skupině a teplota je přiřazena čtvrté zachytávající skupině.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Regulární výraz je definován tak, jak je uvedeno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`(\s\w+)*`|Porovná žádný nebo více výskytů prázdného znaku následovaného jedním nebo více znaky slova. Tento model se shoduje s názvy měst pro více slov. Toto je třetí zachytávající skupina.|  
|`(\w+(\s\w+)*)`|Porovná jeden nebo více znaků slova následovaných žádným nebo více výskyty prázdného znaku a jedním nebo více znaky slova. Toto je druhá zachytávající skupina.|  
|`,`|Porovnává čárku.|  
|`(\d+)`|Porovnává s jednou nebo více číslicemi. Toto je čtvrtá zachytávající skupina.|  
|`;`|Porovnává středník.|  
|`((\w+(\s\w+)*),(\d+);)+`|Porovnává se se vzorem slova následovaného dalšími slovy následovanými čárkou, jednou nebo více číslicemi a středníkem, jednou nebo vícekrát. Toto je první zachytávající skupina.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Text.RegularExpressions>
- [Regulární výrazy .NET](regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](regular-expression-language-quick-reference.md)
