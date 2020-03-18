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
ms.openlocfilehash: 8956be3cf8f96a8dd255f378d4927404c172c908
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159998"
---
# <a name="the-regular-expression-object-model"></a>Model objektu regulárního výrazu
<a name="introduction"></a>Toto téma popisuje objektový model používaný při práci s regulárními výrazy .NET. Obsahuje následující oddíly:  
  
- [Modul regulárních výrazů](#Engine)  
  
- [MatchCollection a match objekty](#Match_and_MCollection)  
  
- [Kolekce skupiny](#GroupCollection)  
  
- [Zachycená skupina](#the_captured_group)  
  
- [Kolekce zachycení](#CaptureCollection)  
  
- [Individuální zachycení](#the_individual_capture)  
  
<a name="Engine"></a>
## <a name="the-regular-expression-engine"></a>Modul regulárních výrazů  
 Modul regulárních výrazů v <xref:System.Text.RegularExpressions.Regex> rozhraní .NET je reprezentován třídou. Modul regulárních výrazů je zodpovědný za analýzu a kompilaci regulárního výrazu a za provádění operací, které odpovídají vzoru regulárního výrazu se vstupním řetězcem. Modul je centrální součástí objektového modelu regulárního výrazu .NET.  
  
 Modul regulárních výrazů můžete použít dvěma způsoby:  
  
- Voláním statické metody <xref:System.Text.RegularExpressions.Regex> třídy. Parametry metody zahrnují vstupní řetězec a vzor regulárního výrazu. Modul regulárních výrazů ukládá regulární výrazy, které se používají při volání statické metody, takže opakovaná volání statických metod regulárních výrazů, které používají stejný regulární výraz, nabízejí relativně dobrý výkon.  
  
- Vytvořením instance objektu <xref:System.Text.RegularExpressions.Regex> předáním regulárního výrazu konstruktoru třídy. V tomto případě <xref:System.Text.RegularExpressions.Regex> je objekt neměnný (jen pro čtení) a představuje modul regulárních výrazů, který je pevně spojen s jedním regulárním výrazem. Vzhledem k tomu, že regulární výrazy používané <xref:System.Text.RegularExpressions.Regex> instancemi <xref:System.Text.RegularExpressions.Regex> nejsou ukládány do mezipaměti, neměli byste vytvořit instanci objektu vícekrát se stejným regulárním výrazem.  
  
 Můžete volat metody <xref:System.Text.RegularExpressions.Regex> třídy k provedení následujících operací:  
  
- Určete, zda řetězec odpovídá vzoru regulárního výrazu.  
  
- Extrahovat jednu shodu nebo první shodu.  
  
- Extrahujte všechny shody.  
  
- Nahraďte odpovídající podřetězec.  
  
- Rozdělte jeden řetězec do pole řetězců.  
  
 Tyto operace jsou popsány v následujících částech.  
  
### <a name="matching-a-regular-expression-pattern"></a>Odpovídající vzor regulárního výrazu  
 Metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> vrátí, `true` pokud řetězec odpovídá `false` vzoru, nebo pokud není. Metoda <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> se často používá k ověření vstupu řetězce. Například následující kód zajišťuje, že řetězec odpovídá platné číslo sociálního zabezpečení ve Spojených státech.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/validate1.cs#1)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/validate1.vb#1)]  
  
 Vzor regulárního výrazu `^\d{3}-\d{2}-\d{4}$` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Porovná začátek vstupního řetězce.|  
|`\d{3}`|Porovná tři desítkové číslice.|  
|`-`|Porovná pomlčku.|  
|`\d{2}`|Porovná dvě desetinná místa.|  
|`-`|Porovná pomlčku.|  
|`\d{4}`|Porovná čtyři desetinné číslice.|  
|`$`|Porovná konec vstupního řetězce.|  
  
### <a name="extracting-a-single-match-or-the-first-match"></a>Extrahování jedné nebo první shody  
 Metoda <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> vrátí <xref:System.Text.RegularExpressions.Match> objekt, který obsahuje informace o prvním podřetězci, který odpovídá vzoru regulárního výrazu. Pokud `Match.Success` vlastnost `true`vrátí , označující, že byla nalezena shoda, můžete <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> načíst informace o následné shody voláním metody. Tato volání metody můžete `Match.Success` pokračovat, dokud vlastnost vrátí `false`. Například následující kód používá <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> metodu k vyhledání prvního výskytu duplicitního slova v řetězci. Potom volá <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metodu najít všechny další výskyty. Příklad zkoumá `Match.Success` vlastnost po každé volání metody k určení, zda aktuální shoda <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> byla úspěšná a zda by mělo následovat volání metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match1.cs#2)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match1.vb#2)]  
  
 Vzor regulárního výrazu `\b(\w+)\W+(\1)\b` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začněte shodu na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\W+`|Porovná jeden nebo více znaků, které nejsou slovem.|  
|`(\1)`|Porovná první zachycený řetězec. Toto je druhá zachytávající skupina.|  
|`\b`|Ukončite shodu na hranici slova.|  
  
### <a name="extracting-all-matches"></a>Extrahování všech shod  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> vrátí <xref:System.Text.RegularExpressions.MatchCollection> objekt, který obsahuje informace o všech shodách, které modul regulárních výrazů nalezený ve vstupním řetězci. Například předchozí příklad může být přepsán <xref:System.Text.RegularExpressions.Regex.Matches%2A> volat metodu namísto <xref:System.Text.RegularExpressions.Regex.Match%2A> a <xref:System.Text.RegularExpressions.Match.NextMatch%2A> metody.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matches1.cs#3)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matches1.vb#3)]  
  
### <a name="replacing-a-matched-substring"></a>Nahrazení odpovídajícího podřetězce  
 Metoda <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nahradí každý podřetězec, který odpovídá vzoru regulárního výrazu, zadaným řetězcem nebo vzorem regulárního výrazu a vrátí celý vstupní řetězec s náhradami. Například následující kód přidá symbol měny USA před desetinné číslo v řetězci.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/replace1.cs#4)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/replace1.vb#4)]  
  
 Vzor regulárního výrazu `\b\d+\.\d{2}\b` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`\.`|Porovná tečku.|  
|`\d{2}`|Porovná dvě desetinná místa.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor nahrazení `$$$&` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Náhradní řetězec|  
|-------------|------------------------|  
|`$$`|Znak dolaru ($).|  
|`$&`|Celý odpovídající podřetězec.|  
  
### <a name="splitting-a-single-string-into-an-array-of-strings"></a>Rozdělení jednoho řetězce do pole řetězců  
 Metoda <xref:System.Text.RegularExpressions.Regex.Split%2A?displayProperty=nameWithType> rozdělí vstupní řetězec na pozice definované shodou regulárních výrazů. Například následující kód umístí položky v číslovaném seznamu do pole řetězců.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/split1.cs#5)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/split1.vb#5)]  
  
 Vzor regulárního výrazu `\b\d{1,2}\.\s` je interpretován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d{1,2}`|Porovná jednu nebo dvě desetinná místa.|  
|`\.`|Porovná tečku.|  
|`\s`|Porovná prázdný znak.|  
  
<a name="Match_and_MCollection"></a>
## <a name="the-matchcollection-and-match-objects"></a>MatchCollection a match objekty  
 Metody Regex vracejí dva objekty, které jsou <xref:System.Text.RegularExpressions.MatchCollection> součástí objektového <xref:System.Text.RegularExpressions.Match> modelu regulárního výrazu: objekt a objekt.  
  
<a name="the_match_collection"></a>
### <a name="the-match-collection"></a>Kolekce shody  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> vrátí <xref:System.Text.RegularExpressions.MatchCollection> objekt, <xref:System.Text.RegularExpressions.Match> který obsahuje objekty, které představují všechny shody, které modul regulárních výrazů nalezen, v pořadí, ve kterém se vyskytují ve vstupním řetězci. Pokud neexistují žádné shody, <xref:System.Text.RegularExpressions.MatchCollection> metoda vrátí objekt bez členů. Vlastnost <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> umožňuje přístup k jednotlivým členům kolekce podle indexu, od nuly <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> do jedné menší než hodnota vlastnosti. <xref:System.Text.RegularExpressions.MatchCollection.Item%2A>je indexer kolekce (v jazyce C#) a výchozí vlastnost (v jazyce Visual Basic).  
  
 Ve výchozím nastavení volání <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> metody používá opožděné <xref:System.Text.RegularExpressions.MatchCollection> vyhodnocení k naplnění objektu. Přístup k vlastnostem, které vyžadují plně <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> vyplněnou kolekci, jako jsou vlastnosti a, <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> může zahrnovat snížení výkonu. V důsledku toho doporučujeme přistupovat ke <xref:System.Collections.IEnumerator> kolekci pomocí objektu, který je vrácen <xref:System.Text.RegularExpressions.MatchCollection.GetEnumerator%2A?displayProperty=nameWithType> metodou. Jednotlivé jazyky poskytují konstrukce, `For Each` například `foreach` v jazyce Visual Basic <xref:System.Collections.IEnumerator> a v jazyce C#, které zabalí rozhraní kolekce.  
  
 Následující příklad používá <xref:System.Text.RegularExpressions.Regex.Matches%28System.String%29?displayProperty=nameWithType> metodu <xref:System.Text.RegularExpressions.MatchCollection> k naplnění objektu se všemi shodami nalezenými ve vstupním řetězci. Příklad vyjmenovává kolekci, zkopíruje shody do pole řetězců a zaznamená pozice znaků v poli celého čísla.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/matchcollection1.cs#6)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/matchcollection1.vb#6)]  
  
<a name="the_match"></a>
### <a name="the-match"></a>Shoda  
 Třída <xref:System.Text.RegularExpressions.Match> představuje výsledek jedné shody regulárního výrazu. K objektům můžete přistupovat <xref:System.Text.RegularExpressions.Match> dvěma způsoby:  
  
- Jejich načtením <xref:System.Text.RegularExpressions.MatchCollection> z objektu, <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> který je vrácen metodou. Chcete-li <xref:System.Text.RegularExpressions.Match> načíst jednotlivé objekty, `foreach` iterát kolekce `For Each`pomocí (v C#) nebo ... `Next` (v jazyce Visual Basic) <xref:System.Text.RegularExpressions.MatchCollection.Item%2A?displayProperty=nameWithType> konstrukce nebo <xref:System.Text.RegularExpressions.Match> použít vlastnost k načtení určitého objektu podle indexu nebo podle názvu. Můžete také načíst jednotlivé <xref:System.Text.RegularExpressions.Match> objekty z kolekce iterace kolekce podle indexu, od nuly do jednoho méně než počet objektů v kolekci. Tato metoda však nevyužívá opožděné vyhodnocení, protože <xref:System.Text.RegularExpressions.MatchCollection.Count%2A?displayProperty=nameWithType> přistupuje k vlastnosti.  
  
     Následující příklad načte <xref:System.Text.RegularExpressions.Match> jednotlivé <xref:System.Text.RegularExpressions.MatchCollection> objekty z objektu iterace kolekce pomocí `foreach` nebo `For Each`... `Next` konstrukce. Regulární výraz jednoduše odpovídá řetězci "abc" ve vstupním řetězci.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match2.cs#7)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match2.vb#7)]  
  
- Voláním <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> metody, která <xref:System.Text.RegularExpressions.Match> vrátí objekt, který představuje první shodu v řetězci nebo část řetězce. Můžete určit, zda byla nalezena shoda načtením hodnoty vlastnosti. `Match.Success` Chcete-li <xref:System.Text.RegularExpressions.Match> načíst objekty, <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> které představují následné `Success` shody, <xref:System.Text.RegularExpressions.Match> volání `false`metody opakovaně, dokud je vlastnost vráceného objektu .  
  
     Následující příklad používá <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%29?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> metody a tak, aby odpovídaly řetězci "abc" ve vstupním řetězci.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/match3.cs#8)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/match3.vb#8)]  
  
 Dvě vlastnosti <xref:System.Text.RegularExpressions.Match> třídy vrátí kolekce objektů:  
  
- Vlastnost <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vrátí <xref:System.Text.RegularExpressions.GroupCollection> objekt, který obsahuje informace o podřetězec, které odpovídají zachytávání skupin ve vzoru regulárního výrazu.  
  
- Vlastnost `Match.Captures` vrátí <xref:System.Text.RegularExpressions.CaptureCollection> objekt, který je s omezeným použitím. Kolekce není naplněna pro <xref:System.Text.RegularExpressions.Match> objekt, `Success` `false`jehož vlastnost je . V opačném případě <xref:System.Text.RegularExpressions.Capture> obsahuje jeden objekt, který <xref:System.Text.RegularExpressions.Match> má stejné informace jako objekt.  
  
 Další informace o těchto objektech naleznete v části [Kolekce skupin a](#GroupCollection) Kolekce [zachycení](#CaptureCollection) dále v tomto tématu.  
  
 Dvě další vlastnosti třídy <xref:System.Text.RegularExpressions.Match> poskytují informace o shodě. Vlastnost `Match.Value` vrátí podřetězec ve vstupním řetězci, který odpovídá vzoru regulárního výrazu. Vlastnost `Match.Index` vrátí počáteční pozici odpovídajícího řetězce ve vstupním řetězci na základě nuly.  
  
 Třída <xref:System.Text.RegularExpressions.Match> má také dvě metody porovnávání vzorů:  
  
- Metoda <xref:System.Text.RegularExpressions.Match.NextMatch%2A?displayProperty=nameWithType> najde shodu za shodou reprezentou aktuálním <xref:System.Text.RegularExpressions.Match> objektem <xref:System.Text.RegularExpressions.Match> a vrátí objekt, který představuje tuto shodu.  
  
- Metoda <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> provede zadanou operaci nahrazení na odpovídající řetězec a vrátí výsledek.  
  
 Následující příklad používá <xref:System.Text.RegularExpressions.Match.Result%2A?displayProperty=nameWithType> metodu předřadit symbol $ a mezeru před každé číslo, které obsahuje dvě zlomkové číslice.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/result1.cs#9)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/result1.vb#9)]  
  
 Vzor regulárního výrazu `\b\d+(,\d{3})*\.\d{2}\b` je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`\d+`|Porovná jednu nebo více desítkových číslic.|  
|`(,\d{3})*`|Porovná nula nebo více výskytů čárky následovaných třemi desetinnými místy.|  
|`\.`|Porovná znak desetinné čárky.|  
|`\d{2}`|Porovná dvě desetinná místa.|  
|`\b`|Ukončí porovnání na hranici slova.|  
  
 Vzor nahrazení `$$ $&` označuje, že odpovídající podřetězec by měl být nahrazen symbolem `$$` dolaru ($) (vzor), mezerou a hodnotou shody `$&` (vzor).  
  
 [Zpět na začátek](#introduction)  
  
<a name="GroupCollection"></a>
## <a name="the-group-collection"></a>Kolekce skupiny  
 Vlastnost <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vrátí <xref:System.Text.RegularExpressions.GroupCollection> objekt, <xref:System.Text.RegularExpressions.Group> který obsahuje objekty, které představují zachycené skupiny v jedné shodě. První <xref:System.Text.RegularExpressions.Group> objekt v kolekci (v indexu 0) představuje celou shodu. Každý následující objekt představuje výsledky jedné zachytávající skupiny.  
  
 Můžete načíst <xref:System.Text.RegularExpressions.Group> jednotlivé objekty v <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> kolekci pomocí vlastnosti. Nepojmenované skupiny můžete načíst podle jejich ordinální pozice v kolekci a načíst pojmenované skupiny podle názvu nebo podle ordinální pozice. Nepojmenované zachycení se zobrazí jako první v kolekci a jsou indexovány zleva doprava v pořadí, ve kterém se zobrazí ve vzoru regulárního výrazu. Pojmenované zachycení jsou indexovány po nepojmenované zachycení, zleva doprava v pořadí, ve kterém se zobrazí ve vzoru regulárního výrazu. Chcete-li zjistit, jaké číslované skupiny jsou k dispozici v kolekci <xref:System.Text.RegularExpressions.Regex.GetGroupNumbers%2A?displayProperty=nameWithType> vrácené pro určitou metodu porovnávání regulárních výrazů, můžete volat metodu instance. Chcete-li zjistit, jaké pojmenované skupiny jsou <xref:System.Text.RegularExpressions.Regex.GetGroupNames%2A?displayProperty=nameWithType> k dispozici v kolekci, můžete volat metodu instance. Obě metody jsou užitečné zejména v rutinách pro obecné účely, které analyzují shody nalezené libovolným regulárním výrazem.  
  
 Vlastnost <xref:System.Text.RegularExpressions.GroupCollection.Item%2A?displayProperty=nameWithType> je indexer kolekce v jazyce C# a výchozí vlastnost objektu kolekce v jazyce Visual Basic. To znamená, <xref:System.Text.RegularExpressions.Group> že jednotlivé objekty lze přistupovat podle indexu (nebo podle názvu, v případě pojmenovaných skupin) takto:  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupsyntax1.cs#13)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupsyntax1.vb#13)]  
  
 Následující příklad definuje regulární výraz, který používá seskupovací konstrukce k zachycení měsíce, dne a roku data.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/groupcollection1.cs#10)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/groupcollection1.vb#10)]  
  
 Vzor regulárního výrazu `\b(\w+)\s(\d{1,2}),\s(\d{4})\b` je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začne porovnání na hranici slova.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(\d{1,2})`|Porovná jednu nebo dvě desetinná místa. Toto je druhá zachytávající skupina.|  
|`,`|Porovnejte čárku.|  
|`\s`|Porovná prázdný znak.|  
|`(\d{4})`|Porovná čtyři desetinné číslice. Toto je třetí zachytávající skupina.|  
|`\b`|Ukončite shodu na hranici slova.|  
  
 [Zpět na začátek](#introduction)  
  
<a name="the_captured_group"></a>
## <a name="the-captured-group"></a>Zachycená skupina  
 Třída <xref:System.Text.RegularExpressions.Group> představuje výsledek z jedné zachytávající skupiny. Objekty skupiny, které představují zachytávající skupiny definované v regulárním výrazu, <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> jsou vráceny vlastností objektu <xref:System.Text.RegularExpressions.GroupCollection> vráceného <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType> vlastností. Vlastnost <xref:System.Text.RegularExpressions.GroupCollection.Item%2A> je indexer (v jazyce C#) a výchozí vlastnost <xref:System.Text.RegularExpressions.Group> (v jazyce Visual Basic) třídy. Můžete také načíst jednotlivé členy iterace `foreach` `For Each` kolekce pomocí nebo konstrukce. Příklad naleznete v předchozí části.  
  
 Následující příklad používá vnořené seskupení konstrukce zachytit podřetězce do skupin. Vzor `(a(b))c` regulárního výrazu odpovídá řetězci "abc". Přiřadí podřetězec "ab" první zachytávající skupině a podřetězec "b" druhé zachytávající skupině.  
  
 [!code-csharp[RegularExpressions.Classes#6](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#6)]
 [!code-vb[RegularExpressions.Classes#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#6)]  
  
 Následující příklad používá pojmenované seskupovací konstrukce k zachycení podřetězců z řetězce, který obsahuje data ve formátu "DATANAME:VALUE", který regulární výraz rozdělí na dvojtečku (:).  
  
 [!code-csharp[RegularExpressions.Classes#8](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#8)]
 [!code-vb[RegularExpressions.Classes#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#8)]  
  
 Vzor regulárního výrazu `^(?<name>\w+):(?<value>\w+)` je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Zahájí porovnávání na začátku vstupního řetězce.|  
|`(?<name>\w+)`|Porovná jeden nebo více znaků slova. Název této zachytávající `name`skupiny je .|  
|`:`|Porovná dvojtečku.|  
|`(?<value>\w+)`|Porovná jeden nebo více znaků slova. Název této zachytávající `value`skupiny je .|  
  
 Vlastnosti <xref:System.Text.RegularExpressions.Group> třídy poskytují informace o zachycené `Group.Value` skupině: Vlastnost obsahuje zachycený podřetězec, `Group.Index` vlastnost označuje počáteční pozici zachycené `Group.Length` skupiny ve vstupním textu, `Group.Success` vlastnost obsahuje délku zachyceného textu a vlastnost označuje, zda podřetězec odpovídá vzoru definovanému zachytávající skupinou.  
  
 Použití kvantifikátorů na skupinu (další informace viz [Kvantifikátory](../../../docs/standard/base-types/quantifiers-in-regular-expressions.md)) upravuje vztah jednoho zachycení na zachytávající skupinu dvěma způsoby:  
  
- Pokud `*` je `*?` pro skupinu použit kvantifikátor nebo kvantifikátor (který určuje nulu nebo více shod), zachytávající skupina nemusí mít ve vstupním řetězci shodu. Pokud není zachycen text, vlastnosti <xref:System.Text.RegularExpressions.Group> objektu jsou nastaveny tak, jak je znázorněno v následující tabulce.  
  
    |Vlastnost skupiny|Hodnota|  
    |--------------------|-----------|  
    |`Success`|`false`|  
    |`Value`|<xref:System.String.Empty?displayProperty=nameWithType>|  
    |`Length`|0|  
  
     V následujícím příkladu je uvedena ukázka. Ve vzoru `aaa(bbb)*ccc`regulárního výrazu může být první zachytávající skupina (podřetězec "bbb") spárována s nulou nebo vícekrát. Vzhledem k tomu, že vstupní řetězec "aaaccc" odpovídá vzoru, zachytávající skupina nemá shodu.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/nocapture1.cs#11)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/nocapture1.vb#11)]  
  
- Kvantifikátory mohou odpovídat více výskytům vzoru, který je definován zachytávající skupinou. V tomto případě `Value` `Length` a vlastnosti objektu <xref:System.Text.RegularExpressions.Group> obsahují informace pouze o posledním zachyceném podřetězci. Například následující regulární výraz odpovídá jedné větě, která končí tečkou. Používá dvě seskupovací konstrukce: První zachycuje jednotlivá slova spolu s znakem prázdného místa; druhý zachycuje jednotlivá slova. Jak ukazuje výstup z příkladu, i když regulární výraz uspěje při zachycení celé věty, druhá zachytávající skupina zachytí pouze poslední slovo.  
  
     [!code-csharp[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/lastcapture1.cs#12)]
     [!code-vb[Conceptual.RegularExpressions.ObjectModel#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/lastcapture1.vb#12)]  
  
 [Zpět na začátek](#introduction)  
  
<a name="CaptureCollection"></a>
## <a name="the-capture-collection"></a>Kolekce zachycení  
 Objekt <xref:System.Text.RegularExpressions.Group> obsahuje informace pouze o posledním zachycení. Celá sada zachycení provedené zachytávající skupiny je však stále k dispozici z objektu, <xref:System.Text.RegularExpressions.CaptureCollection> který je vrácen vlastností. <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> Každý člen kolekce je <xref:System.Text.RegularExpressions.Capture> objekt, který představuje zachycení provedené této zachytávající skupiny, v pořadí, ve kterém byly zachyceny (a proto v pořadí, ve kterém byly zachycené řetězce uzavřeno zleva doprava ve vstupním řetězci). Jednotlivé <xref:System.Text.RegularExpressions.Capture> objekty můžete načíst z kolekce dvěma způsoby:  
  
- Iterace prostřednictvím kolekce pomocí konstrukce, jako `foreach` je `For Each` například (v jazyce C#) nebo (v jazyce Visual Basic).  
  
- Pomocí vlastnosti <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A?displayProperty=nameWithType> načíst konkrétní objekt podle indexu. Vlastnost <xref:System.Text.RegularExpressions.CaptureCollection.Item%2A> je <xref:System.Text.RegularExpressions.CaptureCollection> výchozí vlastnost objektu (v jazyce Visual Basic) nebo indexer (v jazyce C#).  
  
 Pokud kvantifikátor není použit a <xref:System.Text.RegularExpressions.CaptureCollection> zachytávající <xref:System.Text.RegularExpressions.Capture> skupina, objekt obsahuje jeden objekt, který je <xref:System.Text.RegularExpressions.Group> malý zájem, protože poskytuje informace o stejné shody jako jeho objekt. Pokud kvantifikátor je použita <xref:System.Text.RegularExpressions.CaptureCollection> na zachytávající skupiny, objekt obsahuje všechna zachycení provedené zachytávání <xref:System.Text.RegularExpressions.Group> skupiny a poslední člen kolekce představuje stejné zachycení jako objekt.  
  
 Pokud například použijete vzor `((a(b))c)+` regulárního výrazu <xref:System.Text.RegularExpressions.CaptureCollection> (kde kvantifikátor + určuje jednu nebo více shod) k zachycení shod z řetězce "abcabcabc", objekt pro každý <xref:System.Text.RegularExpressions.Group> objekt obsahuje tři členy.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capturecollection1.cs#14)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capturecollection1.vb#14)]  
  
 Následující příklad používá regulární výraz `(Abc)+` k nalezení jednoho nebo více po sobě jdoucích spuštění řetězce "Abc" v řetězci "XYZAbcAbcAbcAbcAb". Příklad ilustruje použití vlastnosti <xref:System.Text.RegularExpressions.Group.Captures%2A?displayProperty=nameWithType> vrátit více skupin zachycených podřetězců.  
  
 [!code-csharp[RegularExpressions.Classes#5](../../../samples/snippets/csharp/VS_Snippets_CLR/RegularExpressions.Classes/cs/Example.cs#5)]
 [!code-vb[RegularExpressions.Classes#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/RegularExpressions.Classes/vb/Example.vb#5)]  
  
 [Zpět na začátek](#introduction)  
  
<a name="the_individual_capture"></a>
## <a name="the-individual-capture"></a>Individuální zachycení  
 Třída <xref:System.Text.RegularExpressions.Capture> obsahuje výsledky z jednoho zachycení dílčího výrazu. Vlastnost <xref:System.Text.RegularExpressions.Capture.Value%2A?displayProperty=nameWithType> obsahuje odpovídající text a <xref:System.Text.RegularExpressions.Capture.Index%2A?displayProperty=nameWithType> vlastnost označuje pozici založenou na nule ve vstupním řetězci, ve kterém začíná odpovídající podřetězec.  
  
 Následující příklad analyzuje vstupní řetězec pro teplotu vybraných měst. Čárka (",") se používá k oddělení města a jeho teploty a středník (";") se používá k oddělení dat každého města. Celý vstupní řetězec představuje jednu shodu. Ve vzoru regulárního výrazu `((\w+(\s\w+)*),(\d+);)+`, který se používá k analýzě řetězce, je název města přiřazen druhé zachytávající skupině a teplota je přiřazena čtvrté zachytávající skupině.  
  
 [!code-csharp[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/cs/capture1.cs#16)]
 [!code-vb[Conceptual.RegularExpressions.ObjectModel#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regularexpressions.objectmodel/vb/capture1.vb#16)]  
  
 Regulární výraz je definován tak, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`(\s\w+)*`|Porovná nula nebo více výskytů prázdného znaku následovaného jedním nebo více znaky slova. Tento vzor odpovídá víceslovým názvům měst. Toto je třetí zachytávající skupina.|  
|`(\w+(\s\w+)*)`|Porovná jeden nebo více znaků slova následovaných nulou nebo více výskyty prázdného znaku a jedním nebo více znaky slova. Toto je druhá zachytávající skupina.|  
|`,`|Porovnejte čárku.|  
|`(\d+)`|Porovná jednu nebo více číslic. Toto je čtvrtá zachytávající skupina.|  
|`;`|Porovná středník.|  
|`((\w+(\s\w+)*),(\d+);)+`|Porovná vzorek slova následovaného dalšími slovy následovanými čárkou, jednou nebo více číslicemi a středníkem, jednou nebo vícekrát. Toto je první zachytávající skupina.|  
  
## <a name="see-also"></a>Viz také

- <xref:System.Text.RegularExpressions>
- [Regulární výrazy rozhraní .NET](../../../docs/standard/base-types/regular-expressions.md)
- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
