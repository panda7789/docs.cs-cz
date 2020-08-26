---
title: Výčty
description: 'Naučte se používat výčty F # místo literálů, aby bylo možné čitelnější a udržovatelnější kód.'
ms.date: 08/15/2020
ms.openlocfilehash: 5f298691ce48a06c203930c7742cf007c819dc33
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812104"
---
# <a name="enumerations"></a>Výčty

*Výčty*, označované také jako *výčty*, představují celočíselné typy, kde jsou popisky přiřazeny podmnožině hodnot. Můžete je použít místo literálů, aby bylo možné čitelnější a udržovatelnější kód.

## <a name="syntax"></a>Syntax

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Poznámky

Výčet vypadá podobně jako rozlišené sjednocení, které má jednoduché hodnoty, s výjimkou toho, že je možné zadat hodnoty. Hodnoty jsou obvykle celá čísla, která začínají na 0 nebo 1 nebo celá čísla, která představují bitové pozice. Pokud je výčet určen pro reprezentace bitových pozic, měli byste také použít atribut [Flags](xref:System.FlagsAttribute) .

Podkladový typ výčtu je určen z literálu, který je použit, takže lze například použít literály s příponou, například `1u` , `2u` a tak dále, pro typ unsigned integer ( `uint32` ).

Když odkazujete na pojmenované hodnoty, je nutné použít název vlastního typu výčtu jako kvalifikátor, to znamená, `enum-name.value1` ne pouze `value1` . Toto chování se liší od v případě rozlišených sjednocení. Je to proto, že výčty mají vždy atribut [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html) .

Následující kód ukazuje deklaraci a použití výčtu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Výčty lze snadno převést na podkladový typ pomocí příslušného operátoru, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Výčtové typy mohou mít jeden z následujících základních typů: `sbyte` , `byte` , `int16` , `uint16` , `int32` , `uint32` , `int64` ,, a `uint16` `uint64` `char` . Výčtové typy jsou reprezentovány v .NET Framework jako typy, které jsou zděděny z `System.Enum` , který je zase zděděn z `System.ValueType` . Proto jsou typy hodnot, které jsou umístěny v zásobníku nebo vloženy do obsahujícího objektu, a libovolná hodnota základního typu je platná hodnota výčtu. To je důležité v případě porovnávání vzorů s hodnotami výčtu, protože je nutné zadat vzor, který zachytává nepojmenované hodnoty.

`enum`Funkce v knihovně F # může být použita k vygenerování hodnoty výčtu, dokonce i jiné hodnoty než jedné z předdefinovaných pojmenovaných hodnot. Funkci použijete následujícím `enum` způsobem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

Výchozí `enum` funkce funguje s typem `int32` . Proto jej nelze použít s výčtovým typem, které mají jiné základní typy. Místo toho použijte následující příkaz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

Kromě toho jsou případy vydaných výčty vždy generovány jako `public` . To je tak, že se zarovnají s jazykem C# a zbytkem platformy .NET.

## <a name="see-also"></a>Viz také

- [Referenční dokumentace jazyka F #](index.md)
- [Přetypování a převody](casting-and-conversions.md)
