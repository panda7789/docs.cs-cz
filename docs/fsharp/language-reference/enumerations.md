---
title: Výčty
description: Naučte se používat F# výčty namísto literálů, aby bylo možné čitelnější a udržovatelnější kód.
ms.date: 05/16/2016
ms.openlocfilehash: 784cd9612b199e4648bb64432d3b4422ad35f649
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630347"
---
# <a name="enumerations"></a>Výčty

*Výčty*, označované takéjako výčty, představují celočíselné typy, kde jsou popisky přiřazeny podmnožině hodnot. Můžete je použít místo literálů, aby bylo možné čitelnější a udržovatelnější kód.

## <a name="syntax"></a>Syntaxe

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Poznámky

Výčet vypadá podobně jako rozlišené sjednocení, které má jednoduché hodnoty, s výjimkou toho, že je možné zadat hodnoty. Hodnoty jsou obvykle celá čísla, která začínají na 0 nebo 1 nebo celá čísla, která představují bitové pozice. Pokud je výčet určen pro reprezentace bitových pozic, měli byste také použít atribut [Flags](xref:System.FlagsAttribute) .

Podkladový typ výčtu je určen z literálu, který je použit, takže lze například použít literály s příponou, například `1u`, `2u`a tak dále, pro typ unsigned integer (`uint32`).

Když odkazujete na pojmenované hodnoty, je nutné použít název vlastního typu výčtu jako kvalifikátor, to znamená `enum-name.value1`, ne pouze. `value1` Toto chování se liší od v případě rozlišených sjednocení. Je to proto, že výčty mají vždy atribut [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) .

Následující kód ukazuje deklaraci a použití výčtu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Výčty lze snadno převést na podkladový typ pomocí příslušného operátoru, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

`sbyte`Výčtové typy mohou mít jeden z následujících základních typů:, `uint16` `uint32` `int64` `uint16` `int16` `byte`, `int32` ,,`uint64`,,,, a. `char` Výčtové typy jsou reprezentovány v .NET Framework jako typy, které `System.Enum`jsou zděděny z, který je `System.ValueType`zase zděděn z. Proto jsou typy hodnot, které jsou umístěny v zásobníku nebo vloženy do obsahujícího objektu, a libovolná hodnota základního typu je platná hodnota výčtu. To je důležité v případě porovnávání vzorů s hodnotami výčtu, protože je nutné zadat vzor, který zachytává nepojmenované hodnoty.

Funkce v F# knihovně může být použita k vygenerování hodnoty výčtu, dokonce i jiné hodnoty než jedné z předdefinovaných pojmenovaných hodnot. `enum` `enum` Funkci použijete následujícím způsobem.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

Výchozí `enum` funkce funguje s typem `int32`. Proto jej nelze použít s výčtovým typem, které mají jiné základní typy. Místo toho použijte následující příkaz.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

Kromě toho jsou případy vydaných výčty vždy `public`generovány jako. To je tak, že se zarovnají s C# a zbytkem platformy .NET.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
- [Přetypování a převody](casting-and-conversions.md)
