---
title: .NET Framework – regulární výrazy
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
ms.openlocfilehash: 33aaf09e284db5c818eb0ff3917533cce5e70ad7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811654"
---
# <a name="net-regular-expressions"></a>Regulárních výrazů .NET
Regulární výrazy poskytují výkonný, flexibilní a efektivní způsob zpracování textu. Rozsáhlé notace vzoru regulárních výrazů umožňuje rychlé analyzování velkého množství textu k vyhledání konkrétních znakových vzorů; pro ověření textu a ověřte, že souhlasí s předdefinovaným vzorem (jako je například e-mailovou adresu); extrahovat, upravovat, nahrazení nebo odstranění podřetězců textu; a přidávání vyjmutých řetězců do kolekce ke generování sestavy. Pro mnoho aplikací, které pracují s řetězci nebo které analyzují velké textové bloky, jsou regulární výrazy nepostradatelným nástrojem.  
  
## <a name="how-regular-expressions-work"></a>Principy regulárních výrazů  
 Ústředním zpracování textu pomocí regulárních výrazů je modul regulárních výrazů, která je reprezentována <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> objektů v rozhraní .NET. Požadované minimum pro zpracování textu pomocí regulárních výrazů je předání následujících dvou informací modulu regulárních výrazů:  
  
- Vzor regulárního výrazu pro identifikaci v textu.  
  
     V rozhraní .NET jsou vzory regulárních výrazů definovány zvláštní syntaxí nebo jazykem, který je kompatibilní s regulárními výrazy jazyka Perl 5 a přináší několik doplňkových funkcí, jako je například porovnávání zprava doleva. Další informace najdete v tématu [jazyk regulárních výrazů – Stručná referenční příručka](../../../docs/standard/base-types/regular-expression-language-quick-reference.md).  
  
- Text určený k analýze pomocí vzoru regulárního výrazu.  
  
 Metody třídy <xref:System.Text.RegularExpressions.Regex> umožňují provedení následujících operací:  
  
- Určení toho, zda se ve vstupním textu objeví vzor regulárního výrazu po zavolání metody <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType>. Příklad, který se používá <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metodu pro ověření textu, naleznete v tématu [jak: Ověřte, zda jsou řetězce ve formátu platné e-mailové](../../../docs/standard/base-types/how-to-verify-that-strings-are-in-valid-email-format.md).  
  
- Vrácení jednoho nebo všech výskytů textu, který se shoduje se vzorem regulárního výrazu, zavoláním metody <xref:System.Text.RegularExpressions.Regex.Match%2A?displayProperty=nameWithType> nebo metody <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType>. První metoda vrátí objekt <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType>, který poskytuje informace o odpovídajícím textu. Druhá vrátí objekt <xref:System.Text.RegularExpressions.MatchCollection>, který obsahuje jeden objekt <xref:System.Text.RegularExpressions.Match?displayProperty=nameWithType> pro jednotlivé shody v rámci analyzovaného textu.  
  
