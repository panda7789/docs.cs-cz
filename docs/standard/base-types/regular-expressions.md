---
title: .NET Framework regulární výrazy
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pattern-matching with regular expressions, about pattern-matching
- substrings
- searching with regular expressions, about regular expressions
- pattern-matching with regular expressions
- searching with regular expressions
- parsing text with regular expressions
- regular expressions [.NET Framework], about regular expressions
- regular expressions [.NET Framework]
- .NET Framework regular expressions, about
- characters [.NET Framework], regular expressions
- parsing text with regular expressions, overview
- .NET Framework regular expressions
- strings [.NET Framework], regular expressions
ms.assetid: 521b3f6d-f869-42e1-93e5-158c54a6895d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 89b527d4febb677512b3cdcf7cd47344d182ae26
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736853"
---
# <a name="net-regular-expressions"></a>Regulární výrazy .NET
Regulární výrazy poskytují výkonnou, flexibilní a efektivní metodu pro zpracování textu. Rozsáhlý zápis regulárních výrazů, který odpovídá vzoru, vám umožní rychle analyzovat velké objemy textu a najít konkrétní vzorové vzory znaků. ověření textu, aby se zajistilo, že odpovídá předdefinovanému vzoru (jako je e-mailová adresa); k extrakci, úpravám, nahrazení nebo odstranění podřetězců textu; a k přidání extrahovaných řetězců do kolekce, aby bylo možné vytvořit sestavu. Pro mnoho aplikací, které využívají řetězce nebo analyzují velké bloky textu, regulární výrazy jsou nepostradatelným nástrojem.  
  
## <a name="how-regular-expressions-work"></a>Jak regulární výrazy fungují  
 Centerpiece zpracování textu pomocí regulárních výrazů je modul regulárních výrazů, který je reprezentován objektem <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> v rozhraní .NET. Minimální zpracování textu pomocí regulárních výrazů vyžaduje, aby byl modul regulárních výrazů k dispozici s následujícími dvěma položkami informací:  
  
- Vzor regulárního výrazu pro identifikaci v textu.  
  
     V rozhraní .NET jsou vzory regulárních výrazů definovány speciální syntaxí nebo jazykem, který je kompatibilní s regulárními výrazy jazyka Perl 5 a přidává další funkce, jako je například shoda zprava doleva. Další informace najdete v tématu [Jazyk regulárních výrazů – rychlé reference](regular-expression-language-quick-reference.md).  
  
- Text, který se má analyzovat pro vzor regulárního výrazu.  
  
 Metody třídy <xref:System.Text.RegularExpressions.Regex> umožňují provádět následující operace:  
  
