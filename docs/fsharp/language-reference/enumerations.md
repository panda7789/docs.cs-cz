---
title: Výčty (F#)
description: 'Další informace o použití výčty F # místo literály, aby váš kód více čitelný a udržovatelný.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 4b1a61fb69403f826733893667e55991d39867c6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="enumerations"></a>Výčty

*Výčty*, také známé jako *výčty*,, jsou celočíselné typy, kde se popisky přiřazené k podmnožině hodnoty. Můžete je používat místo literály, aby kód víc čitelný a udržovatelný.


## <a name="syntax"></a>Syntaxe

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Poznámky
Výčet vypadá podobně jako rozlišovaná sjednocení, která má jednoduché hodnoty, s tím rozdílem, že lze zadat hodnoty. Hodnoty jsou obvykle celá čísla, které začínají 0 nebo 1 nebo celá čísla, které představují bit pozic. Pokud výčet slouží k reprezentaci pozic bit, byste měli použít také [příznaky](xref:System.FlagsAttribute) atribut.

Základní typ výčtu je určit literál, který se používá, takže například můžete použít literály s příponou, jako například `1u`, `2u`a tak dále pro celé číslo bez znaménka (`uint32`) typu.

Když odkazujete na pojmenovaných hodnot, musíte použít název typu výčtu sám sebe jako kvalifikátor, který je `enum-name.value1`, ne jenom `value1`. Toto chování se liší od rozlišovaná sjednocení. Důvodem je, že výčty vždy k dispozici [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atribut.

Následující kód ukazuje deklarace a používání výčtu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Můžete snadno převést výčty základní typ pomocí příslušné operátor, jak je znázorněno v následujícím kódu.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Výčtové typy může mít jeden z následujících typů základní: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, a `char`. Výčtové typy jsou vyjádřené v rozhraní .NET Framework typy, které se dědí z `System.Enum`, který je pak zděděno od `System.ValueType`. Proto jsou typy hodnot, které jsou umístěny v zásobníku nebo vložené v objekt obsahující a hodnotou základní typ není platná hodnota výčtu. To je důležité při porovnávání se na výčet hodnot, protože je nutné zadat vzor, který zachytí nepojmenované hodnoty.

`enum` Funkce knihovny F # lze použít ke generování hodnotou výčtu, i jiná hodnota než jeden z předdefinovaných, s názvem hodnoty. Můžete použít `enum` funkce následujícím způsobem.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

Výchozí hodnota `enum` funkce funguje s typem `int32`. Proto jej nelze použít s výčtové typy, které mají jiné základní typy. Místo toho použijte následující.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]
    
## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)

[Přetypování a převody](casting-and-conversions.md)
