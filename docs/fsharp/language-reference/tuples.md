---
title: N-tice
description: 'Přečtěte si o řazené kolekci členů F #, seskupení nepojmenovaných, ale seřazených hodnot, případně různých typů.'
ms.date: 05/16/2016
ms.openlocfilehash: 5d26fd5d7ec5b4939a895a6d2a6a0d7fc6c6c733
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173286"
---
# <a name="tuples"></a>N-tice

*Řazená kolekce členů* je seskupení nepojmenovaných, ale seřazených hodnot, případně různých typů.  Řazené kolekce členů můžou být buď odkazy na typy nebo struktury.

## <a name="syntax"></a>Syntaxe

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Poznámky

Každý *prvek* v předchozí syntaxi může být libovolný platný výraz F #.

## <a name="examples"></a>Příklady

Příklady řazených kolekcí členů obsahují páry, tři a tak dále, stejného nebo různých typů. Některé příklady jsou znázorněny v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L6-L21)]

## <a name="obtaining-individual-values"></a>Získání individuálních hodnot

Můžete použít porovnávání vzorů k přístupu a přiřazování názvů prvků řazené kolekce členů, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L27-L29)]

Můžete také dekonstruovat řazenou kolekci členů prostřednictvím porovnávání vzorů mimo `match` výraz prostřednictvím `let` vazby:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L34-L37)]

Nebo můžete porovnávání vzorů u řazených kolekcí členů, jako jsou vstupy funkcí:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L43-L47)]

Pokud potřebujete pouze jeden prvek řazené kolekce členů, zástupný znak (podtržítko) lze použít k zamezení vytváření nového názvu pro hodnotu, kterou nepotřebujete.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L53-L54)]

Kopírování elementů z referenční řazené kolekce členů do struktury řazené kolekce členů je také jednoduché:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L62-L66)]

Funkce `fst` a `snd` (pouze řazené kolekce členů) vrací první a druhý prvek řazené kolekce členů v uvedeném pořadí.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L72-L73)]

Neexistuje žádná předdefinovaná funkce, která vrací třetí prvek trojnásobku, ale lze ji snadno napsat následujícím způsobem.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L78-L78)]

Obecně je vhodnější použít porovnávání vzorů pro přístup k jednotlivým prvkům řazené kolekce členů.

## <a name="using-tuples"></a>Použití řazených kolekcí členů

Řazené kolekce členů poskytují pohodlný způsob, jak vrátit více hodnot z funkce, jak je znázorněno v následujícím příkladu. Tento příklad provádí celočíselné dělení a vrací zaoblený výsledek operace jako první člen dvojice řazené kolekce členů a zbytek jako druhý člen dvojice.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L83-L86)]

Řazené kolekce členů lze také použít jako argumenty funkce, pokud chcete zabránit implicitním procesu curryfikace argumentů funkce, které jsou odvozeny pomocí obvyklé syntaxe funkce.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L88-L88)]

Obvyklá syntaxe pro definování funkce `let sum a b = a + b` umožňuje definovat funkci, která je částečnou aplikací prvního argumentu funkce, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/basic-examples.fsx#L90-L94)]

Použití řazené kolekce členů jako parametru zakáže procesu curryfikace. Další informace naleznete v části "částečné použití argumentů" ve [funkcích Functions](./functions/index.md).

## <a name="names-of-tuple-types"></a>Názvy typů řazené kolekce členů

Když napíšete název typu, který je řazené kolekce členů, použijete `*` symbol k oddělení prvků. V případě řazené kolekce členů, která se skládá z, a, jako je `int` `float` `string` `(10, 10.0, "ten")` typ, by byl zápis typu následující.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Spolupráce s řazenými kolekcemi členů jazyka C#

Jazyk C# 7,0 představil do jazyka řazené kolekce členů.  Řazené kolekce členů v jazyce C# jsou struktury a jsou ekvivalentní k řazeným kolekcím členů struktury v F #.  Pokud potřebujete pracovat s jazykem C#, je nutné použít řazené kolekce členů struktury.

To je snadné.  Představte si například, že musíte předat řazenou kolekci členů ke třídě jazyka C# a pak využít svůj výsledek, což je také řazená kolekce členů:

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

V kódu F # pak můžete předat řazenou kolekci členů struktury jako parametr a využít výsledek jako řazenou kolekci členů struktury.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Převod mezi řazenými kolekcemi členů a řazenými kolekcemi členů struktury

Vzhledem k tomu, že řazené kolekce členů a řazené kolekce členů mají zcela odlišnou základní reprezentaci, nejsou implicitně převoditelné.  To znamená, že kód jako následující nebude zkompilován:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Je nutné porovnávání vzorů u jedné řazené kolekce členů a vytvořit druhé s částmi prvků.  Například:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Kompilovaná forma řazených kolekcí členů odkazu

Tato část vysvětluje formu řazených kolekcí členů při jejich kompilaci.  Pokud necílíte .NET Framework 3,5 nebo nižší, nemusíte informace číst.

Řazené kolekce členů jsou kompilovány do objektů jednoho z několika obecných typů, všech pojmenovaných `System.Tuple` , které jsou přetíženy na aritou nebo podle počtu parametrů typu. Typy řazené kolekce členů se zobrazí v tomto formuláři, když je zobrazíte z jiného jazyka, jako je například C# nebo Visual Basic, nebo pokud používáte nástroj, který nemá informace o konstrukcích F #. `Tuple`Typy byly představeny v .NET Framework 4. Pokud cílíte na starší verzi .NET Framework, kompilátor použije verze [System. Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z verze 2,0 základní knihovny F #. Typy v této knihovně jsou používány pouze pro aplikace, které cílí na verze .NET Framework 2,0, 3,0 a 3,5. Přesměrování typu se používá k zajištění binární kompatibility mezi .NET Framework 2,0 a .NET Framework 4 součásti F #.

### <a name="compiled-form-of-struct-tuples"></a>Kompilovaná forma řazených kolekcí členů struktury

Řazené kolekce členů struktury (například `struct (x, y)` ) jsou zásadním rozdílem od řazených kolekcí členů odkazu.  Jsou zkompilovány do <xref:System.ValueTuple> typu, přetíženy pomocí aritou nebo počtu parametrů typu.  Jsou ekvivalentní k [řazené kolekci členů C# 7,0](../../csharp/language-reference/builtin-types/value-tuples.md) a [Visual Basic 2017 řazené kolekce členů](../../visual-basic/programming-guide/language-features/data-types/tuples.md)a pracují obousměrně.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Typy F#](fsharp-types.md)
