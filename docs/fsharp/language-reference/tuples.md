---
title: Řazené kolekce členů (F#)
description: 'Další informace o F # záznam, seskupení nepojmenované ale seřazené hodnoty, může být různých typů.'
ms.date: 05/16/2016
ms.openlocfilehash: e7628e4c4b538c2fe52fca25d2597b10fec28d1c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43749220"
---
# <a name="tuples"></a>Řazené kolekce členů

A *řazené kolekce členů* je seskupení nepojmenované ale seřazené hodnoty, může být různých typů.  Řazené kolekce členů může být buď referenční typy a struktury.

## <a name="syntax"></a>Syntaxe

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Poznámky

Každý *element* v předchozí syntaxi, může být libovolný platný výraz F #.

## <a name="examples"></a>Příklady

Příklady řazených kolekcí členů: dvojice, trojic a tak dále, stejných nebo různých typů. Některé příklady jsou znázorněné v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>Získání jednotlivých hodnot

Můžete porovnávání vzorů pro přístup k a přiřadit názvy elementů řazené kolekce členů, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Můžete také dekonstruovat řazené kolekce členů přes porovnávání vzorů mimo `match` výraz prostřednictvím `let` vazby:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Nebo můžete vzorku odpovídají na řazené kolekce členů jako vstupy do funkce:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Pokud potřebujete pouze jeden prvek řazené kolekce členů, zástupný znak (podtržítko) lze se vyhnout, vytvářet nový název pro hodnotu, která není nutné.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Zkopírování prvků z řazené kolekce členů odkazu do řazené kolekce členů struktury je také jednoduchý:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

Funkce `fst` a `snd` (odkazovat jenom řazených kolekcí členů) vrátí první a druhý elementů řazené kolekce členů, v uvedeném pořadí.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Neexistuje žádná integrované funkce, která vrací třetího prvku pole s trojitými, ale jeden takto snadno zápisu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Obecně je vhodnější použít porovnávání vzorů pro přístup k prvkům jednotlivé řazené kolekce členů.

## <a name="using-tuples"></a>Použití řazených kolekcí členů

Řazené kolekce členů poskytují pohodlný způsob, jak vrátit více hodnot z funkce, jak je znázorněno v následujícím příkladu. V tomto příkladu provede dělení celého čísla a vrátí zaokrouhlené výsledek operace jako první člen pár řazené kolekce členů a zbytek jako druhý člen, které odpovídá páru licencí.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Řazené kolekce členů můžete také použít jako argumenty funkce chcete se vyhnout implicitní curryfikaci argumentů funkce, které je vyjádřena pomocí syntaxe běžné funkce.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

Běžné syntaxi pro definici funkce `let sum a b = a + b` vám umožní definovat funkci, která je částečné použití argumentů prvního argumentu funkce, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Pomocí řazené kolekce členů jako parametr zakáže curryfikace. Další informace najdete v části "Částečné použití argumentů" v [funkce](functions/index.md).

## <a name="names-of-tuple-types"></a>Názvy typů pro řazené kolekce členů

Při psaní název typu, který je řazená kolekce členů je použít `*` k oddělování elementů symbol. Pro n-tice, která se skládá `int`, `float`a `string`, jako například `(10, 10.0, "ten")`, typu by byla zapsána následujícím způsobem.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Vzájemná spolupráce s řazenými kolekcemi členů jazyka C#

C# 7.0 seznámili s řazenými kolekcemi členů jazyka.  Řazené kolekce členů v C# jsou struktury a je stejná u strukturovaných řazených kolekcí členů v jazyce F #.  Pokud potřebujete zajistit vzájemnou funkční spolupráci s jazykem C#, je nutné použít strukturovaných řazených kolekcí členů.

To je jednoduché.  Představte si například, že je nutné předat řazené kolekce členů třídy C# a jeho výsledek, který je zároveň řazené kolekce členů je pak využívat:

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

V kódu F # můžete poté předat řazené kolekce členů struktury jako parametr a využívat výsledek v podobě řazené kolekce členů struktury.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Převod mezi řazené kolekce členů odkazů a strukturovaných řazených kolekcí členů

Protože řazené kolekce členů odkazů a strukturovaných řazených kolekcí členů mají úplně jiné základní reprezentaci, nejsou implicitně převoditelné.  To znamená nebude kompilovat kód například následující:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Třeba vzor odpovídající jedna n-tice a druhý s základní části vytvořit.  Příklad:

[!code-fsharp[Main](../../../samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Zkompilovaná forma řazené kolekce členů odkazů

Tato část vysvětluje formě řazené kolekce členů, když jsou kompilovány.  Tyto informace tady není nutné číst, pokud se zaměřujete na rozhraní .NET Framework 3.5 nebo nižší.

Řazené kolekce členů jsou kompilovány do jednoho z několika obecných typů všechny pojmenované objekty `System.Tuple`, které jsou přetížené Arita nebo počtu parametrů typu. Při zobrazení z jiného jazyka, jako je C# nebo Visual Basic, nebo pokud používáte nástroj, který nemá žádné informace o konstrukce jazyka F # se zobrazí typy řazené kolekce členů v tomto formuláři. `Tuple` Typy byly zavedeny v rozhraní .NET Framework 4. Pokud se zaměřujete na starší verzi rozhraní .NET Framework, kterou kompilátor používá verze [System.Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z 2.0 verze základní knihovny F #. Typy v této knihovně se používají pouze pro aplikace, které se zaměřují 2.0, 3.0 a 3.5 verze rozhraní .NET Framework. Předávání typů slouží k zajištění binární kompatibilitu mezi komponenty rozhraní .NET Framework 2.0 a .NET Framework 4 F #.

### <a name="compiled-form-of-struct-tuples"></a>Zkompilovaná forma strukturovaných řazených kolekcí členů

Strukturovaných řazených kolekcí členů (například `struct (x, y)`), jsou v podstatě totéž řazené kolekce členů odkazů.  Jsou zkompilovány do <xref:System.ValueTuple> typ přetížení Arita nebo počet parametrů typu.  Jsou ekvivalentní [jazyka C# 7.0 řazených kolekcí členů](../../csharp/tuples.md) a [jazyka Visual Basic 2017 řazených kolekcí členů](../../visual-basic/programming-guide/language-features/data-types/tuples.md)a zajistit vzájemnou funkční spolupráci obousměrně.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Typy F#](fsharp-types.md)
