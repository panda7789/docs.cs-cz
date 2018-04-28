---
title: Řazené kolekce členů (F#)
description: 'Další informace o F # tuple, seskupení nepojmenované ale seřazené hodnoty, které by mohly mít různých typů.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 9710f4996a952fdeaab07a30916215f27969e1a3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="tuples"></a>Řazené kolekce členů

A *řazené kolekce členů* je seskupení nepojmenované ale seřazené hodnoty, které by mohly mít různých typů.  Řazené kolekce členů může být buď odkazové typy nebo struktury.

## <a name="syntax"></a>Syntaxe

```fsharp
(element, ... , element)
struct(element, ... ,element )
```
## <a name="remarks"></a>Poznámky
Každý *element* v předchozí syntaxi, může být jakýkoli platný výraz F #.

## <a name="examples"></a>Příklady
Řazené kolekce členů příklady páry, triples a tak dále, stejné nebo různých typů. Některé příklady jsou znázorněné v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]
    
## <a name="obtaining-individual-values"></a>Získání jednotlivých hodnot
Můžete porovnávání vzorů pro přístup a přiřadit názvy elementů řazené kolekce členů, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Můžete také deconstruct řazené kolekce členů prostřednictvím shoda vzoru mimo `match` výraz prostřednictvím `let` vazby:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Nebo můžete vzor shodného řazených kolekcí členů jako vstupy do funkce:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Pokud budete potřebovat pouze jeden element řazenou kolekci členů, zástupný znak (podtržítko) slouží k Vyhněte se vytváření nový název pro hodnotu, která není nutné.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Kopírování prvků z odkazu řazené kolekce členů do struktura řazené kolekce členů je také jednoduchý:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

Funkce `fst` a `snd` (odkazovat jenom řazených kolekcí členů) vrátí první a druhé elementy řazené kolekce členů, v uvedeném pořadí.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Neexistuje žádné integrované funkce, která vrátí třetí elementu triple, ale jeden takto snadno zápisu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Obecně platí je lepší použít porovnávání vzorů pro přístup k elementům jednotlivých řazené kolekce členů.

## <a name="using-tuples"></a>Pomocí řazených kolekcí členů
Řazené kolekce členů poskytují pohodlný způsob, jak vrátit více hodnot z funkce, jak je znázorněno v následujícím příkladu. Tento příklad provede celočíselné dělení a vrátí zaokrouhlené výsledek operace jako první člen pár řazené kolekce členů a zbývající jako druhý člen, které odpovídá páru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Řazené kolekce členů můžete také použít jako argumenty funkce když budete chtít vyhnout implicitní currying argumenty funkce, které je zahrnuto v syntaxi obvyklé funkce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

Obvyklé syntaxi pro definování funkce `let sum a b = a + b` umožňuje definovat funkci, která je částečné aplikace prvního argumentu funkce, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Pomocí řazené kolekce členů jako parametr zakáže currying. Další informace najdete v tématu "Částečné aplikace argumenty" v [funkce](functions/index.md).

## <a name="names-of-tuple-types"></a>Názvy typů řazené kolekce členů
Při psaní název typu, který je řazené kolekce členů použijete `*` symbol jednotlivé prvky. Pro řazené kolekce členů, která se skládá z `int`, `float`a `string`, jako například `(10, 10.0, "ten")`, typ by byla zapsána následujícím způsobem.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Vzájemná spolupráce s řazenými kolekcemi členů C#

Pro jazyk C# 7.0 zavést řazené kolekce členů.  Řazené kolekce členů v jazyce C# jsou struktury a odpovídají struktura řazených kolekcí členů v F #.  Pokud potřebujete zajistit vzájemnou funkční spolupráci s C#, je nutné použít struktura řazené kolekce členů.

Toto je snadné provést.  Představte si například, že je nutné předat řazené kolekce členů třídy jazyka C# a pak využívat jeho výsledek, který je také řazené kolekce členů:

```csharp
namespace CSharpTupleInterop
{
    public static class Example
    {
        public static (int, int) AddOneToXAndY((int x, int y) a) =>
            (a.x + 1, a.y + 1);
    }
}
```

V F # kódu můžete pak předejte řazené kolekce členů struktura jako parametr a využívat výsledek v podobě struktura řazené kolekce členů.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Převod mezi odkaz řazených kolekcí členů a řazené kolekce členů – struktura

Protože odkaz řazených kolekcí členů a struktura řazených kolekcí členů mají základní znázornění úplně jiné, nejsou implicitně převést.  To znamená nebude kompilace kódu, například následující:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Musí vzor odpovídající na jeden záznam a ostatní části základní vytvořit.  Příklad:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Kompilované formuláře odkaz řazené kolekce členů
Tato část vysvětluje formu řazených kolekcí členů v případě, že se kompilují.  Zde uvedené informace není nezbytné pro čtení, pokud cílíte na rozhraní .NET Framework 3.5 nebo nižší.

Řazené kolekce členů kompilovány do jednoho z několika obecné typy všechny pojmenované objekty `System.Tuple`, která jsou přetížené na Arita nebo počet parametrů typu. Typy řazené kolekce členů se zobrazí v tomto formuláři, když zobrazujete v jiném jazyce, jako je například C# nebo Visual Basic nebo používáte nástroj, který nemá informace o konstrukce jazyka F #. `Tuple` Typy byly zavedeny v rozhraní .NET Framework 4. Pokud jsou cílení na dřívější verzi rozhraní .NET Framework, kompilátor použije verzích [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z verze 2.0 základní knihovny F #. Typy v této knihovně se používají pouze pro aplikace, které cílí 2.0, 3.0 a 3.5 verze rozhraní .NET Framework. Předávání typů slouží k zajištění binární kompatibilitu mezi jednotlivými součásti rozhraní .NET Framework 2.0 a .NET Framework 4 F #.

### <a name="compiled-form-of-struct-tuples"></a>Kompilované formuláře řazené kolekce členů – struktura

Struktura řazených kolekcí členů (například `struct (x, y)`), se zásadně liší od odkaz řazené kolekce členů.  Že se kompilují do <xref:System.ValueTuple> typu, přetížené Arita nebo počet parametrů typu.  Jsou ekvivalentní [C# 7.0 řazených kolekcí členů](../../csharp/tuples.md) a [jazyka Visual Basic 2017 řazených kolekcí členů](../../visual-basic/programming-guide/language-features/data-types/tuples.md)a zajistit vzájemnou funkční spolupráci obousměrně.

## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Typy F#](fsharp-types.md)
