---
title: C#příkaz switch
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
ms.openlocfilehash: 6f0a2cfd5a6de9c8c05bc3daea1e242183ebf03e
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552343"
---
# <a name="switch-c-reference"></a>přepínač (C# Referenční dokumentace)

`switch` je příkaz výběru, který zvolí oddíl s jedním *přepínačem* , který se má provést ze seznamu kandidátů na základě porovnávání vzorů s *výrazem shody*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

Příkaz `switch` se často používá jako alternativa k konstruktoru [if-else](if-else.md) , pokud je jeden výraz testován proti třem nebo více podmínkám. Například následující příkaz `switch` určuje, zda proměnná typu `Color` má jednu ze tří hodnot:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Je ekvivalentní s následujícím příkladem, který používá `if`-`else` konstrukce.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Výraz shody

Výraz Match poskytuje hodnotu odpovídající vzorům v `case` popisky. Jeho syntaxe je:

```csharp
   switch (expr)
```

V C# 6 a starších verzích výraz porovnávání musí být výraz, který vrací hodnotu následujících typů:

- [znak](../builtin-types/char.md).
- [řetězec](../builtin-types/reference-types.md).
- [logická](../builtin-types/bool.md)hodnota.
- [celočíselná](../builtin-types/integral-numeric-types.md) hodnota, například `int` nebo `long`.
- hodnota [výčtu](enum.md) .

Počínaje C# 7,0 se výraz shody může jednat o libovolný výraz, který není null.

## <a name="the-switch-section"></a>Oddíl Switch

Příkaz `switch` obsahuje jeden nebo více oddílů přepínače. Každý oddíl přepínače obsahuje jeden nebo více *popisků Case* (buď označení Case nebo Default) následovaný jedním nebo více příkazy. Příkaz `switch` může zahrnovat maximálně jeden výchozí popisek umístěný v jakémkoli oddílu přepínače. Následující příklad ukazuje jednoduchý příkaz `switch`, který má tři oddíly přepínače, z nichž každý obsahuje dva příkazy. Oddíl druhého přepínače obsahuje popisky `case 2:` a `case 3:`.

Příkaz `switch` může obsahovat libovolný počet oddílů přepínače a každý oddíl může obsahovat jeden nebo více popisků případu, jak je znázorněno v následujícím příkladu. Nicméně žádné dva popisky case nemůžou obsahovat stejný výraz.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Provede se pouze jeden oddíl Switch v příkazu switch. C#neumožňuje pokračování v provádění jednoho oddílu přepínače na další. Z tohoto důvodu následující kód vygeneruje chybu kompilátoru, CS0163: "ovládací prvek nemůže přejít z jednoho popisku Case (\<popisek případu >) do jiného."

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

Tento požadavek se obvykle splní explicitním ukončením oddílu přepínače pomocí příkazu [Break](break.md), [goto](goto.md)nebo [return](return.md) . Následující kód je však také platný, protože zajišťuje, že řízení programu nemůže přejít do oddílu `default` Switch.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Provedení seznamu příkazů v oddílu switch s popiskem Case, který odpovídá výrazu shody, začíná prvním příkazem a pokračuje přes seznam příkazů, obvykle dokud není příkaz skoku, například `break``goto case``goto label`, `return`nebo `throw`, je dosaženo. V tomto okamžiku se ovládací prvek přenáší mimo příkaz `switch` nebo na jiný popisek případu. Příkaz `goto`, pokud se používá, musí přenést řízení na konstantní popisek. Toto omezení je nezbytné, protože při pokusu o přenos řízení na nekonstantní popisek může mít nežádoucí vedlejší účinky, například přenáší řízení na nezamýšlené umístění v kódu nebo vytvoření nekonečné smyčky.

## <a name="case-labels"></a>Popisky případů

