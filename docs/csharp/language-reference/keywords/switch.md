---
title: Příkaz switch jazyka C#
ms.date: 08/14/2018
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
ms.openlocfilehash: 371b6e232e9d97df3ce34d69bcb10155c1242e1e
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084716"
---
# <a name="switch-c-reference"></a>Přepnout (referenční dokumentace jazyka C#)

`switch` je příkaz výběru, který vybere jeden *oddíl přepínání* ke spuštění ze seznamu kandidátů podle porovnávání s *odpovídat výrazu*.

[!code-csharp[switch#1](~/samples/snippets/csharp/language-reference/keywords/switch/switch1.cs#1)]

`switch` Příkazu se často používá jako alternativu k [if-else](if-else.md) sestavit, pokud jeden výraz je testován vůči tři nebo více podmínek. Například následující `switch` příkaz určuje, zda proměnná typu `Color` obsahuje jednu ze tří hodnot:

[!code-csharp[switch#3](~/samples/snippets/csharp/language-reference/keywords/switch/switch3.cs#1)]

Je ekvivalentní v následujícím příkladu, který používá `if` - `else` vytvořit.

[!code-csharp[switch#3a](~/samples/snippets/csharp/language-reference/keywords/switch/switch3a.cs#1)]

## <a name="the-match-expression"></a>Výraz shody

Výrazy poskytuje hodnotu k porovnání vzorů v `case` popisky. Syntaxe je:

```csharp
   switch (expr)
```

V jazyce C# 6 shoda výraz musí být výraz, který vrací hodnotu z těchto typů:

- [char](char.md).
- [řetězec](string.md).
- [bool](bool.md).
- integrální hodnotu, například [int](int.md) nebo [dlouhé](long.md).
- [výčtu](enum.md) hodnotu.

Od verze C# 7.0, výrazu shody může být libovolný výraz jinou hodnotu než null.

## <a name="the-switch-section"></a>Oddíl přepínače

A `switch` výpis obsahuje jeden nebo více oddílů přepínače. Každý oddíl přepínače obsahuje jednu nebo více *malá a velká popisky* (popisek případu nebo výchozí), za nímž následuje jedna nebo více příkazů. `switch` Příkaz může obsahovat maximálně jednu výchozí popisek, umístěn v jakékoli části přepínače. Následující příklad ukazuje jednoduchý `switch` příkaz, který obsahuje tři části přepínače, každá obsahuje dva příkazy. Druhý oddíl přepínače obsahuje `case 2:` a `case 3:` popisky.

A `switch` příkaz může obsahovat libovolný počet oddílů přepínače a každý oddíl může obsahovat jeden nebo více štítků případu, jak je znázorněno v následujícím příkladu. Žádné dva popisky případů však může obsahovat stejný výraz.

[!code-csharp[switch#2](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch2.cs#1)]

Provede přepínači pouze jeden oddíl v příkazu switch. C# neumožňuje spuštění pokračovat z jednoho oddílu přepnutí na další. Proto následující kód vygeneruje chybu kompilátoru CS0163: "Ovládací prvek nemůže být předáno z jednoho návěstí příkazu case (<case label>) do jiného."

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

Tento požadavek obvykle splněn explicitně ukončením oddíl přepínače s použitím [přerušení](break.md), [goto](goto.md), nebo [vrátit](return.md) příkazu. Následující kód je však také platný, protože zajistí, že ovládací prvek programu nemůže být předáno `default` přepnutí oddílu.

[!code-csharp[switch#4](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch4.cs#1)]

Spuštění seznamu příkazů ve oddíl přepínače case popiskem, který odpovídá výrazu match začíná prvním příkazem a pokračuje přes seznam příkazů, obvykle dokud výpisu odkazů, jako například `break`, `goto case`, `goto label`, `return`, nebo `throw`, je dosaženo. V tomto okamžiku je ovládací prvek převeden mimo `switch` příkaz nebo jiný popisek případu. A `goto` příkazu, pokud se používá, musí řízení je převedeno na konstantní popisek. Toto omezení je nezbytné, protože pokus o předání řízení na nekonstantní popisek může mít nežádoucí vedlejší účinky, takový přenos řízení na neúmyslnému umístění v kódu nebo vytváření nekonečné smyčky.

## <a name="case-labels"></a>Popisky případu

Každý popisek případu určuje vzor k porovnání s výrazu match ( `caseSwitch` proměnné v předchozích příkladech). Pokud se shodují, ovládací prvek bude převeden do části přepínač, který obsahuje **první** odpovídající popisek případu. Pokud žádný popisek případu vzor odpovídá výrazu shody, ovládací prvek bude převeden do části s `default` popisek příkazu, pokud existuje. Pokud není žádný `default` případu, jsou provedeny žádné příkazy v jakékoli části přepínače a ovládací prvek bude převeden mimo `switch` příkazu.

Informace o tom, `switch` příkazu a porovnávání vzorů, najdete v článku [porovnávání vzorů s `switch` příkaz](#pattern) oddílu.

Protože C# 6 podporuje pouze konstantní vzorek a nepovoluje opakování konstantní hodnoty, popisky případu definovat vzájemně se vylučuje hodnoty a pouze jeden vzor odpovídá výrazu shody. V důsledku toho pořadí, ve kterém `case` příkazy se zobrazí, nedůležité.

V jazyce C# 7.0 ale protože jsou podporována další způsoby, popisky případů není nutné definovat vzájemně se vylučuje hodnoty a více vzorům může odpovídat výrazu match. Protože jsou spouštěny příkazy v první části přepínače, který obsahuje odpovídající vzor, pořadí, ve kterém `case` příkazy se zobrazí, je důležité. Pokud C# zjistí části přepínače, jejichž case – příkaz nebo příkazy jsou ekvivalentní, nebo jsou podmnožinou tohoto předchozích příkazů, vygeneruje chybu kompilátoru, CS8120, "případ přepínače se už zpracovala předchozí větví."

Následující příklad ukazuje `switch` příkaz, který používá celou řadu jiných vzájemně se vylučující vzory. Pokud přesunete `case 0:` oddíl přepínání tak, aby se už v první části `switch` prohlášení, C# vygeneruje chybu kompilátoru, protože celé číslo, jehož hodnota je nula je podmnožinou všech celých čísel, který je definován vzor podle `case int val` příkaz.

[!code-csharp[switch#5](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch5.cs#1)]

Můžete tento problém vyřešit a vyloučit upozornění kompilátoru v jednom ze dvou způsobů:

- Změnou pořadí oddílů přepínače.

- Pomocí [po klauzuli](#when) v `case` popisek.

## <a name="the-default-case"></a>`default` Případ

`default` Případu určuje části přepínače, které budou spuštěny, pokud výrazu shody se neshoduje s jinými `case` popisek. Pokud `default` případ není k dispozici a výrazu shody se neshoduje s jinými `case` popisek, nepropadla tok programu `switch` příkazu.

`default` Případu se mohou objevit v libovolném pořadí, v `switch` příkazu. Bez ohledu na jeho pořadí ve zdrojovém kódu, je vždy vyhodnocen poslední koneckonců `case` popisky vyhodnocení.

## <a name="a-namepattern--pattern-matching-with-the-switch-statement"></a><a name="pattern" /> Porovnávání vzorů s `switch` – příkaz

Každý `case` prohlášení definuje vzor, který, pokud odpovídá výrazu shody způsobí, že jeho nadřazený oddíl přepínače má být proveden. Všechny verze jazyka C# podporují konstantní vzorek. Zbývající vzory jsou podporované od verze C# 7.0.

### <a name="constant-pattern"></a>Konstantní vzorek

Konstantní vzorek testuje, jestli výrazu shody rovná zadané – konstanta. Syntaxe je:

```csharp
   case constant:
```

kde *konstantní* je hodnota pro testování. *konstantní* může být následující konstantní výrazy:

- A [bool](bool.md) literálu, buď `true` nebo `false`.
- Všech integrálového konstantní, například [int](int.md), [dlouhé](long.md), nebo [bajtů](byte.md).
- Název deklarovanou `const` proměnné.
- Konstanta výčtu.
- A [char](char.md) literálu.
- A [řetězec](string.md) literálu.

Konstantní výraz je vyhodnocen následujícím způsobem:

- Pokud *expr* a *konstantní* integrální typy jsou operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).

- V opačném případě je hodnota výrazu určena voláním statické [funkci Object.Equals (expr, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metody.

Následující příklad používá konstantní vzorek k určení, zda je určitý den víkendu, první den v týdnu práce, poslední den v týdnu pracovní nebo střední pracovního týdne. Je vyhodnocen jako <xref:System.DateTime.DayOfWeek?displayProperty=nameWithType> vlastnost aktuálního dne na členech <xref:System.DayOfWeek> výčtu.

[!code-csharp[switch#7](../../../../samples/snippets/csharp/language-reference/keywords/switch/const-pattern.cs#1)]

Následující příklad používá pro zpracování vstupu uživatele v konzolové aplikaci, která simuluje počítače s automatickou kávy konstantní vzorek.

[!code-csharp[switch#6](../../../../samples/snippets/csharp/language-reference/keywords/switch/switch6.cs)]

### <a name="type-pattern"></a>Vzorek typu

Model typu umožňuje stručný typ vyhodnocení a převodu. Při použití s `switch` příkaz k provedení porovnávání vzorů, testuje výraz lze převést na zadaný typ a zda může být, přetypování pro proměnnou daného typu. Syntaxe je:

```csharp
   case type varname
```

kde *typ* je název typu, na který výsledek *expr* se má převést, a *název_proměnné* je objekt, na který výsledek *expr*je převeden v případě, že porovnání se zdaří.

`case` Výraz je `true` Pokud je splněna některá z následujících akcí:

- *výraz* je instance stejného typu jako *typ*.

- *výraz* je instance typu, který je odvozen od *typ*. Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.

- *výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*. *Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci typu. *Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.

- *výraz* je instance typu, který implementuje *typ* rozhraní.

Pokud je hodnota true, výraz case *název_proměnné* je jednoznačně přiřazovat a má místní rozsah v rámci části přepínače.

Všimněte si, že `null` se neshoduje s typem. Tak, aby odpovídaly `null`, použijte následující `case` popisku:

```csharp
case null:
```

Následující příklad používá vzor typu k poskytnutí informací o různé druhy typů kolekce.

[!code-csharp[type-pattern#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern.cs#1)]

Bez porovnávání vzorů, může být napsán takto následujícím způsobem. Použití porovnávání vzorů typu produkuje kompaktnějším čitelné kódu pomocí tím eliminuje nutnost otestovat, jestli je výsledek převodu `null` nebo provádět opakované přetypování.

[!code-csharp[type-pattern2#1](~/samples/snippets/csharp/language-reference/keywords/switch/type-pattern2.cs#1)]

## <a name="a-namewhen--the-case-statement-and-the-when-clause"></a><a name="when" /> `case` Příkazu a `when` – klauzule

Od verze C# 7.0, protože příkazy case musí být vzájemně se vylučující, můžete přidat `when` klauzule zadejte další podmínky, které musí být splněny pro příkaz case vyhodnotit na hodnotu true. `when` Klauzule může být libovolný výraz, který vrací logickou hodnotu.

Následující příklad definuje základní `Shape` třídy, `Rectangle` třídu odvozenou od `Shape`a `Square` třídu odvozenou od `Rectangle`. Používá `when` klauzule zajistěte, aby `ShowShapeInfo` zpracovává `Rectangle` objekt, který má přiřazenou stejné délky a šířky jako `Square` i v případě, že nebyla inicializována jako `Square` objektu. Metoda se nepokusí k zobrazení informací o objektu, který je buď `null` nebo tvar, jehož obsah je nula.

[!code-csharp[when-clause#1](~/samples/snippets/csharp/language-reference/keywords/switch/when-clause.cs#1)]

Všimněte si, že `when` klauzule v příkladu, která se pokusí otestovat, jestli `Shape` objekt `null` nespustí. Vzor správný typ pro testování `null` je `case null:`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [příkazu switch](~/_csharplang/spec/statements.md#the-switch-statement) v [specifikace jazyka C#](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [if-else](if-else.md)
- [Porovnávání vzorů](../../pattern-matching.md)