- Nahrazení textu, který odpovídá vzoru regulárního výrazu zavoláním metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType>. Příklady, které používají <xref:System.Text.RegularExpressions.Regex.Replace%2A> metodu pro změnu formátu data a odstranění neplatných znaků z řetězce, naleznete v tématu [jak: Odstranění neplatných znaků z řetězce](../../../docs/standard/base-types/how-to-strip-invalid-characters-from-a-string.md) a [příkladu: Změna formátů data](../../../docs/standard/base-types/regular-expression-example-changing-date-formats.md).  
  
 Přehled modelu objektu regulárního výrazu, naleznete v tématu [The Model objektu regulárního výrazu](../../../docs/standard/base-types/the-regular-expression-object-model.md).  
  
 Další informace o jazyce regulárních výrazů, naleznete v tématu [jazyk regulárních výrazů – Stručná referenční příručka](../../../docs/standard/base-types/regular-expression-language-quick-reference.md) nebo stáhnout a vytisknout jednu z těchto brožury:  
  
 [Stručná referenční příručka ve formátu aplikace Word (.docx)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Stručná referenční příručka ve formátu PDF (PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)  
  
## <a name="regular-expression-examples"></a>Příklady regulárních výrazů  
 Třída <xref:System.String> zahrnuje celou řadu metod pro vyhledání nebo nahrazení řetězce, které lze ve větším řetězci použít při vyhledávání textových literálů. Regulární výrazy jsou nejužitečnější při hledání jednoho nebo více dílčích podřetězců ve větším řetězci, nebo při identifikaci vzorů v řetězci, jak je znázorněno v následujícím příkladu.  
  
### <a name="example-1-replacing-substrings"></a>Příklad 1: Nahrazení podřetězců  
 Předpokládejme seznam, který obsahuje jména a který může u jména a příjmení zahrnovat také oslovení (Mr., Mrs., Miss, nebo Ms.). Pokud při vytváření popisků ze seznamu nechcete oslovení zahrnout, můžete oslovení odstranit pomocí regulárního výrazu, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[Conceptual.Regex#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example1.cs#2)]
 [!code-vb[Conceptual.Regex#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example1.vb#2)]  
  
 Vzor regulárního výrazu`(Mr\.? |Mrs\.? |Miss |Ms\.? )` shoduje s jakýmkoli výskytem "Mr", "pan", "Mrs", "Paní", "Miss", "Ms nebo"Ms.". Volání metody <xref:System.Text.RegularExpressions.Regex.Replace%2A?displayProperty=nameWithType> nahradí vyhledaný řetězec <xref:System.String.Empty?displayProperty=nameWithType>; jinými slovy to znamená, že jej z původního řetězce odstraní.  
  
### <a name="example-2-identifying-duplicated-words"></a>Příklad 2: Nalezení duplicitních slov  
 Nechtěně zdvojená slova jsou běžnou chybou, které se autoři při psaní dopouštějí. Zdvojená slova mohou být vyhledána pomocí regulárního výrazu, jak znázorňuje následující příklad.  
  
 [!code-csharp[Conceptual.Regex#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example2.cs#3)]
 [!code-vb[Conceptual.Regex#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example2.vb#3)]  
  
 Vzor regulárního výrazu `\b(\w+?)\s\1\b` může být interpretován takto:  
  
|||  
|-|-|  
|`\b`|Začne na hranici slova.|  
|(\w+?)|Porovná jeden nebo více znaků slova, ale co nejméně znakům nejvíce. Společně tvoří skupiny, které lze odkazovat jako `\1`.|  
|`\s`|Porovná prázdný znak.|  
|`\1`|Porovná podřetězec, který se shoduje se skupinou s názvem `\1`.|  
|`\b`|Porovná hranici slova.|  
  
 Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A?displayProperty=nameWithType> je zavolána pomocí možností regulárního výrazu, které jsou nastaveny jako <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>. Operace shody proto rozlišuje velká a malá písmena a příklad vyhodnotí podřetězec „Tento tento“ jako zdvojené slovo.  
  
 Vstupní řetězec obsahuje podřetězec „tento? Tento“. Z důvodu výskytu otazníku však nedojde k vyhodnocení výrazu jako zdvojeného slova.  
  
### <a name="example-3-dynamically-building-a-culture-sensitive-regular-expression"></a>Příklad 3: Dynamické vytvoření regulárního výrazu zohledňující jazykovou verzi  
 Následující příklad ukazuje sílu regulárních výrazů spolu s flexibilitou, kterou nabízejí. Funkce pro globalizaci vaší sítě. Formát měny v aktuální jazykové verzi systému určuje objekt <xref:System.Globalization.NumberFormatInfo>. Tuto informaci následně používá k vytvoření regulárního výrazu, který z textu extrahuje hodnoty měny. Pro jednotlivé shody extrahuje podskupinu obsahující pouze číselný řetězec, převede jej na hodnotu <xref:System.Decimal> a vypočte mezisoučet.  
  
 [!code-csharp[Conceptual.Regex#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex/cs/example.cs#1)]
 [!code-vb[Conceptual.Regex#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex/vb/example.vb#1)]  
  
 Na počítači, jehož aktuální jazyková verze je angličtina - Spojené státy (en US), příklad dynamicky sestaví regulární výraz `\$\s*[-+]?([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`. Tento vzor regulárního výrazu může být interpretován takto:  
  
|||  
|-|-|  
|`\$`|Vyhledá ve vstupním řetězci jeden výskyt symbolu dolaru ($). Vzor regulárního výrazu obsahuje zpětné lomítko pro označení toho, zda bude symbol dolaru spíše interpretován doslovně, než aby byl použit jako ukotvení regulárního výrazu. (Samostatný symbol $ by označoval, že by se měl modul regulárního výrazu pokusit začít vyhledávat shodu na konci řetězce.) Aby symbol místní měny nebyl nesprávně interpretován jako symbol regulárního výrazu, zavolá příklad z důvodu vynechání znaku metodu <xref:System.Text.RegularExpressions.Regex.Escape%2A>.|  
|`\s*`|Vyhledá žádný nebo několik výskytů znaku mezery.|  
|`[-+]?`|Vyhledá žádný nebo jeden ze znaků plus nebo mínus.|  
|`([0-9]{0,3}(,[0-9]{3})*(\.[0-9]+)?)`|Vnější závorky výrazu jej definují jako zachytávající skupinu nebo jako dílčí výraz. Při nalezení shody může být informace o části vyhovujícího řetězce vrácena druhým objektem <xref:System.Text.RegularExpressions.Group> v rámci objektu <xref:System.Text.RegularExpressions.GroupCollection> vráceného vlastností <xref:System.Text.RegularExpressions.Match.Groups%2A?displayProperty=nameWithType>. (První prvek v kolekci představuje celkovou shodu.)|  
|`[0-9]{0,3}`|Vyhledá žádný až tři výskyty desítkových číslic od 0 do 9.|  
|`(,[0-9]{3})*`|Vyhledá žádný nebo několik výskytů oddělovače skupin, za kterým následují tři desítkové číslice.|  
|`\.`|Vyhledá jeden výskyt oddělovače desetinných míst.|  
|`[0-9]+`|Vyhledá jednu nebo několik desítkových číslic.|  
|`(\.[0-9]+)?`|Vyhledá žádný nebo jeden výskyt oddělovače desetinných míst následovaného alespoň jednou desítkovou číslicí.|  
  
 Pokud je v rámci vstupního řetězce každý z těchto dílčích vzorů vyhledán, dojde k nalezení shody a objekt <xref:System.Text.RegularExpressions.Match>, který obsahuje informaci o shodě, je přidán do objektu <xref:System.Text.RegularExpressions.MatchCollection>.  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)|Poskytuje informace o sadách znaků, operátorech a konstrukcích, které lze použít pro definování regulárních výrazů.|  
|[Model objektu regulárního výrazu](../../../docs/standard/base-types/the-regular-expression-object-model.md)|Poskytuje informace a příklady kódu znázorňující způsob používání tříd regulárních výrazů.|  
|[Podrobnosti k chování regulárních výrazů](../../../docs/standard/base-types/details-of-regular-expression-behavior.md)|Poskytuje informace o možnostech a chování regulárních výrazů .NET.|  
|[Příklady regulárních výrazů](../../../docs/standard/base-types/regular-expression-examples.md)|Poskytuje příklady kódu, které znázorňují typické způsoby používání regulárních výrazů.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Text.RegularExpressions?displayProperty=nameWithType>  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Regulárních výrazů – Stručná referenční příručka (ke stažení ve Wordovém formátu)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.docx)  
 [Regulárních výrazů – Stručná referenční příručka (ke stažení ve formátu PDF)](https://download.microsoft.com/download/D/2/4/D240EBF6-A9BA-4E4F-A63F-AEB6DA0B921C/Regular%20expressions%20quick%20reference.pdf)
