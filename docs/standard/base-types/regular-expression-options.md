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
ms.openlocfilehash: 5e77fac49db4a2faadb5785c4ef15e401f340d8b
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663974"
---
# <a name="regular-expression-options"></a>Možnosti regulárních výrazů

<a name="Top"></a> Ve výchozím nastavení porovnání vstupního řetězce s jakýmikoli literálními znaky ve vzorku regulárního výrazu je velká a malá písmena, prázdný znak ve vzorku regulárního výrazu je interpretován jako literální prázdné znaky a zachytávajících skupinách v regulárním výrazu jsou pojmenovány implicitně a také explicitně. Můžete změnit tyto a několik jiných aspektů výchozího chování regulárních výrazů zadáním možností regulárních výrazů. Tyto možnosti, které jsou uvedeny v následující tabulce, mohou být zahrnuty vložené jako součást vzorku regulárního výrazu nebo mohou být poskytnuty <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktoru třídy nebo statické metodě porovnávání vzorků jako <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> hodnota výčtu.

|Člen RegexOptions|Vložený znak|Efekt|
|-------------------------|----------------------|------------|
|<xref:System.Text.RegularExpressions.RegexOptions.None>|Není k dispozici|Použije výchozí chování. Další informace najdete v tématu [výchozí možnosti](#Default).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>|`i`|Použije porovnávání, které nerozlišuje velká a malá písmena. Další informace najdete v tématu [porovnávání](#Case).|
|<xref:System.Text.RegularExpressions.RegexOptions.Multiline>|`m`|Použije víceřádkový režim, ve kterém `^` a `$` odpovídají začátku a konci každého řádku (místo začátku a konci vstupního řetězce). Další informace najdete v tématu [víceřádkový režim](#Multiline).|
|<xref:System.Text.RegularExpressions.RegexOptions.Singleline>|`s`|Použití jednořádkový mód, kde tečka (.) odpovídá každému znaku (namísto každého znaku s výjimkou `\n`). Další informace najdete v tématu [jednořádkový režim](#Singleline).|
|<xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture>|`n`|Nezachytí nepojmenované skupiny. Pouze platná zachycení jsou explicitně pojmenované nebo číslované skupiny formuláře `(?<` *název* `>` *dílčí výraz*`)`. Další informace najdete v tématu [pouze explicitní zachycení](#Explicit).|
|<xref:System.Text.RegularExpressions.RegexOptions.Compiled>|Není k dispozici|Kompilaci regulárních výrazů do sestavení. Další informace najdete v tématu [zkompilované regulární výrazy](#Compiled).|
|<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace>|`x`|Prázdné znaky bez řídících vyloučit ze vzorku a povolí komentáře po číselném znaku (`#`). Další informace najdete v tématu [Ignorovat prázdné znaky](#Whitespace).|
|<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft>|Není k dispozici|Změňte směr hledání. Vyhledávání se přesunuje zprava doleva namísto zleva doprava. Další informace najdete v tématu [režim zprava doleva](#RightToLeft).|
|<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript>|Není k dispozici|Povolte chování standardu ECMAScript pro výraz. Další informace najdete v tématu [chování porovnávání ECMAScript](#ECMAScript).|
|<xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant>|Není k dispozici|Ignoruje kulturní rozdíly v jazyce. Další informace najdete v tématu [porovnávání pomocí neutrální jazykové verze](#Invariant).|

## <a name="specifying-the-options"></a>Určení možností

Můžete určit možnosti pro regulární výrazy jedním ze tří způsobů:

- V `options` parametr <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> konstruktoru třídy nebo statické (`Shared` v jazyce Visual Basic) metodu porovnávání vzorů, jako například <xref:System.Text.RegularExpressions.Regex.%23ctor%28System.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> nebo <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType>. `options` Parametr je bitová kombinace OR <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> hodnot výčtu.

  Pokud se poskytne možnosti <xref:System.Text.RegularExpressions.Regex> instance pomocí `options` parametr konstruktoru třídy možnosti jsou přiřazeny k <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> vlastnost. Ale <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> vlastnost neodráží vložené možnosti ve vzorku regulárního výrazu, samotného.

  V následujícím příkladu je uvedena ukázka. Používá `options` parametr <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metodu pro povolení porovnávání velkých a malých písmen a ignorování vzorků prázdných znaků při identifikaci slov začínajících na písmeno "d".

  [!code-csharp[Conceptual.Regex.Language.Options#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#6)]
  [!code-vb[Conceptual.Regex.Language.Options#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#6)]

- Použitím vložené možnosti ve vzorku regulárního výrazu se syntaxí `(?imnsx-imnsx)`. Možnost se vztahuje na vzorek od bodu, kdy je možnost definována do konce vzoru nebo do bodu, ve kterém je možnost zrušena definicí jiné vložené možnosti. Všimněte si, že <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType> vlastnost <xref:System.Text.RegularExpressions.Regex> instance nebere v úvahu tyto vložené možnosti. Další informace najdete v tématu [různé vytvoří](../../../docs/standard/base-types/miscellaneous-constructs-in-regular-expressions.md) tématu.

  V následujícím příkladu je uvedena ukázka. Použije vložené možnosti pro povolení porovnávání velkých a malých písmen a ignorování vzorků prázdných znaků při identifikaci slov začínajících na písmeno "d".

  [!code-csharp[Conceptual.Regex.Language.Options#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#7)]
  [!code-vb[Conceptual.Regex.Language.Options#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#7)]

- Použitím vložených možností v konkrétní skupině konstrukci ve vzorku regulárního výrazu se syntaxí `(?imnsx-imnsx:` *dílčí výraz*`)`. Žádné znaménko před sadou možností zapne sadu; znaménko minus před sadou možností sadu vypne. (`?` je pevnou součástí syntaxe konstrukce jazyka, která je požadována, zda jsou možnosti povoleny nebo zakázány.) Možnost se vztahuje pouze na tuto skupinu. Další informace najdete v tématu [Seskupovací konstrukce](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

  V následujícím příkladu je uvedena ukázka. Používá vložené možnosti v konstrukci seskupení pro povolení porovnávání velkých a malých písmen a ignorování vzorků prázdných znaků při identifikaci slov začínajících na písmeno "d".

  [!code-csharp[Conceptual.Regex.Language.Options#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/example1.cs#8)]
  [!code-vb[Conceptual.Regex.Language.Options#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/example1.vb#8)]

Pokud jsou možnosti zadány jako vložené, mínus (`-`) před možností nebo sadou možností vypne tyto možnosti. Například vložená konstrukce `(?ix-ms)` Zapne <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> a vypne možnosti <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnosti. Všechny možnosti regulárních výrazů jsou ve výchozím nastavení vypnuta.

> [!NOTE]
> Pokud možnosti regulárních výrazů zadané v `options` vložené zadán parametr konstruktoru nebo metody volání konfliktu s možnostmi ve vzorku regulárního výrazu, jsou použity vložené možnosti.

Následujících pět možností regulárních výrazů lze nastavit, jak s parametrem možnosti a vložené:

- <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType>

Následujících pět možností regulárních výrazů lze nastavit pomocí `options` parametr, ale nelze je nastavit pomocí vložených:

- <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>

- <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType>

## <a name="determining-the-options"></a>Určení možností

Můžete určit, které možnosti byly poskytnuty <xref:System.Text.RegularExpressions.Regex> objektu, když byla vytvořena jeho instance načtením hodnoty jen pro čtení <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> vlastnost. Tato vlastnost je zvláště užitečná pro určení možností, které jsou definovány pro kompilované regulární výrazy vytvořené metodou <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metody.

Chcete-li testovat přítomnost jakýchkoli možností kromě <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, proveďte operaci AND s hodnotou <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> vlastnost a <xref:System.Text.RegularExpressions.RegexOptions> hodnotu, která vás zajímá. Poté otestujte, zda se výsledek rovná <xref:System.Text.RegularExpressions.RegexOptions> hodnotu. Následující příklad testuje, jestli <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> byla nastavena možnost.

[!code-csharp[Conceptual.Regex.Language.Options#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#19)]
[!code-vb[Conceptual.Regex.Language.Options#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#19)]

Pro testování <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, určit, zda hodnota <xref:System.Text.RegularExpressions.Regex.Options%2A?displayProperty=nameWithType> vlastnost je rovna <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType>, jak ukazuje následující příklad.

[!code-csharp[Conceptual.Regex.Language.Options#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/determine1.cs#20)]
[!code-vb[Conceptual.Regex.Language.Options#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/determine1.vb#20)]

V následujících částech jsou uvedeny možnosti podporované regulárními výrazy v rozhraní .NET.

<a name="Default"></a>

## <a name="default-options"></a>Výchozí možnosti

<xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Možnost označuje, že nebyly zadány žádné možnosti a modul regulárních výrazů používá jeho výchozí chování. Ta zahrnují následující:

- Vzorek je interpretován jako kanonický spíše než regulární výraz ECMAScript.

- Vzor regulárního výrazu je porovnán vstupním řetězcem zleva doprava.

- Porovnávání rozlišuje malá a velká písmena.

- `^` a `$` prvky jazyka odpovídají začátku a konci vstupního řetězce.

- `.` Prvek jazyka odpovídá každému znaku s výjimkou `\n`.

- Jakýkoli prázdný znak ve vzorku regulárního výrazu je interpretován jako literální znak mezery.

- Konvence aktuální jazykové verze se používají při porovnávání vzoru se vstupním řetězcem.

- Zachycující skupiny ve vzorku regulárních výrazů jsou implicitní i explicitní.

> [!NOTE]
> <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> Možnost nemá žádný vložený ekvivalent. Když jsou možnosti regulárních výrazů uplatňovány jako vložené, je obnoveno výchozí chování na základě možnost po možnosti vypnutím určité možnosti. Například `(?i)` zapne porovnávání, a `(?-i)` obnoví výchozí porovnávání s malá a velká písmena.

Vzhledem k tomu, <xref:System.Text.RegularExpressions.RegexOptions.None?displayProperty=nameWithType> možnost představuje výchozí chování modulu regulárních výrazů, to je zřídka explicitně zadána ve volání metody. Konstruktor nebo statické metody porovnávání vzorků bez `options` parametr se nazývá místo.

[Zpět na začátek](#Top)

<a name="Case"></a>

## <a name="case-insensitive-matching"></a>Porovnávání

<xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase> Možnost, nebo `i` vloženou možnost poskytuje porovnávání. Ve výchozím nastavení se používají konvence velká a malá písmena aktuální jazykové verze.

Následující příklad definuje vzorek regulárního výrazu `\bthe\w*\b`, který odpovídá všem slovům začínajícím na "the". Protože první volání <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda používá výchozí porovnání velká a malá písmena, výstup označuje, že řetězec "The", který začíná věta, se neshoduje. Je nalezena shoda při <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda je volána s možnostmi nastavenými na <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase>.

[!code-csharp[Conceptual.Regex.Language.Options#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case1.cs#1)]
[!code-vb[Conceptual.Regex.Language.Options#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case1.vb#1)]

Následující příklad upravuje vzorek regulárního výrazu z předchozího příkladu pro použití vložených možností místo `options` parametr pro poskytnutí porovnávání. První vzorek definuje volbou rozlišování velikosti písmen v seskupující konstrukci, která se týká pouze písmene "t" v řetězci "the". Protože se konstrukce možnosti vyskytuje na začátku vzor, druhý vzorek použije možnost velkých a malých písmen na celý regulární výraz.

[!code-csharp[Conceptual.Regex.Language.Options#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/case2.cs#2)]
[!code-vb[Conceptual.Regex.Language.Options#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/case2.vb#2)]

[Zpět na začátek](#Top)

<a name="Multiline"></a>

## <a name="multiline-mode"></a>Víceřádkový režim

<xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> Možnost, nebo `m` vloženou možnost umožňuje modulu regulárních výrazů zpracovat vstupní řetězec, který se skládá z více řádků. Změní výklad `^` a `$` prvky jazyka, aby odpovídaly začátku a konci řádku namísto začátku a konci vstupního řetězce.

Ve výchozím nastavení `$` odpovídá pouze konci vstupního řetězce. Pokud zadáte <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnost, odpovídá buď znaku (`\n`) nebo na konci vstupního řetězce. Avšak neodpovídá kombinaci znaků návrat vozíku/nového řádku. Chcete-li úspěšně porovnávat, použijte dílčí výraz `\r?$` namísto pouze `$`.

Následující příklad extrahuje jména a skóre nadhazovačů a přidá je do <xref:System.Collections.Generic.SortedList%602> kolekce, která je seřadí v sestupném pořadí. <xref:System.Text.RegularExpressions.Regex.Matches%2A> Metoda je volána dvakrát. Při prvním volání metody regulární výraz je `^(\w+)\s(\d+)$` a nejsou nastaveny žádné možnosti. Jak ukazuje výstup, protože modul regulárních výrazů nemůže porovnat vstupní vzorek se začátkem a koncem vstupního řetězce, nejsou nalezeny žádné shody. Ve druhém volání metody regulárních výrazů se změní na `^(\w+)\s(\d+)\r?$` a možnosti jsou nastaveny na <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType>. Jak ukazuje výstup, jména a skóre jsou úspěšně porovnány a skóre jsou zobrazena v sestupném pořadí.

[!code-csharp[Conceptual.Regex.Language.Options#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline1.cs#3)]
[!code-vb[Conceptual.Regex.Language.Options#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline1.vb#3)]

Vzor regulárního výrazu `^(\w+)\s(\d+)\r*$` je definován, jak je znázorněno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`^`|Začít na začátku řádku.|
|`(\w+)`|Porovná jeden nebo více znaků slova. Toto je první zachytávající skupina.|
|`\s`|Porovná prázdný znak.|
|`(\d+)`|Porovná jednu nebo více desítkových číslic. Toto je druhá zachytávající skupina.|
|`\r?`|Porovná žádný nebo jeden návratový znak návrat na začátek řádku.|
|`$`|Skončí na konci řádku.|

Následující příklad je ekvivalentní předchozímu, s tím rozdílem, že používá vloženou možnost `(?m)` nastavení víceřádkové možnosti.

[!code-csharp[Conceptual.Regex.Language.Options#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/multiline2.cs#4)]
[!code-vb[Conceptual.Regex.Language.Options#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/multiline2.vb#4)]

[Zpět na začátek](#Top)

<a name="Singleline"></a>

## <a name="single-line-mode"></a>Jednořádkový režim

<xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> Možnost, nebo `s` vloženou možnost způsobí, že modul regulárních výrazů zachází se vstupním řetězcem, jako by se skládal z jednoho řádku. Dělá to tak, že změníte chování období (`.`) elementu jazyka tak, že odpovídá každému znaku, namísto všech znaků s výjimkou znaku nového řádku `\n` nebo \u000A.

Následující příklad ukazuje, jak chování `.` prvek jazyka změní při použití <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnost. Regulární výraz `^.+` začne na začátku řetězce a porovnává každý znak. Standardně je porovnávání ukončeno na konci prvního řádku. vzorek regulárního výrazu porovnává návratový znak, `\r` nebo \u000D, ale neodpovídá `\n`. Vzhledem k tomu, <xref:System.Text.RegularExpressions.RegexOptions.Singleline?displayProperty=nameWithType> možnost interpretuje celý vstupní řetězec jako jediný řádek, porovnává každý znak ve vstupním řetězci, včetně `\n`.

[!code-csharp[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.characterclasses/cs/any2.cs#5)]
[!code-vb[Conceptual.Regex.Language.CharacterClasses#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.characterclasses/vb/any2.vb#5)]

Následující příklad je ekvivalentní předchozímu, s tím rozdílem, že používá vloženou možnost `(?s)` umožňující jednořádkový režim.

[!code-csharp[Conceptual.Regex.Language.Options#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/singleline1.cs#5)]
[!code-vb[Conceptual.Regex.Language.Options#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/singleline1.vb#5)]

[Zpět na začátek](#Top)

<a name="Explicit"></a>

## <a name="explicit-captures-only"></a>Pouze explicitní zachycení

Ve výchozím nastavení jsou zachycující skupiny definovány pomocí závorek ve vzorku regulárního výrazu. Pojmenovaným skupinám jsou přiřazovány názvy nebo čísla podle `(?<` *název*`>`*dílčí výraz* `)` možnosti jazyka nepojmenované skupiny jsou přístupné pomocí indexů. V <xref:System.Text.RegularExpressions.GroupCollection> objektu nepojmenované skupiny předcházejí pojmenované skupiny.

Seskupovací konstrukce jsou často používány pouze k aplikaci kvantifikátorů pro násobení prvků jazyka a zachycené podřetězce nejsou podstatné. Například pokud následující regulární výraz:

```
\b\(?((\w+),?\s?)+[\.!?]\)?
```

je určen pouze k extrahování vět, které končí tečkou, vykřičníkem nebo otazníkem z dokumentu. pouze výsledná věta (která je reprezentována <xref:System.Text.RegularExpressions.Match> objekt) je relevantní. Jednotlivá slova v kolekci nejsou.

Zachycující skupiny, které se nepoužívají následně může být nákladné, protože modul regulárních výrazů musí naplnit obě <xref:System.Text.RegularExpressions.GroupCollection> a <xref:System.Text.RegularExpressions.CaptureCollection> objekty kolekce. Jako alternativu můžete použít buď <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> možnost nebo `n` vloženou možnost určit, že budou pouze platná zachycení jsou explicitně s názvem nebo číslované skupiny, které jsou určené `(?<` *název* `>` *dílčí výraz* `)` vytvořit.

Následující příklad zobrazí informace o shodách vrácené `\b\(?((\w+),?\s?)+[\.!?]\)?` vzorku regulárního výrazu, kdy <xref:System.Text.RegularExpressions.Regex.Match%2A> metoda je volána a nemusíte <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> možnost. Jak výstup z první metoda ukazuje volání, modul regulárních výrazů plně naplní <xref:System.Text.RegularExpressions.GroupCollection> a <xref:System.Text.RegularExpressions.CaptureCollection> kolekce objektů s informacemi o zachycených podřetězcích. Protože je druhá metoda volána s `options` nastavena na <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType>, nezachycuje informace o skupinách.

[!code-csharp[Conceptual.Regex.Language.Options#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit1.cs#9)]
[!code-vb[Conceptual.Regex.Language.Options#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit1.vb#9)]

Vzor regulárního výrazu`\b\(?((?>\w+),?\s?)+[\.!?]\)?` je definován, jak je znázorněno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`\b`|Začněte na hranici slova.|
|`\(?`|Porovná žádný nebo jeden výskytů levou závorku ("(").|
|`(?>\w+),?`|Porovná jeden nebo více znaků slova, následované žádnou nebo jednou tečkou. Nevracejte se při porovnávání znaků slova.|
|`\s?`|Porovná žádný nebo jeden prázdný znak.|
|`((\w+),?\s?)+`|Porovná kombinaci jednoho nebo více znaků slova, žádné nebo jedné čárky a nula nebo jedním prázdným znakem jednou nebo vícekrát.|
|`[\.!?]\)?`|Shodují s některým z tří interpunkčních znamének, následované žádnou nebo jednou pravou závorkou (")").|

Můžete také použít `(?n)` vloženého elementu k potlačení automatického zachycení. Následující příklad upravuje předchozí vzorek regulárního výrazu pro použití `(?n)` vloženého elementu namísto <xref:System.Text.RegularExpressions.RegexOptions.ExplicitCapture?displayProperty=nameWithType> možnost.

[!code-csharp[Conceptual.Regex.Language.Options#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit2.cs#10)]
[!code-vb[Conceptual.Regex.Language.Options#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit2.vb#10)]

Nakonec můžete použít vložený prvek skupiny `(?n:)` k potlačení automatického zachycení na základě skupin podle skupiny. Následující příklad upravuje předchozí vzorek potlačí nepojmenované zachycení ve skupině vnější `((?>\w+),?\s?)`. Všimněte si, že toto potlačí nepojmenované zachycení také ve vnitřních skupinách.

[!code-csharp[Conceptual.Regex.Language.Options#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/explicit3.cs#11)]
[!code-vb[Conceptual.Regex.Language.Options#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/explicit3.vb#11)]

[Zpět na začátek](#Top)

<a name="Compiled"></a>

## <a name="compiled-regular-expressions"></a>Kompilované regulární výrazy

Ve výchozím nastavení jsou interpretovány regulární výrazy v rozhraní .NET. Když <xref:System.Text.RegularExpressions.Regex> objekt je instance nebo statické <xref:System.Text.RegularExpressions.Regex> metoda je volána, vzorek regulárního výrazu je analyzován do sady vlastních operačních kódů a překladač používá tyto operační kódy ke spuštění regulárního výrazu. To zahrnuje kompromis: Náklady na inicializaci modulu regulárních výrazů je minimalizován za cenu výkonu za běhu.

Můžete použít namísto interpretovaných regulárních výrazů zkompilován s použitím <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost. V tomto případě když je vzorek předán modulu regulárních výrazů, to je analyzován na sadu operačních kódů a poté převeden na jazyk Microsoft intermediate language (MSIL), který může být přímo předán modulu common language runtime. Kompilované regulární výrazy maximalizují výkon na úkor doby inicializace.

> [!NOTE]
> Regulární výraz lze kompilovat pouze zadáním <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> hodnota, která se `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statické metody porovnávání vzorků. Není k dispozici jako vložená možnost.

Můžete použít kompilované regulární výrazy ve voláních statických i instančních regulárních výrazů. Ve statických regulárních výrazů <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> možnost je předána `options` parametr metody porovnávání se vzorem regulárního výrazu. V instančních regulárních výrazech je předána `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy. V obou případech je výsledkem lepší výkon.

K tomuto zlepšení výkonu však dochází pouze za následujících podmínek:

- A <xref:System.Text.RegularExpressions.Regex> objekt představující konkrétní regulární výraz se používá ve více voláních metod porovnávání vzorků regulárních výrazů.

- <xref:System.Text.RegularExpressions.Regex> Objektu není povoleno přejít mimo rozsah, takže je možné využít znovu.

- Statický regulární výraz se používá ve více voláních metod porovnávání vzorků regulárních výrazů. (Zlepšení výkonu je možné, protože regulární výrazy použité ve volání statické metody jsou ukládány do mezipaměti modulem regulárních výrazů.)

> [!NOTE]
> <xref:System.Text.RegularExpressions.RegexOptions.Compiled?displayProperty=nameWithType> Možnost je nezávislá na <xref:System.Text.RegularExpressions.Regex.CompileToAssembly%2A?displayProperty=nameWithType> metodu, která vytvoří sestavení se speciálním účelem obsahující předdefinované kompilované regulární výrazy.

[Zpět na začátek](#Top)

<a name="Whitespace"></a>

## <a name="ignore-white-space"></a>Ignorování prázdných znaků

Ve výchozím nastavení je důležité; prázdný znak ve vzorku regulárního výrazu nutí modul regulárních výrazů tak, aby odpovídaly prázdný znak ve vstupním řetězci. Z toho důvodu regulárního výrazu "`\b\w+\s`"a"`\b\w+` " zhruba ekvivalentní regulární výrazy. Kromě toho při křížku (#) se narazí ve vzorku regulárního výrazu, je interpretován jako literální znak pro porovnání.

<xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> Možnost, nebo `x` vloženou možnost, změní toto výchozí chování následujícím způsobem:

- Prázdný znak ve vzorku regulárního výrazu je ignorován. Jako součást vzorku regulárního výrazu, musí být uvozena prázdné znaky (například jako `\s` nebo "`\` ").

- Znak čísla (#) je interpretován jako začátek komentáře, nikoli jako literální znak. Veškerý text ve vzorku regulárního výrazu od znaku # na konec řetězce je interpretován jako komentář.

Ale v následujících případech prázdné znaky v regulárním výrazu nejsou ignorovány, i když používáte <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> možnost:

- Mezer v rámci třídy znaků je vždy interpretován literálně. Například vzor regulárního výrazu `[ .,;:]` odpovídá jakékoli jeden prázdný znak, období, čárka, středník nebo dvojtečka.

- Není povolen prázdný znak v závorkách kvantifikátor, jako například `{` *n*`}`, `{` *n*`,}`, a `{` *n* `,` *m*`}`. Například vzor regulárního výrazu `\d{1, 3}` selže při porovnávání nějaké sekvence číslic od jedné do tří číslic, protože obsahuje prázdný znak.

- V rámci sekvence znaků, která představuje prvek jazyka není povolen prázdný znak. Příklad:

  - Language element `(?:` *dílčí výraz* `)` představuje skupinu bez zachytávání a `(?:` část element nemůže mít vložené mezery. Vzor `(? :` *dílčí výraz* `)` vyvolá <xref:System.ArgumentException> běhu vzhledem k tomu, že modul regulárních výrazů nelze parsovat vzor a vzor `( ?:` *dílčí výraz*  `)` selže při porovnávání *dílčí výraz*.

  - Language element `\p{` *název*`}`, který představuje kategorie sady Unicode nebo pojmenovaného blok, nesmí obsahovat mezery v `\p{` část elementu. Pokud zahrnete prázdné znaky, vyvolá elementu <xref:System.ArgumentException> v době běhu.

Povolením této možnosti pomáhá zjednodušit regulární výrazy, které je často obtížné analyzovat a pochopit. Zlepšuje čitelnost a umožňuje dokumentovat regulární výrazy.

Následující příklad definuje následující vzorek regulárního výrazu:

`\b \(? ( (?>\w+) ,?\s? )+  [\.!?] \)? # Matches an entire sentence.`

Tento model je podobný vzorku definovanému v [pouze explicitní zachycení](#Explicit) tématu, s tím rozdílem, že používá <xref:System.Text.RegularExpressions.RegexOptions.IgnorePatternWhitespace?displayProperty=nameWithType> možnost ignorování vzorků prázdných znaků.

[!code-csharp[Conceptual.Regex.Language.Options#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace1.cs#12)]
[!code-vb[Conceptual.Regex.Language.Options#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace1.vb#12)]

Následující příklad používá vloženou možnost `(?x)` pro ignorování prázdných znaků.

[!code-csharp[Conceptual.Regex.Language.Options#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/whitespace2.cs#13)]
[!code-vb[Conceptual.Regex.Language.Options#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/whitespace2.vb#13)]

[Zpět na začátek](#Top)

<a name="RightToLeft"></a>

## <a name="right-to-left-mode"></a>Režim zprava doleva

Ve výchozím nastavení modul regulárních výrazů vyhledává zleva doprava. Můžete obrátit směr vyhledávání použitím <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> možnost. Vyhledávání automaticky začne na pozicí posledního znaku řetězce. U metod porovnávání vzorků, které zahrnují počáteční pozice parametru, například <xref:System.Text.RegularExpressions.Regex.Match%28System.String%2CSystem.Int32%29?displayProperty=nameWithType>, počáteční pozice je index pozice znaku zcela vpravo, na které má vyhledávání začít.

> [!NOTE]
> Režim vzorku zprava doleva je k dispozici pouze prostřednictvím zadání <xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> hodnota, která se `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statické metody porovnávání vzorků. Není k dispozici jako vložená možnost.

<xref:System.Text.RegularExpressions.RegexOptions.RightToLeft?displayProperty=nameWithType> Možnost změní pouze směr vyhledávání; nezpůsobí interpretování vzorku regulárního výrazu zprava doleva. Například regulární výraz `\bb\w+\s` odpovídá slovům, která začínají písmenem "b" a jsou následována prázdným znakem. V následujícím příkladu vstupní řetězec skládá ze tří slov, které zahrnují jeden nebo více znaků "b". První slovo začíná písmenem "b", druhé končí "b" a třetí obsahuje dva znaky "b" uprostřed slova. Jak ukazuje výstup z příkladu, pouze první slovo odpovídá vzorku regulárního výrazu.

[!code-csharp[Conceptual.Regex.Language.Options#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft1.cs#17)]
[!code-vb[Conceptual.Regex.Language.Options#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft1.vb#17)]

Všimněte si také, že kontrolní výraz dopředného vyhledávání ( `(?=` *dílčí výraz* `)` prvek jazyka) a kontrolní výraz zpětného vyhledávání ( `(?<=` *dílčí výraz* `)`prvek jazyka) nemění směr. Kontrolní výrazy dopředného vyhledávání hledají zprava; kontrolní výrazy zpětného vyhledávání hledají zleva. Například regulární výraz `(?<=\d{1,2}\s)\w+,?\s\d{4}` používá kontrolní výraz zpětného vyhledávání pro testování datum, které předchází název měsíce. Regulární výraz poté porovnává měsíc a rok. Informace o kontrolní výrazy dopředného a zpětného vyhledávání, najdete v části [Grouping Constructs](../../../docs/standard/base-types/grouping-constructs-in-regular-expressions.md).

[!code-csharp[Conceptual.Regex.Language.Options#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/righttoleft2.cs#18)]
[!code-vb[Conceptual.Regex.Language.Options#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/righttoleft2.vb#18)]

Vzor regulárního výrazu je definován, jak je znázorněno v následující tabulce.

|Vzor|Popis|
|-------------|-----------------|
|`(?<=\d{1,2}\s)`|Začátek porovnávání musí být předcházen jednou nebo dvěma desítkovými číslicemi mezeru.|
|`\w+`|Porovná jeden nebo více znaků slova.|
|`,?`|Porovná žádný nebo jeden znak čárky.|
|`\s`|Porovná prázdný znak.|
|`\d{4}`|Porovná čtyři desítková čísla.|

[Zpět na začátek](#Top)

<a name="ECMAScript"></a>

## <a name="ecmascript-matching-behavior"></a>Chování porovnávání ECMAScript

Ve výchozím nastavení modul regulárních výrazů používá kanonické chování při porovnávání vzorku regulárního výrazu se vstupním textem. Ale můžete dát pokyn, modul regulárních výrazů zadáním chování porovnávání ECMAScript používat <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> možnost.

> [!NOTE]
> Chování standardu ECMAScript je k dispozici pouze prostřednictvím zadání <xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> hodnota, která se `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statické metody porovnávání vzorků. Není k dispozici jako vložená možnost.

<xref:System.Text.RegularExpressions.RegexOptions.ECMAScript?displayProperty=nameWithType> Možnosti lze kombinovat jen s <xref:System.Text.RegularExpressions.RegexOptions.IgnoreCase?displayProperty=nameWithType> a <xref:System.Text.RegularExpressions.RegexOptions.Multiline?displayProperty=nameWithType> možnosti. Použití jiné možnosti v regulárním výrazu vede <xref:System.ArgumentOutOfRangeException>.

Chování ECMAScript a kanonické regulární výrazy se liší ve třech oblastech: znak syntaxe třídy, samoodkazující skupiny zachytávání a interpretace osmičková versus interpretace na zpětný odkaz.

- Syntaxe třídy znaků. Vzhledem k tomu, že kanonické regulární výrazy podporují Unicode, zatímco ECMAScript nepodporuje, třídy znaků v ECMAScript mají omezenější syntaxi a některé jazykové prvky třídy znaků mají různý význam. Například ECMAScript nepodporuje jazykové prvky, jako jsou například prvky kategorie nebo blok sady Unicode `\p` a `\P`. Podobně `\w` element, který odpovídá znaku slova, odpovídá `[a-zA-Z_0-9]` třídy znaků, při použití ECMAScript a `[\p{Ll}\p{Lu}\p{Lt}\p{Lo}\p{Nd}\p{Pc}\p{Lm}]` při použití kanonické chování. Další informace najdete v tématu [třídy znaků](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).

  Následující příklad ukazuje rozdíl mezi kanonickým a ECMAScript porovnáváním vzorů. Definuje regulární výraz `\b(\w+\s*)+`, který odpovídá slovům, následovaným prázdnými znaky. Vstupní řetězec se skládá ze dvou řetězců, jeden používá sadu znaků latinky a, druhý používá znakovou sadu cyrilice. Jak ukazuje výstup, volání <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metodu, která používá porovnávání ECMAScript selže při porovnávání slov cyrilice, že volání metody, které používá kanonické porovnávání neodpovídá tato slova.

  [!code-csharp[Conceptual.Regex.Language.Options#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript1.cs#16)]
  [!code-vb[Conceptual.Regex.Language.Options#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript1.vb#16)]

- Seskupí odkazující samy na zachycení. Třída zachycení regulárních výrazů se zpětným odkazem na sebe sama musí být aktualizována při každé iteraci zachycení. Jak ukazuje následující příklad, tato funkce umožňuje regulárnímu výrazu `((a+)(\1) ?)+` tak, aby odpovídaly vstupní řetězec "aa aaaa aaaaaa" při použití ECMAScript, ale ne v případě, že používá kanonické porovnávání.

  [!code-csharp[Conceptual.Regex.Language.Options#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/ecmascript2.cs#21)]
  [!code-vb[Conceptual.Regex.Language.Options#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/ecmascript2.vb#21)]

  Regulární výraz je definován, jak je znázorněno v následující tabulce.

  |Vzor|Popis|
  |-------------|-----------------|
  |(a+)|Porovná písmeno "a" jednou nebo vícekrát. Toto je druhá zachytávající skupina.|
  |(\1)|Porovná podřetězec zachycený první zachycující skupinou. Toto je třetí zachytávající skupina.|
  |?|Porovná žádný nebo jeden znak mezery.|
  |((a+)(\1) ?)+|Vzor jednoho nebo více znaků "a za nímž následuje řetězec, který se shoduje s první zachytávající skupina" následovaný mezerami žádnou nebo jednu shodu znakem jednou nebo vícekrát. Toto je první zachytávající skupina.|

- Rozlišení nejasností mezi osmičkovými řídícími znaky a zpětnými odkazy. Následující tabulka shrnuje rozdíly mezi interpretace osmičková versus interpretace na zpětný odkaz v kanonické a ECMAScript regulární výrazy.

  |Regulární výraz|Kanonické chování|Chování ECMAScript|
  |------------------------|------------------------|-------------------------|
  |`\0` následované 0 až 2 osmičkovými číslicemi|Interpretováno jako osmičkové. Například `\044` je vždy interpretováno jako osmičková hodnota a znamená "$".|Stejné chování.|
  |`\` následované číslicí od 1 do 9, nenásledované dalšími desítkovými číslicemi, | Interpretováno jako zpětný odkaz. Například `\9` vždy znamená zpětný odkaz na 9, i když devátá zachycující skupina neexistuje. Pokud zachycující skupina neexistuje, vyvolá analyzátor regulárních výrazů <xref:System.ArgumentException>.|Pokud je jednomístné číslo zachytávání skupina existuje, zpětný odkaz na tuto číslici. Jinak interpretujte hodnotu jako literál.|
  |`\` následované číslicí od 1 do 9, nenásledované dalšími desítkovými číslicemi | Interpretujte číslice jako desítkovou hodnotu. Pokud existuje zachycující skupina, interpretuje výraz jako zpětný odkaz.<br /><br /> Jinak interpretujte počáteční osmičkové číslice až do osmičkové hodnoty 377. To znamená vezměte v úvahu pouze na 8 bitech hodnoty. Interpretujte zbývající číslice jako literální. Například ve výrazu `\3000`, pokud existuje zachycující skupina 300 interpretována jako zpětný odkaz 300; pokud zachycující skupina 300 neexistuje, je interpretováno jako osmičková hodnota 300 následována 0.|Interpretováno jako zpětný odkaz převedením tolika číslic je možné, na desítkovou hodnotu, která může odkazovat zachycení. Pokud může být převedeny žádné číslice, interpretujte jako osmičkovou pomocí počáteční osmičkové číslice až do osmičkové hodnoty 377. Interpretujte zbývající číslice jako literální.|

[Zpět na začátek](#Top)

<a name="Invariant"></a>

## <a name="comparison-using-the-invariant-culture"></a>Porovnávání pomocí neutrální jazykové verze

Ve výchozím nastavení když modul regulárních výrazů provádí porovnávání bez rozlišování, používá konvence velká a malá písmena aktuální jazykové verze k určení ekvivalentních velká a malá písmena.

Toto chování je však nežádoucí u některých typů porovnávání, zejména při porovnání vstupu uživatele s názvy systémových prostředků, jako jsou hesla, soubory nebo adresy URL. Následující příklad ukazuje takovýto scénář. Kód je určen k blokování přístupu k jakémukoli prostředku, jehož adresa URL začíná **FILE://** . Regulární výraz zkusí porovnávání s řetězci pomocí regulárního výrazu `$FILE://`. Nicméně, pokud je aktuální jazyková verze systému tr-TR (turečtina – Turecko), "I" není velkým ekvivalentem znaku "i". Ve výsledku volání <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> vrátí metoda `false`, a je povolen přístup k souboru.

[!code-csharp[Conceptual.Regex.Language.Options#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#14)]
[!code-vb[Conceptual.Regex.Language.Options#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#14)]

> [!NOTE]
> Další informace o porovnávání řetězců, které jsou malá a velká písmena a používají invariantní jazykovou verzi, naleznete v tématu [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md).

Namísto použití porovnávání aktuální jazykové verze, můžete zadat <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> možnost ignoruje kulturní rozdíly v jazyce a použít konvence pro invariantní jazykovou verzi.

> [!NOTE]
> Porovnávání pomocí neutrální jazykové verze je k dispozici pouze prostřednictvím zadání <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType> hodnota, která se `options` parametr <xref:System.Text.RegularExpressions.Regex> konstruktoru třídy nebo statické metody porovnávání vzorků. Není k dispozici jako vložená možnost.

Následující příklad je stejný jako předchozí příklad s výjimkou, že statické <xref:System.Text.RegularExpressions.Regex.IsMatch%28System.String%2CSystem.String%2CSystem.Text.RegularExpressions.RegexOptions%29?displayProperty=nameWithType> metoda je volána s možnostmi, které zahrnují <xref:System.Text.RegularExpressions.RegexOptions.CultureInvariant?displayProperty=nameWithType>. I v případě, že je aktuální jazyková verze nastavena na hodnotu turečtina (Turecko), modul regulárních výrazů je schopný úspěšně porovnat "FILE" a "file" a zablokovat přístup ke zdroji souboru.

[!code-csharp[Conceptual.Regex.Language.Options#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.regex.language.options/cs/culture1.cs#15)]
[!code-vb[Conceptual.Regex.Language.Options#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.regex.language.options/vb/culture1.vb#15)]

## <a name="see-also"></a>Viz také:

- [Jazyk regulárních výrazů – stručná referenční dokumentace](../../../docs/standard/base-types/regular-expression-language-quick-reference.md)
