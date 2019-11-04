---
title: Implicitně typované lokální proměnné – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#]
- var [C#]
ms.assetid: b9218fb2-ef5d-4814-8a8e-2bc29b0bbc9b
ms.openlocfilehash: 7010c38797ab64e5106c96c06cd814c143ca9c24
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419378"
---
# <a name="implicitly-typed-local-variables-c-programming-guide"></a>Implicitně typované lokální proměnné (C# Průvodce programováním)

Lokální proměnné lze deklarovat bez poskytnutí explicitního typu. Klíčové slovo `var` instruuje kompilátor, aby odvodí typ proměnné z výrazu na pravé straně příkazu inicializace. Odvozený typ může být vestavěný typ, anonymní typ, uživatelsky definovaný typ nebo typ definovaný v knihovně tříd .NET Framework. Další informace o tom, jak inicializovat pole pomocí `var`, naleznete v tématu [implicitně typované pole](../arrays/implicitly-typed-arrays.md).

Následující příklady znázorňují různé způsoby, jak lze pomocí `var`deklarovat místní proměnné:

[!code-csharp[csProgGuideLINQ#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#43)]

Je důležité pochopit, že klíčové slovo `var` neznamená "variantu" a neindikuje, že proměnná je volně zadaná nebo má pozdní vazbu. Pouze to znamená, že kompilátor určí a přiřadí nejvhodnější typ.

Klíčové slovo `var` může být použito v následujících kontextech:

- Na místních proměnných (proměnné deklarované v oboru metody), jak je znázorněno v předchozím příkladu.

- V příkazu [for](../../language-reference/keywords/for.md) Initialization.

    ```csharp
    for(var x = 1; x < 10; x++)
    ```

- V příkazu [foreach](../../language-reference/keywords/foreach-in.md) Initialization.

    ```csharp
    foreach(var item in list){...}
    ```

- V příkazu [using](../../language-reference/keywords/using-statement.md) .

    ```csharp
    using (var file = new StreamReader("C:\\myfile.txt")) {...}
    ```

Další informace najdete v tématu [Postupy: použití implicitního typu lokálních proměnných a polí ve výrazu dotazu](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md).

## <a name="var-and-anonymous-types"></a>var a anonymní typy

V mnoha případech je použití `var` volitelné a je pouze syntaktické pohodlí. Nicméně pokud je proměnná inicializována pomocí anonymního typu, je nutné deklarovat proměnnou jako `var`, pokud potřebujete získat přístup k vlastnostem objektu v pozdějším bodě. Toto je běžný scénář v [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] výrazy dotazů. Další informace najdete v tématu [anonymní typy](anonymous-types.md).

Z perspektivy zdrojového kódu nemá anonymní typ žádný název. Proto pokud byla proměnná dotazu inicializována pomocí `var`, pak jediným způsobem, jak získat přístup k vlastnostem v vrácené sekvenci objektů, je použití `var` jako typ proměnné iterace v příkazu `foreach`.

[!code-csharp[csProgGuideLINQ#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#44)]

## <a name="remarks"></a>Poznámky

Následující omezení platí pro implicitně typové deklarace proměnných:

- `var` lze použít pouze v případě, že je místní proměnná deklarována a inicializována v rámci stejného příkazu; proměnnou nelze inicializovat na hodnotu null nebo do skupiny metod nebo do anonymní funkce.

- `var` nelze použít pro pole v oboru třídy.

- Proměnné deklarované pomocí `var` nelze použít ve výrazu inicializace. Jinými slovy je tento výraz právní`: int i = (i = 20);`, ale tento výraz vytvoří chybu při kompilaci: `var i = (i = 20);`

- V rámci stejného příkazu nelze inicializovat více proměnných s implicitním typem.

- Pokud je typ s názvem `var` v oboru, pak bude klíčové slovo `var` přeloženo na tento název typu a nebude zpracováno jako součást implicitně typové deklarace lokální proměnné.

Implicitní zadání pomocí klíčového slova `var` lze použít pouze pro proměnné v oboru místních metod. Implicitní psaní není k dispozici pro pole třídy, C# protože by Kompilátor narazil na logické rozhraní Paradox při zpracování kódu: kompilátor musí znát typ pole, ale nemůže určit typ, dokud není výraz přiřazení analyzován. výraz nelze vyhodnotit bez znalosti typu. Vezměte v úvahu následující kód:

```csharp
private var bookTitles;
```

`bookTitles` je pole třídy pro daný typ `var`. Vzhledem k tomu, že pole nemá žádný výraz k vyhodnocení, není možné, aby kompilátor odvodit, jaký typ `bookTitles` by měl být. Kromě toho je také nedostatečné Přidání výrazu do pole (například pro místní proměnnou):

```csharp
private var bookTitles = new List<string>();
```

Když kompilátor narazí na pole během kompilování kódu, zaznamenává typ každého pole před zpracováním jakýchkoli výrazů, které jsou k němu přidruženy. Kompilátor narazí na stejný Paradox, který se pokouší analyzovat `bookTitles`: musí znát typ pole, ale kompilátor obvykle určí `var`typ analýzou výrazu, který není možné bez vědomí typu předem.

Může se stát, že `var` mohou být užitečné také s výrazy dotazu, ve kterých je obtížné určit přesný konstruovaný typ proměnné dotazu. K tomu může dojít při operacích seskupování a řazení.

Klíčové slovo `var` může být užitečné také v případě, že konkrétní typ proměnné je únavné pro psaní na klávesnici nebo je zřejmá nebo nepřidává k čitelnosti kódu. Jeden příklad, kde je `var` užitečné tímto způsobem, je s vnořenými obecnými typy, jako jsou ty, které se používají při operacích skupiny. V následujícím dotazu je typ proměnné dotazu `IEnumerable<IGrouping<string, Student>>`. Pokud vy a ostatní uživatelé, kteří musí tento kód pochopit, neexistují žádné potíže s používáním implicitního zadávání pro pohodlí a zkrácení.

[!code-csharp[cscsrefQueryKeywords#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Group.cs#13)]

Použití `var` však má alespoň potenciál, aby bylo obtížné pochopit kód pro jiné vývojáře. V C# takovém případě dokumentace obecně používá `var` jenom v případě, že je to potřeba.

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../../language-reference/index.md)
- [Implicitně typovaná pole](../arrays/implicitly-typed-arrays.md)
- [Postupy: Použití implicitně typovaných lokálních proměnných a polí ve výrazu dotazu.](how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression.md)
- [Anonymní typy](anonymous-types.md)
- [Inicializátory objektu a kolekce](object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [LINQ (jazykově integrovaný dotaz)](../../linq/index.md)
- [for](../../language-reference/keywords/for.md)
- [foreach, in](../../language-reference/keywords/foreach-in.md)
- [using – příkaz](../../language-reference/keywords/using-statement.md)
