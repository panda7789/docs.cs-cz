---
title: Implicitně typované lokální proměnné – Průvodce programováním v C#
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 842f73b7af9671157495df961f5db22702ae897e
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84240704"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Implicitně typované lokální proměnné (Průvodce programováním v C#)

Lokální proměnné lze deklarovat bez poskytnutí explicitního typu. `var`Klíčové slovo instruuje kompilátor, aby odvodí typ proměnné z výrazu na pravé straně příkazu inicializace. Odvozený typ může být vestavěný typ, anonymní typ, uživatelsky definovaný typ nebo typ definovaný v knihovně tříd .NET. Další informace o tom, jak inicializovat pole pomocí `var` , naleznete v tématu [implicitně typované pole](../arrays/implicitly-typed-arrays.md).

Následující příklady znázorňují různé způsoby, jak lze s místními proměnnými deklarovat `var` :

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

Je důležité pochopit, že `var` klíčové slovo neznamená "variantu" a neindikuje, že proměnná je volně zadaná nebo má pozdní vazbu. Pouze to znamená, že kompilátor určí a přiřadí nejvhodnější typ.

`var`Klíčové slovo lze použít v následujících kontextech:

- Na místních proměnných (proměnné deklarované v oboru metody), jak je znázorněno v předchozím příkladu.

- V příkazu [for](../../language-reference/keywords/for.md) Initialization.

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- V příkazu [foreach](../../language-reference/keywords/foreach-in.md) Initialization.

    ```csharp
    foreach (var item in list) {...}
    ```

- V příkazu [using](../../language-reference/keywords/using-statement.md) .

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Další informace najdete v tématu [použití implicitního typu lokálních proměnných a polí ve výrazu dotazu](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).

## <a name="var-and-anonymous-types"></a>var a anonymní typy

V mnoha případech je použití `var` volitelné a je pouze syntaktické pohodlí. Nicméně pokud je proměnná inicializována pomocí anonymního typu, je nutné deklarovat proměnnou jako v `var` případě, že potřebujete získat přístup k vlastnostem objektu později. Toto je běžný scénář ve výrazech dotazů LINQ. Další informace najdete v tématu [anonymní typy](anonymous-types.md).

Z perspektivy zdrojového kódu nemá anonymní typ žádný název. Proto pokud byla proměnná dotazu inicializována s `var` , pak jediným způsobem, jak získat přístup k vlastnostem v vrácené sekvenci objektů, je použít `var` jako typ proměnné iterace v `foreach` příkazu.

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Poznámky

Následující omezení platí pro implicitně typové deklarace proměnných:

- `var`dá se použít jenom v případě, že je místní Proměnná deklarovaná a inicializovaná v rámci stejného příkazu. proměnnou nelze inicializovat na hodnotu null nebo do skupiny metod nebo do anonymní funkce.

- `var`nelze použít pro pole v oboru třídy.

- Proměnné deklarované pomocí `var` nelze použít ve výrazu inicializace. Jinými slovy, tento výraz je platný: `int i = (i = 20);` Tento výraz však vytvoří chybu při kompilaci:`var i = (i = 20);`

- V rámci stejného příkazu nelze inicializovat více proměnných s implicitním typem.

- Pokud je typ s názvem `var` v oboru, klíčové slovo se přeloží `var` na tento název typu a nebude zpracováno jako součást implicitně typové deklarace lokální proměnné.

Implicitní zápis s `var` klíčovým slovem lze použít pouze pro proměnné v oboru místních metod. Implicitní psaní není k dispozici pro pole třídy, protože kompilátor jazyka C# by narazil na logický kód Paradox při zpracování kódu: kompilátor musí znát typ pole, ale nemůže určit typ, dokud není výraz přiřazení analyzován, a výraz nelze vyhodnotit bez znalosti typu. Uvažujte následující kód:

```csharp
private var bookTitles;
```

`bookTitles`je pole třídy daného typu `var` . Vzhledem k tomu, že pole nemá žádný výraz k vyhodnocení, není možné, aby kompilátor odvodit, jaký typ `bookTitles` by měl být. Kromě toho je také nedostatečné Přidání výrazu do pole (například pro místní proměnnou):

```csharp
private var bookTitles = new List<string>();
```

Když kompilátor narazí na pole během kompilování kódu, zaznamenává typ každého pole před zpracováním jakýchkoli výrazů, které jsou k němu přidruženy. Kompilátor narazí na stejný Paradox, který se snaží analyzovat `bookTitles` : potřebuje znát typ pole, ale kompilátor obvykle určí `var` typ analýzou výrazu, který není možné bez vědomí typu předem.

Může se stát, že může `var` být vhodný také pro výrazy dotazů, ve kterých je obtížné určit přesný konstruovaný typ proměnné dotazu. K tomu může dojít při operacích seskupování a řazení.

`var`Klíčové slovo může být užitečné také v případě, že konkrétní typ proměnné je únavné pro psaní na klávesnici nebo je zřejmé nebo není možné přidat k čitelnosti kódu. Jeden příklad, kde `var` je tento způsob užitečný, je s vnořenými obecnými typy, jako jsou ty, které se používají při operacích skupin. V následujícím dotazu je typ proměnné dotazu `IEnumerable<IGrouping<string, Student>>` . Pokud vy a ostatní uživatelé, kteří musí tento kód pochopit, neexistují žádné potíže s používáním implicitního zadávání pro pohodlí a zkrácení.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

Použití `var` pomáhá zjednodušit váš kód, ale jeho použití by mělo být omezeno na případy, kde je vyžadováno, nebo když je váš kód čitelnější. Další informace o tom, kdy se má `var` správně používat, najdete v části [implicitní zadání místních proměnných](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) v článku pokyny pro kódování v jazyce C#.

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../../language-reference/index.md)
- [Implicitně typovaná pole](../arrays/implicitly-typed-arrays.md)
- [Jak používat implicitně typované lokální proměnné a pole ve výrazu dotazu](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Anonymní typy](anonymous-types.md)
- [Inicializátory objektu a kolekce](object-and-collection-initializers.md)
- [Proměnná](../../language-reference/keywords/var.md)
- [LINQ v jazyku C#](../../linq/index.md)
- [LINQ (jazykově integrovaný dotaz)](../../linq/index.md)
- [pro](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