- Určete, zda se vzor regulárního výrazu vyskytuje ve vstupním textu voláním metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType>. Příklad, který používá metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> pro ověření textu, naleznete v tématu [How to: Verify in platný formát e-mailu](how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- Načtěte jeden nebo všechny výskyty textu, který odpovídá vzoru regulárního výrazu, voláním metody <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>. Předchozí metoda vrátí objekt <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType>, který poskytuje informace o odpovídajícím textu. Druhá vrátí objekt <xref:System.Text.RegularExpressions.MatchCollection>, který obsahuje jeden objekt <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> pro každou shodu nalezenou v analyzovaném textu.  
  
- Nahraďte text, který odpovídá vzoru regulárního výrazu, voláním metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>. Příklady, které používají metodu <xref:System.Text.RegularExpressions.Regex.Replace%2A> ke změně formátů data a odebírání neplatných znaků z řetězce, naleznete v tématu [How to: proložení neplatných znaků z řetězce](how-to-strip-invalid-characters-from-a-string.md) a [Příklad: Změna formátů data](regular-expression-example-changing-date-formats.md).  
  
 Přehled modelu objektu regulárních výrazů naleznete v tématu [model objektu regulárních výrazů](the-regular-expression-object-model.md).  
  
 Další informace o jazyce regulárních výrazů najdete v tématu [Jazyk regulárních výrazů – rychlé reference](regular-expression-language-quick-reference.md) nebo stažení a tisk jedné z těchto brožur:  
  
 [Rychlá reference ve formátu aplikace Word (. docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Rychlá reference ve formátu PDF (. PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Příklady regulárních výrazů  
 Třída <xref:System.String> obsahuje řadu metod pro vyhledávání a nahrazování řetězců, které lze použít, pokud chcete najít řetězce literálů ve větším řetězci. Regulární výrazy jsou nejužitečnější, pokud chcete najít jeden z několika podřetězců ve větším řetězci, nebo pokud chcete identifikovat vzory v řetězci, jak ukazuje následující příklad.  
  
### <a name="example-1-replacing-substrings"></a>Příklad 1: Nahrazení podřetězců  
 Předpokládejme, že seznam adresátů obsahuje názvy, které v některých případech obsahují název (MR, paní, chybíš nebo MS), a to spolu s křestním a posledním jménem. Pokud nechcete zahrnout názvy při generování štítků obálek ze seznamu, můžete použít regulární výraz pro odebrání nadpisů, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Regex#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Vzor regulárního výrazu `(Mr\.? |Mrs\.? |Miss |Ms\.? )` odpovídá jakémukoli výskytu "Mr", "Mr", "paní", "paní", "chybíš", "MS" nebo "MS". Volání metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nahradí porovnávaný řetězec pomocí <xref:System.String.Empty?displayProperty=nameWithType>; Jinými slovy, odebere ho z původního řetězce.  
  
### <a name="example-2-identifying-duplicated-words"></a>Příklad 2: identifikace duplicitních slov  
 Neúmyslná duplikace slov je běžnou chybou, kterou autoři vytvoří. Regulární výraz lze použít k identifikaci duplicitních slov, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Regex#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Vzor regulárního výrazu `\b(\w+?)\s\1\b` lze interpretovat následujícím způsobem:  
  
|||  
|-|-|  
|`\b`|Začněte na hranici slova.|  
|(\w +?)|Porovnává jeden nebo více znaků slova, ale co nejvíce znaků. Dohromady tvoří skupinu, na kterou se dá odkazovat jako na `\1`.|  
|`\s`|Porovnává s prázdným znakem.|  
|`\1`|Porovná podřetězec, který se rovná skupině s názvem `\1`.|  
|`\b`|Odpovídá hranici slova.|  
  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> je volána s možnostmi regulárních výrazů nastavenými na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>. Operace porovnávání proto rozlišuje velká a malá písmena a příklad identifikuje podřetězec "This this" jako duplikování.  
  
 Všimněte si, že vstupní řetězec obsahuje podřetězec "This? This. Z důvodu použité interpunkční znaménka však není identifikována jako duplikace.  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Příklad 3: dynamické sestavení regulárního výrazu závislého na jazykové verzi  
 Následující příklad znázorňuje výkon regulárních výrazů v kombinaci s flexibilitou, kterou nabízí. Funkce globalizace netto. Pomocí objektu <xref:System.Globalization.NumberFormatInfo> určí formát hodnot měny v aktuální jazykové verzi systému. Pak tyto informace použije k dynamickému sestavení regulárního výrazu, který z textu extrahuje hodnoty měny. Pro každou shodu extrahuje podskupinu, která obsahuje pouze číselný řetězec, převede ji na hodnotu <xref:System.Decimal> a vypočítá Mezisoučet.  
  
 [!code-csharp[Conceptual.Regex#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 V počítači, jehož aktuální jazyková verze je English-USA (EN-US), příklad dynamicky vytvoří regulární výraz `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Tento vzor regulárního výrazu může být interpretován takto:  
  
|||  
|-|-|  
|`\$`|Vyhledá v vstupním řetězci jeden výskyt symbolu dolaru (`$`). Řetězec vzoru regulárního výrazu obsahuje zpětné lomítko pro indikaci, že symbol dolaru má být interpretován doslova, nikoli jako kotvu regulárního výrazu. (Samotný symbol `$` znamená, že by se modul regulárních výrazů měl pokusit zahájit shodu na konci řetězce.) Aby se zajistilo, že symbol měny aktuální jazykové verze není špatně interpretován jako symbol regulárního výrazu, příklad volá metodu <xref:System.Text.RegularExpressions.Regex.Escape%2A?displayProperty=nameWithType> pro řídicí znak.|  
|`\s*`|Vyhledá nula nebo více výskytů prázdného znaku.|  
|`[-+]?`|Vyhledá žádný nebo jeden výskyt kladného znaménka nebo záporného znaménka.|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Vnější závorky kolem tohoto výrazu definují jako zachytávající skupinu nebo dílčí výraz. Pokud je nalezena shoda, informace o této části odpovídajícího řetězce lze načíst z druhého objektu <xref:System.Text.RegularExpressions.Group> v objektu <xref:System.Text.RegularExpressions.GroupCollection> vráceného vlastností <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>. (První prvek v kolekci představuje celou shodu.)|  
|`[0-9]{0,3}`|Vyhledá nulové až tři výskyty desítkových číslic od 0 do 9.|  
|`(,[0-9]{3})*`|Vyhledá nula nebo více výskytů oddělovače skupin následovaných třemi desítkovými číslicemi.|  
|`\.`|Vyhledá jeden výskyt oddělovače desetinných míst.|  
|`[0-9]+`|Vyhledá jednu nebo více desítkových číslic.|  
|`(\.[0-9]+)?`|Vyhledá žádný nebo jeden výskyt oddělovače desetinných míst následovaný alespoň jednou desítkovou číslicí.|  
  
 Pokud je každý z těchto dílčích vzorů nalezen ve vstupním řetězci, shoda je úspěšná a objekt <xref:System.Text.RegularExpressions.Match>, který obsahuje informace o shodě, se přidá do objektu <xref:System.Text.RegularExpressions.MatchCollection>.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Jazyk regulárních výrazů – stručná referenční dokumentace](regular-expression-language-quick-reference.md)|Poskytuje informace o sadě znaků, operátorů a konstrukcích, které lze použít k definování regulárních výrazů.|  
|[Model objektu regulárního výrazu](the-regular-expression-object-model.md)|Poskytuje informace a příklady kódu, které ilustrují, jak používat třídy regulárních výrazů.|  
|[Podrobnosti o chování regulárních výrazů](details-of-regular-expression-behavior.md)|Poskytuje informace o schopnostech a chování regulárních výrazů .NET.|  
|[Příklady regulárních výrazů](regular-expression-examples.md)|Poskytuje příklady kódu, které ilustrují Typická použití regulárních výrazů.|  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Regulární výrazy – rychlé reference (stažení ve wordovém formátu)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Regulární výrazy – rychlé reference (stažení ve formátu PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
