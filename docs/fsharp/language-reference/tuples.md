---
title: N-tice
description: Přečtěte si F# o řazené kolekci členů, seskupení nepojmenovaných, ale seřazených hodnot, případně různých typů.
ms.date: 05/16/2016
ms.openlocfilehash: 7a15d7e0c6c9b42118dd75066f02cbb2e05335fc
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630236"
---
# <a name="tuples"></a>N-tice

*Řazená kolekce členů* je seskupení nepojmenovaných, ale seřazených hodnot, případně různých typů.  Řazené kolekce členů můžou být buď odkazy na typy nebo struktury.

## <a name="syntax"></a>Syntaxe

```fsharp
(element, ... , element)
struct(element, ... ,element )
```

## <a name="remarks"></a>Poznámky

Každý *prvek* v předchozí syntaxi může být libovolný platný F# výraz.

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

Funkce `fst` a`snd` (pouze řazené kolekce členů) vrací první a druhý prvek řazené kolekce členů v uvedeném pořadí.

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

Když napíšete název typu, který je řazené kolekce členů, použijete `*` symbol k oddělení prvků. V případě řazené kolekce členů, `int`která se `float`skládá z, `string` `(10, 10.0, "ten")`a, jako je typ, by byl zápis typu následující.

```fsharp
int * float * string
```

## <a name="interoperation-with-c-tuples"></a>Spolupráce s C# řazenými kolekcemi členů

C#7,0 zavedl do jazyka řazené kolekce členů.  Řazené kolekce C# členů v jsou struktury a jsou ekvivalentní k řazeným kolekcím F#členů struktury v.  Pokud potřebujete pracovat s nástrojem C#, je nutné použít řazené kolekce členů struktury.

To je snadné.  Představte si například, že musíte předat řazenou kolekci C# členů ke třídě a pak využít svůj výsledek, což je také řazená kolekce členů:

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

Ve vašem F# kódu pak můžete předat řazenou kolekci členů struktury jako parametr a využít výsledek jako řazenou kolekci členů struktury.

```fsharp
open TupleInterop

let struct (newX, newY) = Example.AddOneToXAndY(struct (1, 2))
// newX is now 2, and newY is now 3
```

### <a name="converting-between-reference-tuples-and-struct-tuples"></a>Převod mezi řazenými kolekcemi členů a řazenými kolekcemi členů struktury

Vzhledem k tomu, že řazené kolekce členů a řazené kolekce členů mají zcela odlišnou základní reprezentaci, nejsou implicitně převoditelné.  To znamená, že kód jako následující nebude zkompilován:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L5-L12)]

Je nutné porovnávání vzorů u jedné řazené kolekce členů a vytvořit druhé s částmi prvků.  Příklad:

[!code-fsharp[Main](~/samples/snippets/fsharp/tuples/interop.fsx#L18-L22)]

## <a name="compiled-form-of-reference-tuples"></a>Kompilovaná forma řazených kolekcí členů odkazu

Tato část vysvětluje formu řazených kolekcí členů při jejich kompilaci.  Pokud necílíte .NET Framework 3,5 nebo nižší, nemusíte informace číst.

Řazené kolekce členů jsou kompilovány do objektů jednoho z několika obecných typů, `System.Tuple`všech pojmenovaných, které jsou přetíženy na aritou nebo podle počtu parametrů typu. Typy řazené kolekce členů se zobrazí v tomto formuláři, když je zobrazíte z C# jiného jazyka, jako je například nebo Visual Basic, nebo pokud používáte nástroj, který F# nemá informace o konstrukcích. `Tuple` Typy byly představeny v .NET Framework 4. Pokud cílíte na starší verzi .NET Framework, kompilátor používá verze [System. Tuple](https://msdn.microsoft.com/library/5ac7953d-acdc-4a58-bfb7-c1f6406c0fa3) z verze 2,0 F# základní knihovny. Typy v této knihovně jsou používány pouze pro aplikace, které cílí na verze .NET Framework 2,0, 3,0 a 3,5. Přesměrování typu se používá k zajištění binární kompatibility mezi .NET Framework 2,0 a .NET Framework 4 F# komponentami.

### <a name="compiled-form-of-struct-tuples"></a>Kompilovaná forma řazených kolekcí členů struktury

Řazené kolekce členů struktury (například `struct (x, y)`) jsou zásadním rozdílem od řazených kolekcí členů odkazu.  Jsou zkompilovány do <xref:System.ValueTuple> typu, přetíženy pomocí aritou nebo počtu parametrů typu.  Jsou ekvivalentní k [ C# 7,0 řazených kolekcí členů](../../csharp/tuples.md) a [Visual Basic 2017 řazené kolekce členů](../../visual-basic/programming-guide/language-features/data-types/tuples.md)a spolupracují obousměrně.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Typy F#](fsharp-types.md)
