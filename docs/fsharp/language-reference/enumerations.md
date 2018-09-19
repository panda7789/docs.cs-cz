---
title: Výčty (F#)
description: 'Další informace o použití výčty F # místo literály, aby byl kód čitelnější a udržovatelný.'
ms.date: 05/16/2016
ms.openlocfilehash: 47fb353c2698f8b1474834ebbd1b0eff2c7f76e7
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46003162"
---
# <a name="enumerations"></a>Výčty

*Výčty*, označované také jako *výčty*,, jsou celočíselných typů, kde popisky jsou přiřazeny k podmnožině hodnoty. Můžete je použít místo literály aby byl kód čitelnější a udržovatelný.

## <a name="syntax"></a>Syntaxe

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Poznámky

Výčet vypadá podobně jako diskriminované sjednocení, který má jednoduché hodnoty, s tím rozdílem, že můžete zadat hodnoty. Hodnoty jsou obvykle celých čísel, které začínají 0 nebo 1 nebo celých čísel představujících bitové pozice. Pokud výčet slouží k reprezentaci bitové pozice, měli byste také použít [příznaky](xref:System.FlagsAttribute) atribut.

Základní typ výčtu je určen z literál, který se používá, takže například můžete použít literály s příponou, jako například `1u`, `2u`, a tak dále pro celé číslo bez znaménka (`uint32`) typu.

Při odkazování na pojmenované hodnoty, musíte použít název samotného typu výčtu jako kvalifikátoru, tedy `enum-name.value1`, nejen `value1`. Toto chování se liší od rozlišovaná sjednocení. Důvodem je, že výčty mají vždy [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atribut.

Následující kód ukazuje deklaraci a užívání výčet.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Jak je znázorněno v následujícím kódu, můžete snadno převést výčty pro základní typ pomocí příslušného operátoru.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Výčtové typy může mít jednu z následujících typů základní: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, a `char`. Typy výčtu jsou reprezentovány v rozhraní .NET Framework jako typy, které jsou zděděny z `System.Enum`, pak dědí se ze `System.ValueType`. Proto jsou typy hodnot, které jsou umístěny na zásobník nebo vloženého do nadřazeného objektu a platná hodnota výčtu je libovolná hodnota základního typu. To je důležité, když vzorec pro porovnávání na výčet hodnot, protože je nutné zadat vzor, který zachytává nepojmenovaných hodnot.

`enum` Funkce v knihovně F # lze použít ke generování hodnoty výčtu, dokonce i jiná hodnota než jeden z předdefinovaných, s názvem hodnoty. Můžete použít `enum` funkce následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

Výchozí hodnota `enum` funkce pracuje s typem `int32`. Proto jej nelze použít s výčtové typy, které mají jiné základní typy. Místo toho použijte následující.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

Kromě toho případech pro výčty jsou vždy generované jako `public`. Je to tak, aby jejich zarovnání bylo pomocí C# a zbytek na platformě .NET.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Přetypování a převody](casting-and-conversions.md)
