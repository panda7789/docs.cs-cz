---
title: Příkaz přepínače jazyka C#
ms.date: 04/09/2019
f1_keywords:
- switch_CSharpKeyword
- switch
- case
- case_CSharpKeyword
helpviewer_keywords:
- switch statement [C#]
- switch keyword [C#]
- case statement [C#]
- default keyword [C#]
ms.assetid: 44bae8b8-8841-4d85-826b-8a94277daecb
ms.openlocfilehash: 9335399be2d4909a02fecbf2959c6f5608664732
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84493666"
---
# <a name="switch-c-reference"></a>Switch (Referenční dokumentace jazyka C#)

Tento článek se zabývá `switch` příkazem. Informace o `switch` výrazu (představené v C# 8,0) najdete v článku [ `switch` výrazy](../operators/switch-expression.md) v části [výrazy a operátory](../operators/index.md) .

`switch`je příkaz výběru, který zvolí oddíl s jedním *přepínačem* , který se má provést ze seznamu kandidátů na základě porovnávání vzorů s *výrazem shody*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

`switch`Příkaz se často používá jako alternativa k konstruktoru [if-else](if-else.md) , pokud je jeden výraz testován proti třem nebo více podmínkám. Například následující `switch` příkaz určuje, zda proměnná typu `Color` má jednu ze tří hodnot:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Je ekvivalentní s následujícím příkladem, který používá `if` - `else` konstrukci.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Výraz shody

Výraz Match poskytuje hodnotu odpovídající vzorům v `case` popiscích. Jeho syntaxe je:

```csharp
   switch (expr)
```

V jazyce C# 6 a dřívější výraz porovnávání musí být výraz, který vrací hodnotu následujících typů:

- [znak](../builtin-types/char.md).
- [řetězec](../builtin-types/reference-types.md).
- [logická](../builtin-types/bool.md)hodnota.
- [celočíselná](../builtin-types/integral-numeric-types.md) hodnota, například `int` nebo `long` .
- hodnota [výčtu](../builtin-types/enum.md) .

Počínaje jazykem C# 7,0 může výraz porovnávání být libovolný výraz, který není null.

## <a name="the-switch-section"></a>Oddíl Switch

`switch`Příkaz obsahuje jeden nebo více oddílů přepínače. Každý oddíl přepínače obsahuje jeden nebo více *popisků Case* (buď označení Case nebo Default) následovaný jedním nebo více příkazy. `switch`Příkaz může obsahovat maximálně jeden výchozí popisek umístěný v libovolném oddílu Switch. Následující příklad ukazuje jednoduchý `switch` příkaz, který má tři oddíly přepínače, z nichž každý obsahuje dva příkazy. Oddíl druhého přepínače obsahuje `case 2:` `case 3:` popisky a.

`switch`Příkaz může obsahovat libovolný počet oddílů přepínače a každý oddíl může obsahovat jeden nebo více popisků případu, jak je znázorněno v následujícím příkladu. Nicméně žádné dva popisky case nemůžou obsahovat stejný výraz.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Provede se pouze jeden oddíl Switch v příkazu switch. C# neumožní pokračování v provádění jednoho oddílu přepínače na další. Z tohoto důvodu následující kód vygeneruje chybu kompilátoru, CS0163: "řízení nemůže být z jednoho popisku Case ( \<case label> ) do jiného."

```csharp
switch (caseSwitch)
{
    // The following switch section causes an error.
    case 1:
        Console.WriteLine("Case 1...");
        // Add a break or other jump statement here.
    case 2:
        Console.WriteLine("... and/or Case 2");
        break;
}
```

Tento požadavek se obvykle splní explicitním ukončením oddílu přepínače pomocí příkazu [Break](break.md), [goto](goto.md)nebo [return](return.md) . Následující kód je však také platný, protože zajišťuje, že řízení programu nemůže `default` Přejít do oddílu Switch.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Spuštění seznamu příkazů v oddílu switch s popiskem Case, který odpovídá výrazu Match začíná prvním příkazem a pokračuje přes seznam příkazů, obvykle dokud není dosaženo příkazu skok, jako je,,, `break` `goto case` `goto label` `return` nebo `throw` . V tomto okamžiku je ovládací prvek převeden mimo `switch` příkaz nebo na jiný popisek případu. `goto`Příkaz, pokud se používá, musí přenést řízení na konstantní popisek. Toto omezení je nezbytné, protože při pokusu o přenos řízení na nekonstantní popisek může mít nežádoucí vedlejší účinky, například přenáší řízení na nezamýšlené umístění v kódu nebo vytvoření nekonečné smyčky.

## <a name="case-labels"></a>Popisky případů

Každý popisek případu určuje vzor, který se má porovnat s výrazem shody ( `caseSwitch` Proměnná v předchozích příkladech). Pokud se shodují, ovládací prvek se přenese do oddílu Switch, který obsahuje **první** odpovídající popisek případu. Pokud žádný vzor popisku případu neodpovídá výrazu Match, je ovládací prvek převeden do oddílu s `default` popiskem Case, pokud existuje. Pokud není žádný `default` případ, nejsou spuštěny žádné příkazy v žádném oddílu přepínače a ovládací prvek se přenese mimo `switch` příkaz.

Informace o `switch` příkazu a porovnávání vzorů naleznete v tématu porovnávání [vzorů s oddílem `switch` Statement](#pattern-matching with-the-switch-statement) .

Vzhledem k tomu, že C# 6 podporuje pouze konstantní vzor a neumožňuje opakování konstantních hodnot, popisky case definují vzájemně se vylučující hodnoty a pouze jeden vzor může odpovídat výrazu shody. V důsledku toho pořadí, ve kterém `case` se zobrazují příkazy, je neimportované.

V jazyce C# 7,0 však, protože jsou podporovány jiné modely, popisky case nemusí definovat vzájemně se vylučující hodnoty a více vzorů může odpovídat výrazu shody. Vzhledem k tomu, že jsou spuštěny pouze příkazy v první části přepínače obsahující odpovídající vzor, je nyní důležité pořadí, ve kterém jsou `case` příkazy zobrazeny. Pokud C# detekuje oddíl Switch, jehož příkaz Case nebo příkazy jsou ekvivalentní nebo jsou podmnožinou předchozích příkazů, vygeneruje chybu kompilátoru, CS8120, "případ přepínače již byl zpracován předchozím případem".

Následující příklad znázorňuje `switch` příkaz, který používá celou řadu nevzájemně se vylučujících vzorů. Pokud přesunete `case 0:` oddíl Switch tak, že již není prvním oddílem v `switch` příkazu, C# vygeneruje chybu kompilátoru, protože celé číslo, jehož hodnota je nula, je podmnožina všech celých čísel, což je vzor definovaný `case int val` příkazem.

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Tento problém můžete vyřešit a odstranit upozornění kompilátoru jedním ze dvou způsobů:

- Změnou pořadí oddílů přepínače.

- Použitím [klauzule when](#the-case-statement-and-the-when-clause) v `case` popisku.

## <a name="the-default-case"></a>`default`Případ

`default`Parametr Case určuje oddíl přepínače, který se má provést, pokud výraz shody neodpovídá žádnému jinému `case` popisku. Pokud není k `default` dispozici případ a výraz shody neodpovídá žádnému jinému `case` popisku, tok programu přepadne do `switch` příkazu.

`default`Případ se může objevit v libovolném pořadí `switch` příkazu. Bez ohledu na pořadí ve zdrojovém kódu je vždy vyhodnoceno jako poslední, po `case` vyhodnocení všech popisků.

## <a name="pattern-matching-with-the-switch-statement"></a>Porovnávání vzorů s `switch` příkazem

Každý `case` příkaz definuje vzor, který, pokud se shoduje s výrazem shody, způsobí, že obsahuje oddíl obsahujícího přepínače, který má být spuštěn. Všechny verze jazyka C# podporují konstantní vzorek. Zbývající vzorce jsou podporovány počínaje jazykem C# 7,0.

### <a name="constant-pattern"></a>Konstantní vzorek

Konstantní vzor testuje, zda se výraz shody rovná zadané konstantě. Jeho syntaxe je:

```csharp
   case constant:
```

kde *konstanta* je hodnota, která má být testována. *konstanta* může být libovolný z následujících konstantních výrazů:

- Literál [bool](../builtin-types/bool.md) : `true` nebo `false` .
- Jakékoli [integrální](../builtin-types/integral-numeric-types.md) konstanty, například `int` , a `long` , nebo `byte` .
- Název deklarované `const` proměnné.
- Konstanta výčtu.
- Literál [znaků](../builtin-types/char.md) .
- [Řetězcový](../builtin-types/reference-types.md) literál.

Konstantní výraz je vyhodnocen následujícím způsobem:

- Pokud je *výraz* a *konstanta* integrální typy, operátor rovnosti jazyka C# určuje, zda výraz vrátí hodnotu `true` (tj `expr == constant` . zda).

- V opačném případě je hodnota výrazu určena voláním statické metody [Object. Equals (Expr, konstanta)](xref:System.Object.Equals(System.Object,System.Object)) .

V následujícím příkladu je použit model konstanty k určení, zda je konkrétní datum víkend, první den pracovního týdne, poslední den pracovního týdne nebo uprostřed pracovního týdne. Vyhodnocuje <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> vlastnost aktuálního dne proti členům <xref:System.DayOfWeek> výčtu.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Následující příklad používá konstantní vzorek pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje automatický kavárnový počítač.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Vzor typu

Vzor typu umožňuje napsat a převést stručný typ hodnocení. Při použití s `switch` příkazem k provedení porovnávání vzorů testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování na proměnnou daného typu. Jeho syntaxe je:

```csharp
   case type varname
```

kde *Type* je název typu, na který má být výsledek *výrazu* převeden, a *název_proměnné* je objekt, na který je výsledek *výrazu* převeden, pokud je shoda úspěšná. Typ *výrazu* v čase kompilace může být parametr obecného typu, počínaje jazykem C# 7,1.

`case`Výraz je v `true` případě, že platí některá z následujících podmínek:

- *výraz* je instancí stejného typu jako *typ*.

- *expr* je instance typu, která je odvozena z *typu*. Jinými slovy výsledek *výrazu* lze přetypování na instanci *typu*.

- *výraz* má typ při kompilaci, který je základní třídou *typu*, a *výraz* má typ modulu runtime, který je *typu* nebo je odvozen z *typu*. *Typ proměnné doby kompilace* proměnné je typ proměnné definovaný v deklaraci typu. *Typ modulu runtime* proměnné je typ instance, která je přiřazena této proměnné.

- *expr* je instance typu, který implementuje rozhraní *typu* .

Pokud *je výraz Case pravdivý, má* jednoznačně přiřazený a má místní rozsah jenom v rámci oddílu Switch.

Všimněte si, že `null` se neshoduje s typem. K vyhledání shody `null` použijte následující `case` popisek:

```csharp
case null:
```

V následujícím příkladu je použit vzor typu k poskytnutí informací o různých typech kolekcí.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Namísto `object` byste mohli vytvořit obecnou metodu pomocí typu kolekce jako parametru typu, jak je znázorněno v následujícím kódu:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Obecná verze se liší od první ukázky dvěma způsoby. Nejdříve nemůžete použít `null` případ. Nemůžete použít žádný konstantní případ, protože kompilátor nemůže převést libovolný typ `T` na jiný typ než `object` . Jaký byl `default` případ nyní testů pro jinou hodnotu než null `object` . To znamená, že `default` testy případu jsou pouze pro `null` .

Bez porovnávání vzorů může být tento kód napsán následujícím způsobem. Použití porovnávání vzorů typů vytváří více kompaktních čitelných kódů tím, že eliminuje nutnost testovat, zda je výsledek převodu `null` nebo aby prováděl opakované přetypování.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a>`case`Příkaz a `when` klauzule

Počínaje jazykem C# 7,0, protože příkazy Case nemusejí být vzájemně exkluzivní, můžete přidat `when` klauzuli pro určení další podmínky, která musí být splněna, aby příkaz Case vyhodnotil hodnotu true. `when`Klauzule může být libovolný výraz, který vrací logickou hodnotu.

Následující příklad definuje základní `Shape` třídu, `Rectangle` třídu, která je odvozena z třídy `Shape` , a `Square` třídu, která je odvozena z `Rectangle` . Používá `when` klauzuli k zajištění toho, aby `ShowShapeInfo` považovala `Rectangle` objekt, kterému byla přiřazena shodná délka a šířka, a `Square` to i v případě, že nebyla vytvořena instance `Square` objektu. Metoda se nepokusí zobrazit informace buď s objektem, který je `null` nebo tvarem, jehož oblast je nula.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Všimněte si, že `when` klauzule v příkladu, která se pokouší otestovat, zda `Shape` objekt není `null` spuštěn. Správný vzor typu, který se má testovat, `null` je `case null:` .

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v [příkazu switch](~/_csharplang/spec/statements.md#the-switch-statement) v tématu [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [if-else](if-else.md)
- [Porovnávání vzorů](../../pattern-matching.md)
