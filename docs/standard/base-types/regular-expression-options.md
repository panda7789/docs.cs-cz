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
ms.openlocfilehash: a53d7517485d2a0b02b6f11928f478a7da3f9503
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73972105"
---
# <a name="regular-expression-options"></a>Možnosti regulárních výrazů

Ve výchozím nastavení je porovnání vstupního řetězce s libovolnými literálovými znaky ve vzorku regulárního výrazu rozlišováno malá a velká písmena, prázdné místo ve vzoru regulárního výrazu je interpretováno jako literálové prázdné znaky a zachycující skupiny v regulárním výrazu jsou pojmenovány implicitně i explicitně. Tyto a několik dalších aspektů výchozího chování regulárních výrazů můžete upravit zadáním možností regulárních výrazů. Tyto možnosti, které jsou uvedeny v následující tabulce, mohou být zahrnuty do řádku <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> jako součást vzoru regulárního <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> výrazu, nebo mohou být dodány do konstruktoru třídy nebo statické metody porovnávání vzorů jako hodnotu výčtu.

|Člen RegexOptions|Vsazený znak|Účinek|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Není k dispozici.|Použijte výchozí chování. Další informace naleznete [v tématu Výchozí možnosti](#default-options).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Použije porovnávání, které nerozlišuje velká a malá písmena. Další informace naleznete v tématu [Porovnávání nerozlišujícímalá písmena](#case-insensitive-matching).|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Použijte víceřádkový `^` `$` režim, kde a odpovídají začátku a konci každého řádku (namísto začátku a konce vstupního řetězce). Další informace naleznete [v tématu Multiline Mode](#multiline-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Použijte jednořádkový režim, kde tečka (.) odpovídá `\n`každému znaku (namísto každého znaku kromě ). Další informace naleznete [v tématu Jednořádkový režim](#single-line-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Nezachytí nepojmenované skupiny. Jediná platná zachycení jsou explicitně pojmenované nebo `(?<`číslované skupiny *podvýrazu*`)` *názvu* `>` formuláře . Další informace naleznete [v tématu Explicit Captures Only](#explicit-captures-only).|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Není k dispozici.|Zkompilujte regulární výraz do sestavení. Další informace naleznete v [tématu Kompilované regulární výrazy](#compiled-regular-expressions).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Vylučte ze vzorku prázdné místo bez možnosti`#`a povolte komentáře za znakem čísla ( ). Další informace naleznete v tématu [Ignorování prázdného místa](#ignore-white-space).|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Není k dispozici.|Změňte směr hledání. Hledání se přesune zprava doleva místo zleva doprava. Další informace naleznete v [tématu Režim zprava doleva](#right-to-left-mode).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Není k dispozici.|Povolte chování odpovídající ecmascriptu pro výraz. Další informace naleznete v tématu [ECMAScript Matching Behavior](#ecmascript-matching-behavior).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Není k dispozici.|Ignorovat kulturní rozdíly v jazyce. Další informace naleznete [v tématu Porovnání pomocí invariantní jazykové verze](#comparison-using-the-invariant-culture).|

## <a name="specifying-the-options"></a>Určení možností

Možnosti regulárních výrazů můžete určit jedním ze tří způsobů:

- V `options` parametru <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktoru třídy`Shared` nebo statické ( v jazyce <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>Visual Basic) metoda porovnávání vzorů, například nebo . Parametr `options` je bitová nebo <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> kombinace výčtových hodnot.

  Když jsou možnosti <xref:System.Text.RegularExpressions.Regex> dodávány `options` do instance pomocí parametru konstruktoru <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> třídy, jsou vlastnosti přiřazeny možnosti. <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> Vlastnost však neodráží možnosti vřádků v samotném vzoru regulárního výrazu.

  V následujícím příkladu je uvedena ukázka. Používá `options` parametr <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody povolit porovnávání bez rozlišování velkých a malých písmen a ignorovat prázdné znaky vzoru při identifikaci slov začínajících písmenem "d".

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Aplikováním vložkových voleb ve `(?imnsx-imnsx)`vzoru regulárního výrazu se syntaxí . Volba se vztahuje na vzorek z bodu, kdy je volba definována buď na konec pole, nebo do bodu, ve kterém je volba nedefinovaná jinou voboucí volbou. Všimněte <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> si, <xref:System.Text.RegularExpressions.Regex> že vlastnost instance neodráží tyto vsazené možnosti. Další informace naleznete v tématu [Různé konstrukce.](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md)

  V následujícím příkladu je uvedena ukázka. Používá včleněné možnosti povolit porovnávání bez rozlišování velkých a malých písmen a ignorovat prázdné znaky vzorku při identifikaci slov, která začínají písmenem "d".

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Použitím vložkových voleb v určité konstrukci seskupení `(?imnsx-imnsx:`ve vzoru regulárního výrazu se *podvýrazem*`)`syntaxe . Žádné znamení před sadou možností zapne sadu; znaménko mínus, než sada možností vypne nastavení. (`?` je pevná část syntaxe konstrukce jazyka, která je vyžadována bez ohledu na to, zda jsou možnosti povoleny nebo zakázány.) Tato možnost platí pouze pro tuto skupinu. Další informace naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

  V následujícím příkladu je uvedena ukázka. Používá včleněné možnosti v konstrukci seskupení k povolení porovnávání bez rozlišování velkých a malých písmen a k ignorování prázdného místa vzorku při identifikaci slov začínajících písmenem "d".

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Pokud jsou volby zadány v`-`řádku, znaménko mínus ( ) před možností nebo sadou možností tyto možnosti vypne. Například vřaditkonstrukce `(?ix-ms)` zapne <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> možnosti a <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> vypne možnosti a. Všechny možnosti regulárních výrazů jsou ve výchozím nastavení vypnuty.

> [!NOTE]
> Pokud jsou možnosti regulárního výrazu zadané v parametru `options` konstruktoru nebo volání metody v konfliktu s možnostmi určenými v řádku ve vzoru regulárního výrazu, použijí se vřadné možnosti.

Následujících pět možností regulárního výrazu lze nastavit jak pomocí parametru options, tak vtextu:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Pomocí parametru lze nastavit následujících `options` pět možností regulárních výrazů, ale nelze je nastavit jako vřádík:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Určení možností

Můžete určit, které možnosti <xref:System.Text.RegularExpressions.Regex> byly poskytnuty objektu, když byl vytvořena instance načtením hodnoty vlastnosti jen <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> pro čtení. Tato vlastnost je zvláště užitečná pro určení možností, které jsou <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> definovány pro zkompilovaný regulární výraz vytvořený metodou.

Chcete-li otestovat přítomnost <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>jakékoli možnosti s výjimkou , <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> proveďte <xref:System.Text.RegularExpressions.RegexOptions> operaci AND s hodnotou vlastnosti a hodnotou, o kterou máte zájem. Potom otestujte, zda <xref:System.Text.RegularExpressions.RegexOptions> se výsledek rovná této hodnotě. Následující příklad testuje, <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> zda byla nastavena možnost.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Chcete-li <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>otestovat , určete, zda je hodnota vlastnosti <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> rovna <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, jak ukazuje následující příklad.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

V následujících částech jsou uvedeny možnosti podporované regulárním výrazem v rozhraní .NET.

## <a name="default-options"></a>Výchozí možnosti

Tato <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> možnost označuje, že nebyly zadány žádné možnosti a modul regulárních výrazů používá své výchozí chování. Ta zahrnují následující:

- Vzor je interpretován jako kanonický, nikoli jako regulární výraz ECMAScript.

- Vzor regulárního výrazu je spárován ve vstupním řetězci zleva doprava.

- Porovnání rozlišují malá a velká písmena.

- `^` Prvky `$` jazyka a odpovídají začátku a konci vstupního řetězce.

- Prvek `.` jazyka odpovídá každému `\n`znaku kromě .

- Jakékoli prázdné místo ve vzoru regulárního výrazu je interpretováno jako znak mezery literálu.

- Konvence aktuální jazykové verze se používají při porovnávání vzoru se vstupním řetězcem.

- Zachytávání skupin ve vzoru regulárního výrazu je implicitní i explicitní.

> [!NOTE]
> Možnost <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> nemá žádný vsazený ekvivalent. Pokud jsou možnosti regulárního výrazu použity v řadě, výchozí chování se obnoví na základě možností podle možností vypnutím určité možnosti. Například `(?i)` zapne porovnání bez rozlišování velkých a malých písmen a `(?-i)` obnoví výchozí porovnání rozlišující malá a velká písmena.

Vzhledem <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> k tomu, že možnost představuje výchozí chování modulu regulárních výrazů, je zřídka explicitně zadána ve volání metody. Místo toho je volána metoda `options` shody konstruktoru nebo statického vzoru bez parametru.

## <a name="case-insensitive-matching"></a>Porovnávání bez pouzdřící písmena

Možnost <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> nebo včleněná `i` možnost poskytuje porovnávání bez rozlišování velkých a malých písmen. Ve výchozím nastavení se používají konvence písmen aktuální jazykové verze.

Následující příklad definuje vzor regulárního výrazu , `\bthe\w*\b`který odpovídá všem slovům začínajícím na "the". Vzhledem k tomu, že první volání <xref:System.Text.RegularExpressions.Regex.Match%2A> metody používá výchozí porovnání rozlišující malá a velká písmena, výstup označuje, že řetězec "The", který začíná větu není spárován. Je spárována, <xref:System.Text.RegularExpressions.Regex.Match%2A> když je metoda volána s možnostmi nastavenými na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

Následující příklad upravuje vzor regulárního výrazu z předchozího příkladu `options` tak, aby místo parametru používal včleněné možnosti, aby bylo porovnáno s rozlišování velkých a malých písmen. První vzorek definuje možnost bez rozlišování velkých a malých písmen ve sestavě konstrukce, která se vztahuje pouze na písmeno "t" v řetězci "the". Vzhledem k tomu, že konstrukce option se vyskytuje na začátku vzoru, druhý vzorek použije volbu bez rozlišování velkých a malých písmen na celý regulární výraz.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

## <a name="multiline-mode"></a>Víceřádkový režim

Možnost <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> nebo `m` možnost vložené umožňuje modulu regulárních výrazů zpracovat vstupní řetězec, který se skládá z více řádků. Změní interpretaci `^` a `$` jazykové prvky tak, aby odpovídaly začátku a konci řádku, namísto začátku a konce vstupního řetězce.

Ve výchozím `$` nastavení odpovídá pouze konec vstupního řetězce. Pokud zadáte <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost, bude se shodovat buď se znakem nového řádku (`\n`) nebo koncem vstupního řetězce. Neodpovídá však kombinaci znaků návrat/řádek posuvu vozíku. Chcete-li je úspěšně porovnat, `\r?$` použijte `$`podvýraz namísto pouze .

Následující příklad extrahuje jména nadhazovačů a skóre <xref:System.Collections.Generic.SortedList%602> a přidá je do kolekce, která je seřadí v sestupném pořadí. Metoda <xref:System.Text.RegularExpressions.Regex.Matches%2A> se nazývá dvakrát. Při volání první metody je `^(\w+)\s(\d+)$` regulární výraz a nejsou nastaveny žádné možnosti. Jak ukazuje výstup, protože modul regulárních výrazů nemůže odpovídat vstupnímu vzoru spolu s začátkem a koncem vstupního řetězce, nejsou nalezeny žádné shody. Při volání druhé metody se regulární výraz změní `^(\w+)\s(\d+)\r?$` <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>na a možnosti jsou nastaveny na . Jak ukazuje výstup, názvy a skóre jsou úspěšně spárovány a skóre jsou zobrazeny v sestupném pořadí.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

Vzor regulárního výrazu `^(\w+)\s(\d+)\r*$` je definován tak, jak je znázorněno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`^`|Začněte na začátku řádku.|
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|
|`\s`|Porovná prázdný znak.|
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je druhá zachytávající skupina.|
|`\r?`|Porovná nulový nebo jeden znak konce řádku.|
|`$`|Konec na konci řádku.|

Následující příklad je ekvivalentní předchozímu, s tím rozdílem, že k nastavení možnosti víceřádkové používá možnost `(?m)` vsazení.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

## <a name="single-line-mode"></a>Jednořádkový režim

Možnost <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> nebo `s` možnost vložené způsobí, že modul regulárních výrazů zachází se vstupním řetězcem, jako by se skládal z jednoho řádku. Provádí to změnou chování elementu`.`jazyka tečka ( ) tak, aby odpovídala každý znak, namísto odpovídající každý znak s výjimkou znak `\n` u nového řádku nebo \u000A.

Následující příklad ukazuje, jak se `.` při použití této <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnosti změní chování prvku jazyka. Regulární `^.+` výraz začíná na začátku řetězce a odpovídá každému znaku. Ve výchozím nastavení končí shoda na konci prvního řádku. vzor regulárního výrazu `\r` odpovídá znaku návratu řádku nebo \u000D, ale neodpovídá `\n`. Protože <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnost interpretuje celý vstupní řetězec jako jeden řádek, odpovídá každému `\n`znaku ve vstupním řetězci, včetně .

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Následující příklad je ekvivalentní předchozímu, s tím rozdílem, že používá možnost `(?s)` inline k povolení jednořádkového režimu.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

## <a name="explicit-captures-only"></a>Pouze explicitní zachycení

Ve výchozím nastavení jsou zachytávající skupiny definovány použitím závorek ve vzoru regulárního výrazu. Pojmenovaným skupinám je přiřazen `(?<`název nebo číslo podle možnosti jazyka*podvýraz* `)` *u názvu,*`>`zatímco nepojmenované skupiny jsou přístupné podle indexu. V <xref:System.Text.RegularExpressions.GroupCollection> objektu nepojmenované skupiny předcházejí pojmenované skupiny.

Seskupování konstrukce se často používají pouze k použití kvantifikátory pro více prvků jazyka a zachycené podřetězce nejsou žádné zajímavé. Například pokud následující regulární výraz:

`\b\(?((\w+),?\s?)+[\.!?]\)?`

je určena pouze k extrakci vět, které končí tečkou, vykřičníkem nebo otazníkem <xref:System.Text.RegularExpressions.Match> z dokumentu, je zajímavá pouze výsledná věta (která je zastoupena objektem). Jednotlivá slova v kolekci nejsou.

Zachytávání skupin, které nejsou následně použity, může být <xref:System.Text.RegularExpressions.GroupCollection> nákladné, protože modul regulárních výrazů musí naplnit objekty i <xref:System.Text.RegularExpressions.CaptureCollection> kolekce. Jako alternativu můžete použít <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> možnost nebo `n` možnost vložku k určení, že pouze platné zachycení jsou `(?<`explicitně pojmenované nebo číslované skupiny, které jsou označeny konstrukcí`)` *podvýrazu.* `>` *subexpression*

Následující příklad zobrazuje informace o shodách vrácených vzorem `\b\(?((\w+),?\s?)+[\.!?]\)?` regulárního výrazu, <xref:System.Text.RegularExpressions.Regex.Match%2A> když je metoda volána s <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> možností a bez ní. Jak ukazuje výstup z prvního volání metody, modul <xref:System.Text.RegularExpressions.GroupCollection> regulárních výrazů plně naplní objekty a <xref:System.Text.RegularExpressions.CaptureCollection> kolekce informacemi o zachycených podřetězecch. Vzhledem k tomu, `options` že <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>druhá metoda je volána s nastavenou na , nezachycuje informace o skupinách.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

Vzor regulárního výrazu`\b\(?((?>\w+),?\s?)+[\.!?]\)?` je definován tak, jak je znázorněno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`\b`|Začněte na hranici slova.|
|`\(?`|Porovná nula nebo jeden výskyt počáteční závorky ("().|
|`(?>\w+),?`|Porovná jeden nebo více znaků slova následovanýnulou nebo jednou čárkou. Nepoužívejte zpětný návrat při porovnávání znaků slova.|
|`\s?`|Porovná žádný nebo jeden prázdný znak.|
|`((\w+),?\s?)+`|Porovná kombinaci jednoho nebo více znaků slova, nuly nebo jednoho čárka a nulových nebo jedněch nemezerových znaků jednou nebo vícekrát.|
|`[\.!?]\)?`|Porovná libovolný ze tří interpunkčních symbolů následovaných nulou nebo jednou uzavíracími závorky (")").|

Můžete také použít `(?n)` vřadný prvek k potlačení automatického sběru. Následující příklad upraví předchozí vzor regulárního `(?n)` výrazu tak, <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> aby místo možnosti používal vřavový prvek.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Nakonec můžete použít element `(?n:)` včleněné skupiny k potlačení automatického zachycení na základě skupiny po skupině. Následující příklad upraví předchozí vzorek tak, aby potlačil nepojmenované `((?>\w+),?\s?)`zachycení ve vnější skupině . Všimněte si, že to potlačí nepojmenované zachycení ve vnitřní skupině také.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

## <a name="compiled-regular-expressions"></a>Zkompilované regulární výrazy

Ve výchozím nastavení jsou regulární výrazy v rozhraní .NET interpretovány. Při <xref:System.Text.RegularExpressions.Regex> vytvoření instance objektu nebo <xref:System.Text.RegularExpressions.Regex> je volána statická metoda, vzor regulárního výrazu je analyzován do sady vlastních opcodes a interpret používá tyto kódy opcodes ke spuštění regulárního výrazu. To zahrnuje kompromis: Náklady na inicializaci modulu regulárních výrazů jsou minimalizovány na úkor výkonu za běhu.

Pomocí této možnosti můžete použít kompilované <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> místo interpretovaných regulárních výrazů. V tomto případě při vzor je předán modulregulárních výrazů, je analyzován na sadu opcodes a pak převedeny na zprostředkující jazyk Microsoft (MSIL), který lze předat přímo do modulu CLR jazyka runtime. Zkompilované regulární výrazy maximalizují výkon za běhu na úkor času inicializace.

> [!NOTE]
> Regulární výraz lze zkompilovat <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> pouze `options` zadáním <xref:System.Text.RegularExpressions.Regex> hodnoty parametru konstruktoru třídy nebo statické metody porovnávání vzorů. Není k dispozici jako možnost vsazení.

Kompilované regulární výrazy můžete použít při volání statických i instancí regulárních výrazů. Ve statických regulárních <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> výrazech `options` je tato možnost předána parametru metody porovnávání vzorů regulárního výrazu. V případě, že regulární `options` výrazy <xref:System.Text.RegularExpressions.Regex> je předán parametr konstruktoru třídy. V obou případech má za následek vyšší výkon.

K tomuto zlepšení výkonu však dochází pouze za následujících podmínek:

- Objekt, <xref:System.Text.RegularExpressions.Regex> který představuje určitý regulární výraz, se používá ve více voláních metod porovnávání vzorů regulárních výrazů.

- Objekt <xref:System.Text.RegularExpressions.Regex> není povoleno přejít mimo rozsah, takže jej lze znovu použít.

- Statický regulární výraz se používá ve více voláních metod porovnávání vzorů regulárních výrazů. (Zlepšení výkonu je možné, protože regulární výrazy používané v volání statické metody jsou ukládány do mezipaměti modulu regulárních výrazů.)

> [!NOTE]
> Tato <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost nesouvisí <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> s metodou, která vytvoří speciální sestavení, které obsahuje předdefinované kompilované regulární výrazy.

## <a name="ignore-white-space"></a>Ignorovat prázdné místo

Ve výchozím nastavení je významné prázdné místo ve vzorku regulárního výrazu. vynutí, aby modul regulárních výrazů odpovídal prázdnému znaku ve vstupním řetězci. Z tohoto důvodu jsou`\b\w+\s`regulární`\b\w+` výrazy " " a " přibližně ekvivalentní regulární výrazy. Kromě toho při znak čísla (#) je zjištěna ve vzoru regulárního výrazu, je interpretován jako literál znak, který má být spárován.

Tato <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> možnost nebo `x` vsazená možnost změní toto výchozí chování následujícím způsobem:

- Neuvozené prázdné místo ve vzoru regulárního výrazu je ignorováno. Chcete-li být součástí vzoru regulárního výrazu, musí `\s` být`\` prázdné znaky uvozeny (například jako nebo " ").

- Znak čísla (#) je interpretován jako začátek komentáře, nikoli jako literál. Veškerý text ve vzoru regulárního výrazu od znaku # až po konec řetězce je interpretován jako komentář.

V následujících případech však prázdné znaky v regulárním výrazu nejsou <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> ignorovány, a to ani v případě, že použijete tuto možnost:

- Prázdné místo v rámci třídy znaků je vždy interpretováno doslovně. Například vzor regulárního výrazu `[ .,;:]` odpovídá libovolnému znaku prázdného místa, období, čárce, středníku nebo dvojtečkě.

- Prázdné místo není povoleno v závorkách kvantifikátoru, `{`například *n*`}`, `{` *n*`,}`a `{` *n*`,`*m*`}`. Například vzor `\d{1, 3}` regulárního výrazu neodpovídá všem sekvencí číslic od jedné do tří číslic, protože obsahuje nevýrazný znak.

- Prázdné znaky není povoleno v rámci sekvence znaků, který zavádí prvek jazyka. Například:

  - `(?:` *Podvýraz* `)` elementu jazyka představuje skupinu bez `(?:` zachycení a část prvku nemůže mít vložené mezery. `(? :` *Podvýraz* `)` vzoru vyvolá <xref:System.ArgumentException> čas za běhu, protože modul regulárních výrazů `( ?:`nemůže analyzovat vzorek a *dílčí výraz* `)` vzoru se neshoduje s *dílčím výrazem*.

  - `\p{` *name*Název`}`elementu jazyka , který představuje kategorii Unicode nebo pojmenovaný blok, `\p{` nemůže obsahovat vložené mezery v části prvku. Pokud zahrnete prázdné místo, prvek <xref:System.ArgumentException> vyvolá za běhu.

Povolení této možnosti pomáhá zjednodušit regulární výrazy, které je často obtížné analyzovat a pochopit. Zlepšuje čitelnost a umožňuje dokumentovat regulární výraz.

Následující příklad definuje následující vzor regulárního výrazu:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Tento vzorek je podobný vzoru definovanému v části [Explicit Captures Only](#explicit-captures-only) s tím rozdílem, že používá <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> možnost ignorovat prázdné místo vzorku.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

Následující příklad používá možnost `(?x)` vsazení k ignorování prázdného místa vzorku.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

## <a name="right-to-left-mode"></a>Režim zprava doleva

Ve výchozím nastavení modul regulárních výrazů vyhledává zleva doprava. Směr hledání můžete obrátit pomocí <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> možnosti. Hledání automaticky začíná na pozici posledního znaku řetězce. Pro metody porovnávání vzorů, které obsahují <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>parametr počáteční pozice, například , počáteční pozice je index pozice znaku nejvíce vpravo, ve kterém má hledání začít.

> [!NOTE]
> Režim vzoru se vzorkem se vzorkem <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> se vzorkem se vzorkem zprava doleva je k dispozici pouze zadáním hodnoty parametru `options` konstruktoru <xref:System.Text.RegularExpressions.Regex> třídy nebo statické metody porovnávání vzorů. Není k dispozici jako možnost vsazení.

Tato <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> možnost změní pouze směr hledání; neinterpretuje vzor regulárního výrazu zprava doleva. Například regulární `\bb\w+\s` výraz odpovídá slovům začínajícím písmenem "b" a následuje znak prázdného místa. V následujícím příkladu se vstupní řetězec skládá ze tří slov, která obsahují jeden nebo více znaků "b". První slovo začíná písmenem "b", druhé končí písmenem "b" a třetí obsahuje dva znaky "b" uprostřed slova. Jak ukazuje výstup z příkladu, pouze první slovo odpovídá vzoru regulárního výrazu.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Všimněte si také, že `(?=`kontrolní výraz dopředného vyhledávání (prvek jazyka *podvýraz)* `)` a kontrolní výraz zpětného vyhledávání (prvek `(?<=`jazyka *podvýraz)* `)` nemění směr. Kontrolní výrazy dopředného vyhledávání se dívají doprava; výrazy zpětného vyhledávání vypadají vlevo. Regulární výraz `(?<=\d{1,2}\s)\w+,?\s\d{4}` například používá výraz zpětného vyhledávání k testování data, které předchází názvu měsíce. Regulární výraz pak odpovídá měsíci a roku. Informace o dopředných a vyhledávacích kontrolních výrazech naleznete v [tématu Seskupování konstrukcí](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Vzor regulárního výrazu je definován tak, jak je znázorněno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Začátek shody musí předcházet jedné nebo dvě desetinné číslice následované mezerou.|
|`\w+`|Porovná jeden nebo více znaků slova.|
|`,?`|Porovná nulové nebo jedno čárkové znaky.|
|`\s`|Porovná prázdný znak.|
|`\d{4}`|Porovná čtyři desetinné číslice.|

## <a name="ecmascript-matching-behavior"></a>Odpovídající chování ecmascriptu

Ve výchozím nastavení používá modul regulárních výrazů kanonické chování při porovnávání vzoru regulárního výrazu se vstupním textem. Můžete však dát pokyn modulu regulárních výrazů, <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> aby používal odpovídající chování ECMAScript zadáním volby.

> [!NOTE]
> Chování kompatibilní s ECMAScript je k <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> dispozici `options` pouze dodáním hodnoty parametru konstruktoru <xref:System.Text.RegularExpressions.Regex> třídy nebo statické metody porovnávání vzorů. Není k dispozici jako možnost vsazení.

Možnost <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> lze kombinovat pouze s <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnostmi a. Použití jakékoli jiné možnosti v regulárním výrazu <xref:System.ArgumentOutOfRangeException>má za následek .

Chování ecmascriptových a kanonických regulárních výrazů se liší ve třech oblastech: syntaxe třídy znaků, sebeodkazující zachytávající skupiny a osmičková versus zpětně odkazová interpretace.

- Syntaxe třídy znaků. Protože kanonické regulární výrazy podporují kódování Unicode, zatímco ECMAScript nikoli, třídy znaků v jazyce ECMAScript mají omezenější syntaxi a některé prvky jazyka znakové třídy mají jiný význam. Například ECMAScript nepodporuje prvky jazyka, jako je například kategorie Unicode nebo blokové prvky `\p` a `\P`. Podobně `\w` prvek, který odpovídá znaku slova, je `[a-zA-Z_0-9]` ekvivalentní třídě znaků při `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` použití ECMAScript a při použití kanonického chování. Další informace naleznete v [tématu Třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).

  Následující příklad ilustruje rozdíl mezi kanonickým a ECMAScript vzorem. Definuje regulární výraz `\b(\w+\s*)+`, který odpovídá slovům následovaným prázdné znaky. Vstup se skládá ze dvou řetězců, jeden, který používá znakovou sadu latinky a druhý, který používá znakovou sadu cyrilice. Jak ukazuje výstup, volání <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metody, která používá odpovídající ECMAScript, neodpovídá slovům cyrilice, zatímco volání metody, které používá kanonické porovnávání, odpovídá těmto slovům.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Sebeodkazující zachytávající skupiny. Třída sběru regulárních výrazů s zpětným odkazem na sebe sama musí být aktualizována s každou iterací sběru. Jak ukazuje následující příklad, tato funkce `((a+)(\1) ?)+` umožňuje, aby regulární výraz odpovídal vstupnímu řetězci " aa aaaaaa " při použití ecmascriptu, ale ne při použití kanonického párování.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  Regulární výraz je definován tak, jak je znázorněno v následující tabulce.

  |Vzor|Popis|
  |-------------|-----------------|
  |(a+)|Porovnejte písmeno "a" jednou nebo vícekrát. Toto je druhá zachytávající skupina.|
  |(\1)|Porovná podřetězec zachycený první zachytávající skupinou. Toto je třetí zachytávající skupina.|
  |?|Porovná znaky nuly nebo jedné mezery.|
  |((a+)(\1)?) +|Porovná vzorek jednoho nebo více znaků "a" následovaný řetězcem, který odpovídá první zachytávající skupině následované nulou nebo jedním znakem mezery jednou nebo vícekrát. Toto je první zachytávající skupina.|

- Rozlišení nejasností mezi osmičkovými úniky a zpětných odkazů. Následující tabulka shrnuje rozdíly v osmičkové interpretaci a zpětném odkazu pomocí kanonických regulárních výrazů a regulárních výrazů ECMAScript.

  |Regulární výraz|Kanonické chování|Chování ecmascriptu|
  |------------------------|------------------------|-------------------------|
  |`\0`následované 0 až 2 osmimístnými číslicemi|Interpretovat jako osmičkový. Například `\044` je vždy interpretován jako osmičková hodnota a znamená "$".|Stejné chování.|
  |`\`následované číslicí od 1 do 9 následovanou žádnými dalšími desetinnými číslicemi,|Interpretovat jako zpětný odkaz. Například `\9` vždy znamená zpětný odkaz 9, i když neexistuje devátá zachytávající skupina. Pokud zachytávající skupina neexistuje, analyzátor regulárních výrazů vyvolá . <xref:System.ArgumentException>|Pokud existuje jedna desetinná číslice zachycující skupina, zpětný odkaz na tuto číslici. V opačném případě interpretovat hodnotu jako literál.|
  |`\`následované číslicí od 1 do 9 následovanou dalšími desetinnými číslicemi|Interpretovat číslice jako desítkovou hodnotu. Pokud tato zachytávající skupina existuje, interpretovat výraz jako zpětný odkaz.<br /><br /> V opačném případě interpretovat úvodní osmičkové číslice až do osmičky 377; to znamená, zvažte pouze nízké 8 bitů hodnoty. Interpretovat zbývající číslice jako literály. Například ve výrazu `\3000`, pokud zachytávání skupina 300 existuje, interpretovat jako zpětný odkaz 300; Pokud zachytávající skupina 300 neexistuje, interpretujte jako osmičkový 300 následovaný 0.|Interpretovat jako zpětný odkaz převodem co nejvíce číslic na desítkovou hodnotu, která může odkazovat na zachycení. Pokud nelze převést žádné číslice, interpretujte jako osmičkové pomocí počátečních osmičkových číslic až do osmičkového 377; interpretovat zbývající číslice jako literály.|

## <a name="comparison-using-the-invariant-culture"></a>Porovnání pomocí invariantní jazykové verze

Ve výchozím nastavení, když modul regulárních výrazů provádí porovnání bez rozlišování velkých a malých písmen, používá konvence písmen aktuální jazykové verze k určení ekvivalentních velkých a malých písmen.

Toto chování je však nežádoucí pro některé typy porovnání, zejména při porovnávání uživatelský vstup na názvy systémových prostředků, jako jsou hesla, soubory nebo adresy URL. Následující příklad ilustruje například scénář. Kód je určen k zablokování přístupu k libovolnému prostředku, jehož adresa URL je předchází **FILE://**. Regulární výraz se pokusí o shodu s `$FILE://`řetězcem bez rozlišování velkých a malých písmen pomocí regulárního výrazu . Pokud je však současná jazyková verze systému tr-TR (Turecko-Turecko), "I" není velkými písmeny ekvivalentu "i". V důsledku toho volání <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> metody `false`vrátí a přístup k souboru je povolen.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Další informace o porovnávání řetězců, které rozlišují malá a velká písmena a které používají invariantní jazykovou verzi, naleznete v [tématu Doporučené postupy pro použití řetězců](../../../docs/standard/base-types/best-practices-strings.md).

Namísto použití porovnání bez rozlišování velkých a malých písmen aktuální jazykové verze, můžete zadat <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> možnost ignorovat kulturní rozdíly v jazyce a použít konvence invariantní jazykové verze.

> [!NOTE]
> Porovnání pomocí invariantní jazykové verze je <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> k `options` dispozici pouze <xref:System.Text.RegularExpressions.Regex> zadáním hodnoty parametru konstruktoru třídy nebo statické metody porovnávání vzorů. Není k dispozici jako možnost vsazení.

Následující příklad je shodný s předchozím příkladem <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> s tím rozdílem, že statická metoda je volána s možnostmi, které zahrnují <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. I v případě, že aktuální jazyková verze je nastavena na turečtina (Turecko), modul regulárních výrazů je schopen úspěšně odpovídat "SOUBOR" a "soubor" a blokovat přístup k prostředku souboru.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Viz také

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