Každý popisek případu určuje vzor, který se má porovnat s výrazem shody (`caseSwitch` proměnnou v předchozích příkladech). Pokud se shodují, ovládací prvek se přenese do oddílu Switch, který obsahuje **první** odpovídající popisek případu. Pokud žádný vzor popisku případu neodpovídá výrazu shody, ovládací prvek se přenese do oddílu pomocí popisku `default` případu, pokud existuje. Pokud není k dispozici žádný `default` případ, nejsou provedeny žádné příkazy v žádném oddílu přepínače a ovládací prvek se přenese mimo příkaz `switch`.

Informace o příkazu `switch` a porovnávání vzorů naleznete v části [porovnávání vzorů pomocí příkazu `switch`](#pattern) .

Vzhledem C# k tomu, že 6 podporuje pouze konstantní vzor a neumožňuje opakování konstantních hodnot, popisky case definují vzájemně se vylučující hodnoty a pouze jeden vzor může odpovídat výrazu shody. V důsledku toho je pořadí, ve kterém jsou `case` příkazy, neimportované.

V C# 7,0, protože jsou však podporovány jiné modely, popisky case nemusí definovat vzájemně se vylučující hodnoty a více vzorů se může shodovat s výrazem shody. Vzhledem k tomu, že jsou spuštěny pouze příkazy v prvním oddílu přepínače, který obsahuje odpovídající vzor, je nyní důležité pořadí, v jakém jsou `case` příkazy. Pokud C# zjistí oddíl Switch, jehož příkaz Case nebo příkazy jsou ekvivalentní nebo jsou podmnožinou předchozích příkazů, vygeneruje chybu kompilátoru, CS8120, "případ přepínače již byl zpracován předchozím případem".

Následující příklad ukazuje příkaz `switch`, který používá celou řadu nevzájemně se vylučujících vzorů. Pokud přesunete oddíl `case 0:` přepínač tak, že již není prvním oddílem v příkazu `switch`, vygeneruje chybu C# kompilátoru, protože celé číslo, jehož hodnota je nula, je podmnožina všech celých čísel, což je vzor definovaný pomocí příkazu `case int val` .

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Tento problém můžete vyřešit a odstranit upozornění kompilátoru jedním ze dvou způsobů:

- Změnou pořadí oddílů přepínače.

- Pomocí [klauzule when](#when) v popisku `case`.

## <a name="the-default-case"></a>Případ `default`

`default` případ určuje oddíl Switch, který se má provést, pokud výraz shody neodpovídá žádnému jinému popisku `case`. Pokud není přítomen případ `default` a výraz shody neodpovídá žádnému jinému popisku `case`, tok programu spadá do příkazu `switch`.

`default` případ se může v příkazu `switch` zobrazit v libovolném pořadí. Bez ohledu na pořadí ve zdrojovém kódu je vždy vyhodnoceno jako poslední, po vyhodnocení všech `case`ch popisků.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" /> porovnávání vzorů s příkazem `switch`

Každý příkaz `case` definuje vzor, který, pokud se shoduje s výrazem shody, způsobí, že obsahuje oddíl obsahujícího přepínače, který má být spuštěn. Všechny verze nástroje C# podporují konstantní vzorek. Zbývající vzorce jsou podporovány od C# 7,0.

### <a name="constant-pattern"></a>Konstantní vzorek

Konstantní vzor testuje, zda se výraz shody rovná zadané konstantě. Jeho syntaxe je:

```csharp
   case constant:
```

kde *konstanta* je hodnota, která má být testována. *konstanta* může být libovolný z následujících konstantních výrazů:

- Literál [bool](../builtin-types/bool.md) : buď `true`, nebo `false`.
- Jakákoli [integrální](../builtin-types/integral-numeric-types.md) konstanta, například `int`, `long`nebo `byte`.
- Název deklarované `const` proměnné.
- Konstanta výčtu.
- Literál [znaků](../builtin-types/char.md) .
- [Řetězcový](../builtin-types/reference-types.md) literál.

Konstantní výraz je vyhodnocen následujícím způsobem:

- Je *-li výraz* a *konstanta* integrální typy C# , operátor rovnosti určuje, zda výraz vrátí hodnotu `true` (tj. zda `expr == constant`).

- V opačném případě je hodnota výrazu určena voláním statické metody [Object. Equals (Expr, konstanta)](xref:System.Object.Equals(System.Object,System.Object)) .

V následujícím příkladu je použit model konstanty k určení, zda je konkrétní datum víkend, první den pracovního týdne, poslední den pracovního týdne nebo uprostřed pracovního týdne. Vyhodnocuje vlastnost <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> aktuálního dne proti členům <xref:System.DayOfWeek> výčtu.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Následující příklad používá konstantní vzorek pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje automatický kavárnový počítač.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Vzor typu

Vzor typu umožňuje napsat a převést stručný typ hodnocení. Při použití s příkazem `switch` k provedení porovnávání se vzorem testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování na proměnnou daného typu. Jeho syntaxe je:

```csharp
   case type varname
```

kde *Type* je název typu, na který má být výsledek *výrazu* převeden, a *název_proměnné* je objekt, na který je výsledek *výrazu* převeden, pokud je shoda úspěšná. Typ *výrazu* v čase kompilace může být parametr obecného typu, počínaje C# 7,1.

Výraz `case` je `true`, pokud platí některá z následujících podmínek:

- *výraz* je instancí stejného typu jako *typ*.

- *expr* je instance typu, která je odvozena z *typu*. Jinými slovy výsledek *výrazu* lze přetypování na instanci *typu*.

- *výraz* má typ při kompilaci, který je základní třídou *typu*, a *výraz* má typ modulu runtime, který je *typu* nebo je odvozen z *typu*. *Typ proměnné doby kompilace* proměnné je typ proměnné definovaný v deklaraci typu. *Typ modulu runtime* proměnné je typ instance, která je přiřazena této proměnné.

- *expr* je instance typu, který implementuje rozhraní *typu* .

Pokud *je výraz Case pravdivý, má* jednoznačně přiřazený a má místní rozsah jenom v rámci oddílu Switch.

Všimněte si, že `null` neodpovídá typu. Aby se shodovala s `null`, použijte následující `case` popisek:

```csharp
case null:
```

V následujícím příkladu je použit vzor typu k poskytnutí informací o různých typech kolekcí.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Místo `object`můžete vytvořit obecnou metodu pomocí typu kolekce jako parametru typu, jak je znázorněno v následujícím kódu:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Obecná verze se liší od první ukázky dvěma způsoby. Nejdříve nemůžete použít případ `null`. Nemůžete použít žádný konstantní případ, protože kompilátor nemůže převést libovolný typ `T` na jiný typ než `object`. Co byl `default` případ nyní testuje `object`, která není null. To znamená, že `default` testy případu pouze pro `null`.

Bez porovnávání vzorů může být tento kód napsán následujícím způsobem. Použití porovnávání vzorů typů vytváří více kompaktních a čitelných kódů tím, že eliminuje nutnost testovat, zda je výsledek převodu `null` nebo aby prováděl opakované přetypování.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><a name="when" /> příkazu `case` a klauzule `when`

Počínaje C# 7,0, protože příkazy Case nemusejí být vzájemně exkluzivní, můžete přidat klauzuli `when` pro určení další podmínky, která musí být splněna, aby se příkaz Case vyhodnotil na hodnotu true. Klauzule `when` může být libovolný výraz, který vrací logickou hodnotu.

Následující příklad definuje základní třídu `Shape`, `Rectangle` třídu odvozenou z `Shape`a třídu `Square`, která je odvozena z `Rectangle`. Používá klauzuli `when`, aby se zajistilo, že `ShowShapeInfo` zachází s objektem `Rectangle`, kterému byla přiřazena shodná délka a šířka jako `Square` i v případě, že nebyla vytvořena instance objektu `Square`. Metoda se nepokusí zobrazit informace buď s objektem, který je `null` nebo tvar, jehož oblast je nula.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Všimněte si, že klauzule `when` v příkladu, která se pokouší otestovat, zda je objekt `Shape` `null` není spuštěn. `case null:`je správný vzor typu pro otestování `null`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v [příkazu switch](~/_csharplang/spec/statements.md#the-switch-statement) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [if-else](if-else.md)
- [Porovnávání vzorů](../../pattern-matching.md)
