---
title: Možnosti regulárních výrazů
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- regular expressions, options
- constructs, options
- .NET Framework regular expressions, options
- inline option constructs
- options parameter
ms.assetid: c82dc689-7e82-4767-a18d-cd24ce5f05e9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f3c229b0fc463863b7113c7ba73890b84e86553b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579649"
---
# <a name="regular-expression-options"></a>Možnosti regulárních výrazů
<a name="Top"></a> Ve výchozím nastavení při porovnání vstupní řetězec se znaky literálu v vzor regulárního výrazu je velká a malá písmena, prázdné znaky v vzor regulárního výrazu interpretována jako literál prázdné znaky a zaznamenávání skupiny v regulárním výrazu jsou pojmenované implicitně také jako explicitně. Tyto a několik dalších aspektů výchozího chování regulárních výrazů můžete upravit zadáním možnosti regulárních výrazů. Tyto možnosti, které jsou uvedené v následující tabulce, mohou být zahrnuty vložené jako součást regulární výraz nebo mohou být poskytnuty <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktoru třídy nebo statické vzor jako odpovídající metodu <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> hodnota výčtu.  
  
|Člen RegexOptions|Vložený znak|Efekt|  
|-------------------------|----------------------|------------|  
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Není k dispozici|Použijte výchozí chování. Další informace najdete v tématu [výchozí možnosti](#Default).|  
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Použije porovnávání, které nerozlišuje velká a malá písmena. Další informace najdete v tématu [porovnávání](#Case).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Použití víceřádkového režimu, kde `^` a `$` odpovídají začátku a konci řádku (namísto začátek a konec vstupní řetězec). Další informace najdete v tématu [víceřádkových režimu](#Multiline).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Použití režimu jeden řádek, kde tečka (.) odpovídá každý znak (místo každých znaku kromě `\n`). Další informace najdete v tématu [Jednořákový režim](#Singleline).|  
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Nezachytí nepojmenované skupiny. Jediné platné zachycení explicitně s názvem nebo číslované skupiny formuláře `(?<` *název* `>` *dílčím výrazu*`)`. Další informace najdete v tématu [pouze explicitní zachycení](#Explicit).|  
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Není k dispozici|Zkompilujte regulární výraz k sestavení. Další informace najdete v tématu [kompilované regulární výrazy](#Compiled).|  
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Vyloučit z vzoru prázdný znak a povolte komentáře po znaku (`#`). Další informace najdete v tématu [ignorovat mezer](#Whitespace).|  
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Není k dispozici|Změňte směr vyhledávání. Hledání přesune zprava doleva místo zleva doprava. Další informace najdete v tématu [režim zprava doleva](#RightToLeft).|  
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Není k dispozici|Povolte chování ECMAScript výrazu. Další informace najdete v tématu [ECMAScript chování porovnávání](#ECMAScript).|  
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Není k dispozici|Ignorujte rozdíly v jazyce. Další informace najdete v tématu [porovnání s použitím neutrální jazykovou verzi](#Invariant).|  
  
## <a name="specifying-the-options"></a>Zadání možností  
 Možnosti regulárních výrazů můžete zadat v jednom ze tří způsobů:  
  
-   V `options` parametr <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktoru třídy nebo statické (`Shared` v jazyce Visual Basic) porovnávání metoda, jako například <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. `options` Parametr je bitovou kombinaci nebo <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> uvedené hodnoty.  
  
     Když jsou možnosti zadaný do <xref:System.Text.RegularExpressions.Regex> instance pomocí `options` parametr konstruktoru třídy, možnosti jsou přiřazené k <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> vlastnost. Ale <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> vlastnost nezohledňuje vložených možností v samotné vzor regulárního výrazu.  
  
     V následujícím příkladu je uvedena ukázka. Použije `options` parametr <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda pro povolení porovnávání a ignorování prázdných znaků při identifikaci slova začínající písmenem "d".  
  
     [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
     [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]  
  
-   Použitím vložených možností v vzor regulárního výrazu se syntaxí `(?imnsx-imnsx)`. Možnost se vztahuje na vzoru z bodu, zda je možnost definováno buď na konec vzoru nebo do bodu, kdy je možnost zrušena pomocí jiné vložené možnosti. Všimněte si, že <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> vlastnost <xref:System.Text.RegularExpressions.Regex> instance nebere v úvahu tyto možnosti vložené. Další informace najdete v tématu [různé vytvoří](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) tématu.  
  
     V následujícím příkladu je uvedena ukázka. Používá vložené možnosti pro povolení porovnávání a ignorování prázdných znaků při identifikaci slova začínající písmenem "d".  
  
     [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
     [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]  
  
-   Použitím vložených možností v konkrétní skupině vytvořit v vzor regulárního výrazu se syntaxí `(?imnsx-imnsx:` *dílčím výrazu*`)`. Žádné přihlášení, než sada možností zapne sadu; znaménkem minus před sadu možností sadu vypne. (`?` je pevnou součástí syntaxe jazyka konstrukce, která je požadována, jestli jsou možnosti povolená nebo zakázaná.) Možnost se vztahuje pouze na tuto skupinu. Další informace najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
     V následujícím příkladu je uvedena ukázka. Pro povolení porovnávání a ignorování prázdných znaků při identifikaci slova začínající písmenem "d" použije v seskupovací konstrukce vložených možností.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
     [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]  
  
 Pokud jsou možnosti zadaný vložené znaménkem minus (`-`) před možností nebo sadou možností vypne tyto možnosti. Můžete například vytvořit vložený `(?ix-ms)` Zapne <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> a vypne možnosti <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnosti. Ve výchozím nastavení jsou vypnuté všechny možnosti regulárních výrazů.  
  
> [!NOTE]
>  Pokud zadané možnosti regulárních výrazů v `options` zadán parametr konstruktoru nebo metoda konfliktu volání s možností vložené v vzor regulárního výrazu, jsou použity vložené možnosti.  
  
 Následujících pět možnosti regulárních výrazů můžete nastavit, jak se parametr možností a vložené:  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>  
  
 Následujících pět možnosti regulárních výrazů se dá nastavit pomocí `options` parametru ale nejde nastavit vložený:  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>  
  
-   <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>  
  
## <a name="determining-the-options"></a>Určení možnosti  
 Můžete určit, které možnosti byly poskytnuty <xref:System.Text.RegularExpressions.Regex> objektu, když byla vytvořena instance načtením hodnotu jen pro čtení <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> vlastnost. Tato vlastnost je obzvláště užitečné pro určení možnosti, které jsou definovány pro kompilované regulární výraz vytvořené <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metoda.  
  
 K testování přítomnost jakákoliv možnost, s výjimkou <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, provedení určité operace, a s hodnotou <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> vlastnost a <xref:System.Text.RegularExpressions.RegexOptions> hodnotu, která vás zajímá. Pak test, zda se výsledek rovná <xref:System.Text.RegularExpressions.RegexOptions> hodnotu. Následující příklad testy jestli <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> byla nastavena možnost.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
 [!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]  
  
 K testování pro <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, určit, zda hodnota <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> vlastnost rovná <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, jak ukazuje následující příklad.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
 [!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]  
  
 Následující části uvádějí možnosti podporované regulárnímu výrazu v rozhraní .NET.  
  
<a name="Default"></a>   
## <a name="default-options"></a>Výchozí možnosti  
 <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Možnost označuje, že nebyly zadány žádné možnosti a modul regulární výraz používá jeho výchozí chování. To zahrnuje následující:  
  
-   Vzor interpretována jako kanonický spíše než regulární výraz ECMAScript.  
  
-   Regulární výraz je nalezena shoda s ve vstupním řetězci zleva doprava.  
  
-   Porovnávání rozlišuje velká a malá písmena.  
  
-   `^` a `$` odpovídat prvků jazyka začátek a konec vstupní řetězec.  
  
-   `.` Jazyk element odpovídá každých znaku kromě `\n`.  
  
-   Všechny prázdné znaky v vzor regulárního výrazu interpretována jako literál mezerou.  
  
-   Porovnávání vzoru vstupní řetězec se používají konvence aktuální jazykové verze.  
  
-   Implicitní, jakož i explicitní jsou zaznamenávání skupiny regulární výraz.  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Možnost nemá žádný vložený ekvivalent. Po přiřazený možnosti regulárních výrazů se výchozí chování je obnovena na základě možnost možnost vypnutím určité možnosti. Například `(?i)` zapne porovnávání, a `(?-i)` obnoví výchozí porovnávání malá a velká písmena.  
  
 Protože <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> možnost představuje výchozí chování modul regulárních výrazů, jsou zřídka explicitně zadány při volání metody. Konstruktor nebo statickou metodu porovnávání bez `options` parametr se nazývá místo.  
  
 [Zpět na začátek](#Top)  
  
<a name="Case"></a>   
## <a name="case-insensitive-matching"></a>Porovnávání  
 <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> Možnost, nebo `i` poskytuje možnost inline porovnávání. Ve výchozím nastavení se používají konvence velká a malá písmena aktuální jazykové verze.  
  
 V následujícím příkladu definuje vzor regulárního výrazu `\bthe\w*\b`, který odpovídá všechna slova začínající na "na". Vzhledem k tomu, že první volání <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda používá výchozí porovnání malá a velká písmena, výstup znamená, že řetězec "Na", který začíná věta se neshoduje. Je nalezena shoda při <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda je volána s možnostmi nastavenými na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
 [!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]  
  
 Následující příklad změní vzor regulárního výrazu z předchozího příkladu použití možností vložené místo `options` parametr pro poskytnutí porovnávání. První vzorek definuje volbou rozlišování velikosti písmen v seskupovací konstrukce, která se vztahuje pouze na písmeno "t" v řetězci "na". Protože konstrukce možnosti vyskytuje na začátku vzor, druhý vzorek použije volbou rozlišování velikosti písmen na celý regulární výraz.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
 [!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]  
  
 [Zpět na začátek](#Top)  
  
<a name="Multiline"></a>   
## <a name="multiline-mode"></a>Víceřádkového režimu  
 <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> Možnost, nebo `m` možnost inline umožňuje modulu regulární výraz zpracovat vstupní řetězec, který se skládá z více řádků. Změní výklad `^` a `$` jazykové elementy tak, aby odpovídaly začátku a konci řádku, místo začátek a konec vstupní řetězec.  
  
 Ve výchozím nastavení `$` odpovídá pouze konci vstupní řetězec. Pokud zadáte <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost, odpovídá buď znaku (`\n`) nebo na konci vstupní řetězec. Ale neodpovídá kombinaci znaků vrátit znaků CR/nového řádku. Chcete-li úspěšně porovnávat, použijte dílčí výraz `\r?$` místo právě `$`.  
  
 Následující příklad extrahuje jména a skóre nadhazovačů a přidá je do <xref:System.Collections.Generic.SortedList%602> kolekce, která je seřadí v sestupném pořadí. <xref:System.Text.RegularExpressions.Regex.Matches%2A> Metoda je volána dvakrát. Při prvním volání metoda regulární výraz je `^(\w+)\s(\d+)$` a nejsou nastaveny žádné možnosti. Jak ukazuje výstup, protože modul regulárních výrazů se nemůže shodovat vstupní vzor společně s začátek a konec vstupní řetězec, nebyly nalezeny žádné odpovídající položky. V druhé volání metody s regulárním výrazem se změní na `^(\w+)\s(\d+)\r?$` a možnosti jsou nastaveny na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Jak ukazuje výstup, názvy a skóre jsou úspěšně porovnány a skóre jsou zobrazeny v sestupném pořadí.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
 [!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]  
  
 Regulární výraz `^(\w+)\s(\d+)\r*$` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`^`|Začít na začátku řádku.|  
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|  
|`\s`|Porovná prázdný znak.|  
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je druhá zachytávající skupina.|  
|`\r?`|Odpovídat návratový znak žádnou nebo jednu.|  
|`$`|Ukončení na konci řádku.|  
  
 Následující příklad je ekvivalentní k té předchozí, s tím rozdílem, že používá možnost inline `(?m)` nastavit možnost víceřádkový.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
 [!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]  
  
 [Zpět na začátek](#Top)  
  
<a name="Singleline"></a>   
## <a name="single-line-mode"></a>Jeden řádek režimu  
 <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> Možnost, nebo `s` možnost inline způsobí, že modul regulární výraz zachází vstupní řetězec, jako kdyby se skládá z jednoho řádku. Dělá to tak, že změníte chování období (`.`) jazyk elementu, které odpovídá každý znak, místo odpovídající každý znak s výjimkou znak nového řádku `\n` nebo \u000A.  
  
 Následující příklad ukazuje, jak chování `.` jazyk element změny při použití <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnost. Regulární výraz `^.+` spustí na začátku řetězce a odpovídá každý znak. Ve výchozím nastavení shody končí na konci prvního řádku. regulární výraz odpovídá znakem konce řádku, `\r` nebo \u000D, ale neodpovídá `\n`. Protože <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnost interpretuje celý vstupní řetězec jako jeden řádek, porovnává každý znak ve vstupním řetězci, včetně `\n`.  
  
 [!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
 [!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]  
  
 Následující příklad je ekvivalentní k té předchozí, s tím rozdílem, že používá možnost inline `(?s)` chcete povolit režim jeden řádek.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
 [!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]  
  
 [Zpět na začátek](#Top)  
  
<a name="Explicit"></a>   
## <a name="explicit-captures-only"></a>Explicitní zaznamená  
 Ve výchozím nastavení zaznamenávání skupiny jsou definované závorky v regulární výraz. S názvem skupiny přiřazené názvu nebo čísla podle `(?<` *název*`>`*dílčím výrazu* `)` možnosti jazyka nepojmenované skupiny jsou přístupné pro index. V <xref:System.Text.RegularExpressions.GroupCollection> objektu nepojmenované skupiny předcházejí s názvem skupiny.  
  
 Seskupovací konstrukce se často používají jenom pro použití kvantifikátory víc elementů jazyka a zachycené podřetězce nejsou nejsou důležité. Například pokud následujícímu regulárnímu výrazu:  
  
```  
\b\(?((\w+),?\s?)+[\.!?]\)?  
```  
  
 je určen pouze k extrahování věty obsahující končit tečkou, vykřičník nebo otazník z dokumentu, pouze výsledná věta (která je reprezentována <xref:System.Text.RegularExpressions.Match> objektu) je určen. Jednotlivých slov v kolekci nejsou.  
  
 Zaznamenání skupiny, které nepoužívají následně může být náročné, protože modul regulárních výrazů musí naplnit obě <xref:System.Text.RegularExpressions.GroupCollection> a <xref:System.Text.RegularExpressions.CaptureCollection> objekty kolekce. Jako alternativu, můžete použít buď <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> možnost nebo `n` vložené možnost určit, že jsou jediné platné zachycení explicitně s názvem nebo číslované skupiny, které jsou určené, které `(?<` *název* `>` *dílčím výrazu* `)` vytvořit.  
  
 Tento příklad zobrazuje informace o shodách vrácené `\b\(?((\w+),?\s?)+[\.!?]\)?` vzor regulárního výrazu, kdy <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda je volána s i bez <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> možnost. Jako výstup z první metodu ukazuje volání, modul regulárních výrazů plně naplní <xref:System.Text.RegularExpressions.GroupCollection> a <xref:System.Text.RegularExpressions.CaptureCollection> kolekce objektů s informacemi o zaznamenané dílčích řetězců. Protože druhý metoda je volána s `options` nastavena na <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, nezachycuje informace o skupinách.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
 [!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]  
  
 Regulární výraz`\b\(?((?>\w+),?\s?)+[\.!?]\)?` je definovaný jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`\b`|Začněte na hranici slova.|  
|`\(?`|Porovná žádnou nebo jednu výskytů levé závorky ("(").|  
|`(?>\w+),?`|Porovná jeden nebo více znaků slova následuje žádnou nebo jednu čárkami. Nevrací se při kontrole shody znaků slova.|  
|`\s?`|Porovná žádný nebo jeden prázdný znak.|  
|`((\w+),?\s?)+`|Shodovat s kombinací jeden nebo více znaků slova, žádnou nebo jednu čárkami a nula nebo jeden prázdným znakem jeden či více krát.|  
|`[\.!?]\)?`|Odpovídat žádné z tří interpunkčních znamének, za nímž následuje žádnou nebo jednu uzavírací závorky (")").|  
  
 Můžete také `(?n)` vloženého elementu pro potlačení automatických zachycení. Následující příklad změní použitím předchozího vzoru názvů regulární výraz k použití `(?n)` vloženého elementu místo <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> možnost.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
 [!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]  
  
 Nakonec můžete použít skupiny vloženého elementu `(?n:)` pro potlačení automatických zachycení na základě podle skupiny. Následující příklad změní použitím předchozího vzoru názvů pro potlačení nepojmenované zachycení ve vnější skupiny `((?>\w+),?\s?)`. Všimněte si, že to potlačí nepojmenované zaznamená v informacích o vnitřní skupiny.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
 [!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]  
  
 [Zpět na začátek](#Top)  
  
<a name="Compiled"></a>   
## <a name="compiled-regular-expressions"></a>Kompilované regulární výrazy  
 Ve výchozím nastavení se interpretují regulární výrazy v rozhraní .NET. Když <xref:System.Text.RegularExpressions.Regex> je objekt vytvořenou instanci nebo statické <xref:System.Text.RegularExpressions.Regex> metoda je volána, regulární výraz je analyzován do sady vlastních operačních kódů a překladač používá tyto operační kódy ke spuštění regulárního výrazu. To vyžaduje kompromis: náklady inicializace modulu regulární výraz je minimalizován za cenu výkon.  
  
 Můžete použít zkompilován místo interpretovaný regulární výrazy s použitím <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost. V takovém případě když vzor předána modul regulárních výrazů, ho je analyzován do sady operačních kódů a potom převedou do Microsoft (MSIL intermediate language), které lze předat přímo modul common language runtime. Kompilované regulární výrazy maximalizovat výkon za cenu čas inicializace.  
  
> [!NOTE]
>  Regulární výraz může být zkompilovány pouze zadáním <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> hodnotu `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statickou metodu porovnávání. Není k dispozici možnost vložené.  
  
 Můžete použít kompilované regulární výrazy ve voláních statických a instance regulární výrazy. V statické regulární výrazy <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost předána `options` parametru metody porovnávání regulární výraz. V regulárních výrazech instanci, je předána `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy. V obou případech je výsledkem lepší výkon.  
  
 Toto zvýšení výkonu však dochází pouze za následujících podmínek:  
  
-   A <xref:System.Text.RegularExpressions.Regex> objekt, který reprezentuje konkrétní regulární výraz se používá v několika volání metody porovnávání regulárních výrazů.  
  
-   <xref:System.Text.RegularExpressions.Regex> Objektu nelze dostala mimo rozsah, proto ji můžete znovu použít.  
  
-   Statické regulární výraz se používá v několika volání metody porovnávání regulárních výrazů. (Zlepšení výkonu je možné, protože používá při voláních statickou metodu regulární výrazy jsou uloženy v mezipaměti modul regulárních výrazů.)  
  
> [!NOTE]
>  <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> Možnost je nezávislá na <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metoda, která vytvoří speciální sestavení, která obsahuje předdefinované kompilované regulární výrazy.  
  
 [Zpět na začátek](#Top)  
  
<a name="Whitespace"></a>   
## <a name="ignore-white-space"></a>Ignorovat prázdné znaky  
 Ve výchozím nastavení je prázdné místo v vzor regulárního výrazu důležité; Vynutí modul regulárních výrazů tak, aby odpovídaly prázdný znak ve vstupním řetězci. Z toho důvodu regulární výraz "`\b\w+\s`"a"`\b\w+` " jsou přibližně ekvivalentem regulární výrazy. Kromě toho když křížku (#) se vyskytuje v vzor regulárního výrazu, je interpretován jako literál znak pro porovnání.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> Možnost, nebo `x` možnost inline změní toto výchozí chování následujícím způsobem:  
  
-   Prázdný znak v regulární výraz je ignorován. Jako součást vzor regulárního výrazu, je nutné uvést prázdné znaky (například jako `\s` nebo "`\` ").  
  
-   Znaménko čísla (#) interpretována jako začátek komentář, nikoli jako literál znak. Veškerého textu v vzor regulárního výrazu z znak # na konci řetězce interpretována jako komentář.  
  
 Ale v těchto případech prázdné znaky v regulárním výrazu nejsou ignorovány, i když používáte <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> možnost:  
  
-   Prázdné znaky v rámci třídy znak je vždy interpretovány oznámena. Například vzor regulárního výrazu `[ .,;:]` odpovídá žádné jeden prázdný znak, období, čárkou, středníkem nebo středníkem.  
  
-   Mezer není povolen v závorkách kvantifikátor, jako například `{` *n*`}`, `{` *n*`,}`, a `{` *n* `,` *m*`}`. Například vzor regulárního výrazu `\d{1. 3}` selže tak, aby odpovídaly žádné posloupností číslic od jedné do tří číslic, protože obsahuje prázdné znaky.  
  
-   Prázdné znaky není povoleno v rámci sekvence znaků, která představuje element jazyka. Příklad:  
  
    -   Element jazyk `(?:` *dílčím výrazu* `)` představuje skupinu bez zachycení a `(?:` část elementu nelze vložených mezer. Vzor `(? :` *dílčím výrazu* `)` vyvolá <xref:System.ArgumentException> v spustit času, protože modul regulárních výrazů nelze analyzovat vzoru a vzor `( ?:` *dílčím výrazu*  `)` selže tak, aby odpovídaly *dílčím výrazu*.  
  
    -   Element jazyk `\p{` *název*`}`, která představuje kategorii Unicode nebo pojmenovaného blok, nesmí obsahovat mezery v `\p{` část elementu. Pokud obsahovat prázdné znaky, vyvolá elementu <xref:System.ArgumentException> za běhu.  
  
 Povolením této možnosti pomáhá zjednodušit regulární výrazy, které jsou často obtížně analyzovat a pochopit. Zlepšuje čitelnost a umožňuje dokumentu regulární výraz.  
  
 V následujícím příkladu definuje následující vzor regulárního výrazu:  
  
 `\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`  
  
 Je podobná vzoru definované v tomto vzoru [pouze explicitní zachycení](#Explicit) tématu, s tím rozdílem, že se používá <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> možnosti ignorování prázdných znaků.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
 [!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]  
  
 Následující příklad používá možnost inline `(?x)` ignorovat prázdných znaků.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
 [!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]  
  
 [Zpět na začátek](#Top)  
  
<a name="RightToLeft"></a>   
## <a name="right-to-left-mode"></a>Režim zprava doleva  
 Ve výchozím nastavení modul regulárních výrazů vyhledá zleva doprava. Můžete obrátit směr vyhledávání pomocí <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> možnost. Hledání automaticky začíná na poslední pozice znaku řetězce. Pro porovnávání metody, které zahrnují počáteční pozice parametru, jako například <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>, počáteční pozice je index nejvíce vpravo znak na pozici, na které má začít prohledávání.  
  
> [!NOTE]
>  Režim vzorku zprava doleva je k dispozici pouze zadáním <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> hodnotu `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statickou metodu porovnávání. Není k dispozici možnost vložené.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> Možnost změny pouze směr vyhledávání; neinterpretuje vzor regulárního výrazu zprava doleva. Například regulární výraz `\bb\w+\s` odpovídá slova, která začíná písmenem "b" a jsou následuje prázdný znak. V následujícím příkladu vstupní řetězec skládá ze tří slov, které obsahují jeden nebo více znaků "b". První slovo začíná "b", "b" a třetí druhé končí obsahuje dva znaky "b" uprostřed slova. Jak ukazuje výstup z příkladu, odpovídá pouze první slovo regulární výraz.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
 [!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]  
  
 Všimněte si také, že dopředné ( `(?=` *dílčím výrazu* `)` element jazyk) a kontrolní výraz ( `(?<=` *dílčím výrazu* `)`jazyk element) nemění směr. Kontrolní výrazy s dopředným vyhledáváním hledají zprava. zpětné vyhledávání hledá na levé straně. Například regulární výraz `(?<=\d{1,2}\s)\w+,?\s\d{4}` používá kontrolní výraz k testování data, která předchází název měsíce. Regulární výraz pak odpovídá měsíce a roku. Informace o s dopředným vyhledáváním a zpětných hledáních najdete v tématu [seskupení vytvoří](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).  
  
 [!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
 [!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]  
  
 Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
|Vzor|Popis|  
|-------------|-----------------|  
|`(?<=\d{1,2}\s)`|Na začátek shody musí předcházet jedno nebo dvě desetinných míst následované mezerou.|  
|`\w+`|Porovná jeden nebo více znaků slova.|  
|`,?`|Porovná nula nebo jeden znak čárkami.|  
|`\s`|Porovná prázdný znak.|  
|`\d{4}`|Porovná čtyři desítková číslice.|  
  
 [Zpět na začátek](#Top)  
  
<a name="ECMAScript"></a>   
## <a name="ecmascript-matching-behavior"></a>ECMAScript chování porovnávání  
 Ve výchozím nastavení modul regulárních výrazů používá kanonické chování při kontrole shody regulárního výrazu ke vkládání textu. Ale můžete určit, aby používal chování porovnávání zadáním ECMAScript modul regulární výraz <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> možnost.  
  
> [!NOTE]
>  Chování ECMAScript je k dispozici pouze zadáním <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> hodnotu `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statickou metodu porovnávání. Není k dispozici možnost vložené.  
  
 <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> Možnost je možné kombinovat pouze s <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnosti. Výsledkem použití jakékoli jiné možnosti regulární výraz <xref:System.ArgumentOutOfRangeException>.  
  
 Chování ECMAScript a kanonické regulární výrazy se liší do tří oblastí: znak syntaxe třídy, odkazující zaznamenávání skupin a osmičková versus zpětných odkazů.  
  
-   Syntaxe třídy znaků. Protože kanonický regulární výrazy podporují kódování Unicode, zatímco ECMAScript nemá, třídy znaků v ECMAScript mají omezenější syntaxi a některé prvky jazyka třída znak mít jiný význam. Například ECMAScript nepodporuje jazyk prvky, jako jsou například elementy kategorie nebo blok kódu Unicode `\p` a `\P`. Podobně `\w` element, který odpovídá znaku slova, je ekvivalentní `[a-zA-Z_0-9]` znak třída při použití ECMAScript a `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` při použití kanonické chování. Další informace najdete v tématu [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).  
  
     Následující příklad ukazuje rozdíl mezi kanonické a ECMAScript porovnávání vzorů. Definuje regulární výraz, `\b(\w+\s*)+`, který odpovídá slova, za nímž následuje prázdné znaky. Vstup se skládá z dva řetězce, ten, který používá sadu latinky znaků a druhý používá azbuce znaková sada. Jak ukazuje výstup, volání <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda, která používá odpovídající ECMAScript selže tak, aby odpovídaly azbuce slova, zatímco volání metody, které používá kanonické porovnávání neshoduje tato slova.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
     [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]  
  
-   Odkazující samy na sebe zaznamenávání skupiny. Třída zachycení regulárních výrazů s zpětný odkaz sám na sebe musí aktualizovat při každé iteraci zachycení. Jak ukazuje následující příklad, tato funkce umožňuje regulárnímu výrazu `((a+)(\1) ?)+` tak, aby odpovídaly vstupní řetězec "aa aaaa aaaaaa" při použití ECMAScript, ale ne v případě, že používá kanonické porovnávání.  
  
     [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
     [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]  
  
     Regulární výraz je definována, jak je znázorněno v následující tabulce.  
  
    |Vzor|Popis|  
    |-------------|-----------------|  
    |(+)|Porovnává písmenem "a" jeden nebo více krát. Toto je druhá zachytávající skupina.|  
    |(\1)|Porovná podřetězec zachycenou první zaznamenávání skupinu. Toto je třetí zachytávající skupina.|  
    |?|Odpovídat nula nebo jeden znak mezery.|  
    |((a+)(\1)?) +|Shoda vzoru jeden nebo více znaků "a následuje řetězec, který odpovídá skupině první zaznamenávání" následuje žádnou nebo jednu místo znaků jeden či více krát. Toto je první zachytávající skupina.|  
  
-   Řešení nejednoznačnosti mezi osmičková řídicí sekvence a zpětné odkazy. Následující tabulka shrnuje rozdíly v osmičková versus interpretace zpětných odkazů pomocí kanonické a ECMAScript regulární výrazy.  
  
    |Regulární výraz|Kanonické chování|Chování ECMAScript|  
    |------------------------|------------------------|-------------------------|  
    |`\0` Následuje osmičková číslice 0 až 2|Interpretujte jako osmičkové. Například `\044` vždy interpretována jako osmičkovou hodnotu a znamená "$".|Stejné chování.|  
    |`\` následuje číslice od 1 do 9, za nímž následuje bez dalších desítkových číslic,|Interpretujte jako zpětný odkaz. Například `\9` vždy znamená zpětných odkazů 9, i když devátá zachycující skupina neexistuje. Pokud zaznamenávání skupina neexistuje, vyvolá analyzátor regulárních výrazů <xref:System.ArgumentException>.|Pokud jednu číslici desítkové soustavy zaznamenávání skupina existuje, zpětných odkazů na tuto číslici. Hodnota, jinak hodnota interpretujte jako literál.|  
    |`\` následuje číslice od 1 do 9, za nímž následuje další desetinných míst|Číslice interpretujte jako desítkovou hodnotu. Pokud existuje zachycující skupina interpretujte výraz jako zpětný odkaz.<br /><br /> V opačném interpretovat počáteční osmičkové číslice hodnoty 377. To znamená vezměte v úvahu jenom nízkou 8 bitů hodnotu. Zbývající číslice interpretujte jako literály. Například ve výrazu `\3000`, pokud zachycující skupina 300 existuje, interpretovat jako zpětných odkazů 300; pokud zachycující skupina 300 neexistuje, interpretovat jako osmičková 300, za nímž následuje 0.|Interpretujte jako zpětný odkaz převedením tolik číslic nejdříve desetinnou hodnotu, která se může vztahovat k zachycení. Pokud žádné číslic lze převést, interpretujte jako osmičkové pomocí úvodní osmičková číslice hodnoty 377. Zbývající číslice interpretujte jako literály.|  
  
 [Zpět na začátek](#Top)  
  
<a name="Invariant"></a>   
## <a name="comparison-using-the-invariant-culture"></a>Porovnání s použitím neutrální jazykovou verzi  
 Ve výchozím nastavení když modul regulárních výrazů provádí porovnávání, použije konvencí aktuální jazykové verze pro určení ekvivalentních velká a malá písmena.  
  
 Toto chování je však nežádoucí u některých typů porovnávání, zejména při porovnání vstupu uživatele na názvy systémové prostředky, jako jsou hesla, soubory nebo adresy URL. Následující příklad ukazuje, jako je například scénář. Kód je určen k blokování přístupu k jakémukoli prostředku, jehož adresa URL začíná **FILE://**. Regulární výraz zkusí porovnávání s řetězcem pomocí regulárního výrazu `$FILE://`. Ale pokud aktuální systémovou kulturu tr-TR (turečtina-Turecko), "I" není velkým ekvivalentem "i". V důsledku volání <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metoda vrátí `false`, a je povolen přístup k souboru.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
 [!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]  
  
> [!NOTE]
>  Další informace o porovnávání řetězců, které jsou velká a malá písmena a které používají neutrální jazykovou verzi najdete v tématu [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md).  
  
 Namísto použití porovnávání aktuální jazykové verze, můžete zadat <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> možnost Ignorovat rozdíly v jazyce a používat pravidla neutrální jazykovou verzi.  
  
> [!NOTE]
>  Porovnání s využitím neutrální jazykové verze je k dispozici pouze zadáním <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> hodnotu `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statickou metodu porovnávání. Není k dispozici možnost vložené.  
  
 Následující příklad je stejný jako předchozí příklad, vyjma toho, že statické <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda je volána s možnostmi, které zahrnují <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. I v případě, že je aktuální jazykovou verzi nastavené na turečtina (Turecko), je možné úspěšně shodovat s "Soubor" a "soubor" a blokovat přístup k souboru prostředků modul regulárních výrazů.  
  
 [!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
 [!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]  
  
## <a name="see-also"></a>Viz také  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
