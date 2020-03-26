---
title: Příkaz c# switch
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
ms.openlocfilehash: 49b3836f17e91ae8de10d68e97fd662aae80d1ff
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249315"
---
# <a name="switch-c-reference"></a>přepínač (odkaz C#)

Tento článek `switch` se vztahuje na prohlášení. Informace o `switch` výrazu (zavedeném v c# 8.0) naleznete v článku o [ `switch` výrazech](../operators/switch-expression.md) v části [výrazy a operátory.](../operators/index.md)

`switch`je příkaz výběru, který vybere *jeden oddíl přepínače,* který se provede ze seznamu kandidátů na základě shody vzoru s *výrazem shody*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

Příkaz `switch` se často používá jako alternativa k [if-else](if-else.md) konstrukce, pokud jeden výraz je testován proti tři nebo více podmínek. Například následující `switch` příkaz určuje, zda proměnná typu `Color` má jednu ze tří hodnot:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Je ekvivalentní následující příklad, který `if` - `else` používá konstrukci.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Výraz shody

Výraz shody poskytuje hodnotu, která `case` se má shodovat se vzorky v popiscích. Jeho syntaxe je:

```csharp
   switch (expr)
```

V c# 6 a starší výraz shody musí být výraz, který vrací hodnotu následujících typů:

- [znak](../builtin-types/char.md).
- [řetězec](../builtin-types/reference-types.md).
- [bool](../builtin-types/bool.md).
- [integrální](../builtin-types/integral-numeric-types.md) hodnotu, `int` `long`například a nebo .
- hodnotu [výčtu.](../builtin-types/enum.md)

Počínaje C# 7.0, výraz shody může být libovolný výraz bez null.

## <a name="the-switch-section"></a>Sekce přepínače

Příkaz `switch` obsahuje jeden nebo více oddílů přepínače. Každý oddíl přepínače obsahuje jeden nebo více *popisků případu* (případ nebo výchozí popisek) následovaný jedním nebo více příkazy. Příkaz `switch` může obsahovat maximálně jeden výchozí popisek umístěný v libovolné mašice přepínače. Následující příklad ukazuje `switch` jednoduchý příkaz, který má tři oddíly přepínače, z nichž každý obsahuje dva příkazy. Druhý přepínač sekce `case 2:` obsahuje `case 3:` a popisky.

Příkaz `switch` může obsahovat libovolný počet oddílů přepínače a každý oddíl může mít jeden nebo více popisků případu, jak je znázorněno v následujícím příkladu. Žádné dva popisky případu však nesmí obsahovat stejný výraz.

[!code-csharp[switch#2](~/samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Spustí se pouze jeden oddíl přepínače v příkazu switch. C# neumožňuje spuštění pokračovat z jednoho oddílu přepínače do další. Z tohoto důvodu následující kód generuje chybu kompilátoru CS0163: "Ovládací prvek\<nemůže propadnout z jednoho popisku případu (popisek případu>) do jiného."

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

Tento požadavek je obvykle splněn explicitním ukončením oddílu přepínače pomocí příkazu [break](break.md), [goto](goto.md)nebo [return.](return.md) Následující kód je však také platný, protože zajišťuje, že ovládací `default` prvek programu nemůže propadnout do části přepínače.

[!code-csharp[switch#4](~/samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Spuštění seznamu příkazů v části switch s popiskem případu, který odpovídá výrazu shody, začíná prvním příkazem a `break`pokračuje `goto case` `goto label`v `return`seznamu příkazů, obvykle dokud není dosaženo příkazu skoku, například , , , nebo `throw`, . V tomto okamžiku je ovládací `switch` prvek převeden mimo příkaz nebo na jiný popisek případu. Příkaz, `goto` pokud se používá, musí přenést řízení na konstantní popisek. Toto omezení je nezbytné, protože pokus o přenos řízení na nekonstantní popisek může mít nežádoucí vedlejší účinky, jako přenos řízení do nezamýšleného umístění v kódu nebo vytvoření nekonečné smyčky.

## <a name="case-labels"></a>Popisky případů

Každý popisek případu určuje vzorek, který má `caseSwitch` být porovnán s výrazem shody (proměnná v předchozích příkladech). Pokud se shodují, ovládací prvek je převeden do oddílu přepínače, který obsahuje **první** odpovídající popisek případu. Pokud žádný vzor popisku případu neodpovídá výrazu shody, ovládací prvek se přenese do oddílu s popiskem `default` případu, pokud existuje. Pokud neexistuje žádný `default` případ, žádné příkazy v žádné části přepínače jsou `switch` provedeny a řízení je převedena mimo příkaz.

Informace o `switch` příkazu a porovnávání vzorů naleznete v [části Pattern odpovídající oddílu. `switch` ](#pattern)

Vzhledem k tomu, že C# 6 podporuje pouze konstantní vzor a neumožňuje opakování konstantní hodnoty, popisky případu definovat vzájemně se vylučující hodnoty a pouze jeden vzorek může odpovídat výrazu shody. V důsledku toho pořadí, `case` ve kterém příkazy se zobrazí, není důležité.

V c# 7.0 však protože ostatní vzorky jsou podporovány, popisky případu nemusí definovat vzájemně se vylučující hodnoty a více vzorů může odpovídat výrazu shody. Vzhledem k tomu, že jsou provedeny pouze příkazy v první `case` části přepínače, která obsahuje odpovídající vzorek, pořadí, ve kterém příkazy se zobrazí, je nyní důležité. Pokud C# zjistí oddíl přepínače, jehož case prohlášení nebo příkazy jsou rovnocenné nebo jsou podmnožiny předchozí příkazy, generuje chybu kompilátoru, CS8120, "případ přepínače již byla zpracována předchozí případ."

Následující příklad ilustruje `switch` příkaz, který používá různé vzory, které se nevylučují. Pokud přesunete `case 0:` oddíl přepínačtak, že již není první `switch` část v příkazu, C# generuje chybu kompilátoru, protože celé číslo, jehož hodnota je nula je podmnožinou všech celých čísel, což je vzor definovaný příkazem. `case int val`

[!code-csharp[switch#5](~/samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Tento problém můžete opravit a odstranit upozornění kompilátoru jedním ze dvou způsobů:

- Změnou pořadí sekcí přepínače.

- Pomocí [when klauzule](#when) `case` v popisku.

## <a name="the-default-case"></a>Případ `default`

Případ `default` určuje oddíl přepínače, který má být proveden, `case` pokud výraz shody neodpovídá žádnému jinému popisku. Pokud `default` případ není k dispozici a výraz shody `case` neodpovídá žádnému `switch` jinému popisku, tok programu spadá do příkazu.

Případ `default` se může objevit v `switch` libovolném pořadí v příkazu. Bez ohledu na jeho pořadí ve zdrojovém kódu je `case` vždy vyhodnocena jako poslední, poté, co byly vyhodnoceny všechny popisky.

## <a name="pattern-matching-with-the-switch-statement"></a><a name="pattern" />Porovnávání vzorů `switch` s příkazem

Každý `case` příkaz definuje vzor, který, pokud odpovídá výrazu shody, způsobí, že jeho část obsahující přepínač bude spuštěna. Všechny verze jazyka C# podporují konstantní vzor. Zbývající vzorky jsou podporovány počínaje C# 7.0.

### <a name="constant-pattern"></a>Konstantní vzor

Konstantní vzorek testuje, zda se výraz shody rovná zadané konstantě. Jeho syntaxe je:

```csharp
   case constant:
```

*kde konstanta* je hodnota, pro kterou se má testovat. *konstanta* může být některý z následujících konstantních výrazů:

- [Bool](../builtin-types/bool.md) literál: `true` `false`buď nebo .
- Jakákoli [integrální](../builtin-types/integral-numeric-types.md) `int`konstanta, například , a `long`nebo . `byte`
- Název deklarované `const` proměnné.
- Konstanta výčtu.
- [Char](../builtin-types/char.md) doslovný.
- [Řetězcový](../builtin-types/reference-types.md) literál.

Konstantní výraz je vyhodnocen takto:

- Pokud *expr* a *konstanta* jsou integrální typy, c# operátor rovnosti určuje, zda výraz vrátí `true` (to znamená, zda `expr == constant`).

- Jinak je hodnota výrazu určena voláním statické [metody Object.Equals(expr, constant).](xref:System.Object.Equals(System.Object,System.Object))

Následující příklad používá konstantní vzor k určení, zda je určité datum víkend, první den pracovního týdne, poslední den pracovního týdne nebo uprostřed pracovního týdne. Vyhodnotí <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> vlastnost aktuální ho dne proti <xref:System.DayOfWeek> členům výčtu.

[!code-csharp[switch#7](~/samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Následující příklad používá konstantní vzor pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje automatický kávovar.

[!code-csharp[switch#6](~/samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Vzor typu

Vzorek typu umožňuje stručné hodnocení typu a převod. Při použití `switch` s příkazem provádět porovnávání vzorů, testuje, zda výraz lze převést na zadaný typ, a pokud může být, přetypování do proměnné tohoto typu. Jeho syntaxe je:

```csharp
   case type varname
```

kde *type* je název typu, na který má být převeden výsledek *expr,* a *varname* je objekt, na který je výsledek *expr* převeden, pokud je shoda úspěšná. Typ *expr* v době kompilace může být parametr obecného typu, počínaje C# 7.1.

Výraz `case` je, `true` pokud je splněna některá z následujících hodnot:

- *expr* je instancí stejného typu jako *typ*.

- *expr* je instancí typu, který je odvozen od *typu*. Jinými slovy, výsledek *expr* může být upcast na instanci *typu*.

- *expr* má typ kompilace, který je základní třídou *typu*, a *expr* má typ runtime, který je *typu* nebo je odvozen od *typu*. Typ proměnné v *době kompilace* je typ proměnné, jak je definován v deklaraci typu. *Typ runtime* proměnné je typ instance, která je přiřazena k této proměnné.

- *expr* je instancí třídy typu, který implementuje *rozhraní typu.*

Pokud je výraz případu true, *varname* je jednoznačně přiřazena a má místní obor v rámci oddílu switch.

Všimněte `null` si, že neodpovídá typu. Chcete-li `null`odpovídat , `case` použijte následující popisek:

```csharp
case null:
```

Následující příklad používá vzor typu k poskytnutí informací o různých typech typů kolekcí.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Místo `object`, můžete provést obecnou metodu pomocí typu kolekce jako parametr typu, jak je znázorněno v následujícím kódu:

[!code-csharp[type-pattern#3](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern3.cs#1)]

Obecná verze se liší od první ukázky dvěma způsoby. Za prvé, nemůžete použít `null` případ. Nelze použít žádný konstantní případ, protože kompilátor nelze převést libovolný `T` typ `object`na jiný typ než . Co bylo `default` v případě nyní testuje `object`pro non-null . To znamená, `default` že `null`případ testy pouze pro .

Bez porovnávání vzorů může být tento kód zapsán následujícím způsobem. Použití odpovídající typ vzorku vytváří kompaktnější, čitelný kód tím, že eliminuje potřebu `null` otestovat, zda je výsledkem převodu nebo provádět opakované přetypování.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="the-case-statement-and-the-when-clause"></a><a name="when" />Prohlášení `case` a `when` doložka

Počínaje C# 7.0, protože case příkazy nemusí být vzájemně `when` vylučovat, můžete přidat klauzule určit další podmínku, která musí být splněna pro případ prohlášení vyhodnotit na true. Klauzule `when` může být libovolný výraz, který vrací logickou hodnotu.

Následující příklad definuje základní `Shape` třídu, `Rectangle` třídu, `Shape`která `Square` je odvozena `Rectangle`od , a třídu, která je odvozena z . `when` Používá klauzuli k zajištění, že `ShowShapeInfo` zachází `Rectangle` objekt, který byl přiřazen stejné `Square` délky a šířky jako i `Square` v případě, že nebyl anas unátřizován jako objekt. Metoda se nepokouší zobrazit informace o objektu, který je, `null` nebo obrazec, jehož plocha je nula.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Všimněte `when` si, že klauzule v příkladu, který se pokusí otestovat, zda `Shape` je `null` objekt neprovede. Správný vzorek typu pro `null` testování `case null:`je .

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete [v příkazu switch](~/_csharplang/spec/statements.md#the-switch-statement) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [C# Klíčová slova](index.md)
- [if-else](if-else.md)
- [Porovnávání](../../pattern-matching.md)
