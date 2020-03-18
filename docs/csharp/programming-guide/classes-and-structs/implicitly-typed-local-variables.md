---
title: Implicitně zadané místní proměnné – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: d39e4c4dd180ba35b7555d61211a34d696b04f50
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399824"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Implicitně zadané místní proměnné (Průvodce programováním jazyka C#)

Místní proměnné lze deklarovat bez zadání explicitního typu. Klíčové `var` slovo pokyn kompilátorododu odvodit typ proměnné z výrazu na pravé straně příkazu inicializace. Odvozený typ může být vestavěný typ, anonymní typ, uživatelem definovaný typ nebo typ definovaný v knihovně tříd rozhraní .NET Framework. Další informace o inicializaci polí `var`pomocí naleznete [v tématu Implicitně zadaný pole](../arrays/implicitly-typed-arrays.md).

Následující příklady ukazují různé způsoby, kterými `var`lze deklarovat místní proměnné pomocí :

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

Je důležité si uvědomit, že `var` klíčové slovo neznamená "varianta" a neznamená, že proměnná je volně zadaný nebo pozdní vázaný. To jen znamená, že kompilátor určuje a přiřadí nejvhodnější typ.

Klíčové `var` slovo lze použít v následujících kontextech:

- Na místní proměnné (proměnné deklarované v oboru metody), jak je znázorněno v předchozím příkladu.

- V příkazu [for](../../language-reference/keywords/for.md) inicializace.

    ```csharp
    for (var x = 1; x < 10; x++)
    ```

- V [příkazu foreach](../../language-reference/keywords/foreach-in.md) inicializace.

    ```csharp
    foreach (var item in list) {...}
    ```

- V [using](../../language-reference/keywords/using-statement.md) prohlášení.

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Další informace naleznete v tématu [Použití implicitně zadávaných místních proměnných a polí ve výrazu dotazu](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).

## <a name="var-and-anonymous-types"></a>var a anonymní typy

V mnoha případech `var` je použití je volitelné a je jen syntaktické pohodlí. Pokud je však proměnná inicializována s `var` anonymním typem, musíte deklarovat proměnnou, jako byste potřebovali přístup k vlastnostem objektu později. Toto je běžný scénář ve výrazech dotazu LINQ. Další informace naleznete [v tématu Anonymní typy](anonymous-types.md).

Z hlediska zdrojového kódu anonymní typ nemá žádný název. Proto pokud proměnná dotazu byla `var`inicializována s , pak jediný způsob, `var` jak získat přístup k vlastnostem v vrácené posloupnosti objektů je použít jako typ iterace proměnné v příkazu. `foreach`

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Poznámky

Následující omezení platí pro implicitně zadané deklarace proměnných:

- `var`lze použít pouze v případě, že je místní proměnná deklarována a inicializována ve stejném příkazu; proměnnou nelze inicializovat na hodnotu null nebo na skupinu metod nebo anonymní funkci.

- `var`nelze použít v polích v oboru třídy.

- Proměnné deklarované pomocí `var` nelze použít ve výrazu inicializace. Jinými slovy, tento výraz `int i = (i = 20);` je legální: ale tento výraz vytváří chybu v době kompilace:`var i = (i = 20);`

- Více implicitně zadaných proměnných nelze inicializovat ve stejném příkazu.

- Pokud je `var` typ pojmenovaný v `var` oboru, bude klíčové slovo přeložit na tento název typu a nebude považováno za součást implicitně zadané deklarace místní proměnné.

Implicitní psaní `var` pomocí klíčového slova lze použít pouze na proměnné v oboru místní metody. Implicitní psaní není k dispozici pro pole třídy jako kompilátor Jazyka C# by dojít k logickému paradoxu, protože zpracovává kód: kompilátor potřebuje znát typ pole, ale nemůže určit typ, dokud je analyzován výraz přiřazení a výraz nelze vyhodnotit bez znalosti typu. Uvažujte následující kód:

```csharp
private var bookTitles;
```

`bookTitles`je pole třídy `var`s typem . Vzhledem k tomu, že pole nemá žádný výraz k vyhodnocení, je nemožné, aby kompilátor odvodil, jaký typ `bookTitles` má být. Kromě toho přidání výrazu do pole (stejně jako u místní proměnné) je také nedostatečné:

```csharp
private var bookTitles = new List<string>();
```

Když kompilátor narazí na pole během kompilace kódu, zaznamená typ každého pole před zpracováním všech výrazů, které jsou k němu přidruženy. Kompilátor narazí na stejný paradox `bookTitles`při pokusu o analýzu : potřebuje znát typ `var`pole, ale kompilátor by normálně určit 's typ analýzou výrazu, který není možné bez znalosti typu předem.

Můžete zjistit, `var` že může být také užitečné s výrazy dotazu, ve kterém je obtížné určit přesný typ konstruované proměnné dotazu. K tomu může dojít při seskupování a řazení operací.

Klíčové `var` slovo může být také užitečné, pokud je konkrétní typ proměnné zdlouhavý pro psaní na klávesnici, nebo je zřejmý nebo nepřidává k čitelnosti kódu. Jeden příklad, kde `var` je užitečné tímto způsobem je s vnořené obecné typy, jako jsou ty, které se používají s operacemi skupiny. V následujícím dotazu je `IEnumerable<IGrouping<string, Student>>`typ proměnné dotazu . Tak dlouho, dokud vy a ostatní, kteří musí udržovat váš kód pochopit, není žádný problém s použitím implicitní psaní pro pohodlí a stručnost.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

Použití `var` pomáhá zjednodušit kód, ale jeho použití by mělo být omezeno na případy, kde je požadováno, nebo když usnadňuje čtení kódu. Další informace o tom, kdy správně používat, `var` naleznete v části [Implicitně zadané místní proměnné](../inside-a-program/coding-conventions.md#implicitly-typed-local-variables) v článku C# Coding Guidelines.

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../../language-reference/index.md)
- [Implicitně typovaná pole](../arrays/implicitly-typed-arrays.md)
- [Použití implicitně zadávaných místních proměnných a polí ve výrazu dotazu](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Anonymní typy](anonymous-types.md)
- [Inicializátory objektu a kolekce](object-and-collection-initializers.md)
- [Var](../../language-reference/keywords/var.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [LINQ (dotaz integrovaný jazykem)](../../linq/index.md)
- [Pro](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
