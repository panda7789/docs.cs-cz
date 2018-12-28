---
title: Literály
description: Seznamte se s typy literálu v F# programovací jazyk.
ms.date: 05/16/2016
ms.openlocfilehash: dfc02f0ff8ac3ad8600be5f3b6c9359f02bd25be
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612449"
---
# <a name="literals"></a>Literály

> [!NOTE]
> Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN (prozatím).

Toto téma obsahuje tabulku, která ukazuje, jak určit typ literály v F#.

## <a name="literal-types"></a>Typy literálu

Následující tabulka uvádí typy literálu v F#. Znaky, které představují číslice v šestnáctkové soustavě nerozlišují; znaky, které označují typ rozlišují malá a velká písmena.

|Typ|Popis|Přípona nebo předpona|Příklady|
|----|-----------|----------------|--------|
|sbyte|8bitové celé číslo se znaménkem|y|`86y`<br /><br />`0b00000101y`|
|byte|přirozené číslo bez znaménka 8 bitů|UY|`86uy`<br /><br />`0b00000101uy`|
|Int16|16bitové celé číslo se znaménkem|s|`86s`|
|UInt16|přirozené číslo bez znaménka 16 bitů|USA|`86us`|
|int<br /><br />int32|32bitové celé číslo se znaménkem|l nebo žádný|`86`<br /><br />`86l`|
|uint<br /><br />UInt32|přirozené číslo bez znaménka 32-bit|u nebo ul|`86u`<br /><br />`86ul`|
|unativeint –|Nativní ukazatel jako přirozené číslo bez znaménka|zrušení|`0x00002D3Fun`|
|int64|64bitové celé číslo se znaménkem|L|`86L`|
|UInt64|přirozené číslo bez znaménka 64-bit|UL|`86UL`|
|jeden, float32.|32bitové číslo s plovoucí desetinnou|F nebo f|`4.14F` Nebo `4.14f`|
|||LF|`0x00000000lf`|
|plovoucí; Double|64bitové číslo s plovoucí desetinnou|žádná|`4.14` nebo `2.3E+32` nebo `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|celé číslo, ne pouze 64bitové znázornění|I|`9999999999999999999999999999I`|
|decimal|desetinné číslo, které jsou reprezentovány jako pevný bod nebo racionální číslo|M nebo m|`0.7833M` Nebo `0.7833m`|
|Char|znak Unicode|žádná|`'a'`|
|String|Řetězec znaků Unicode|žádná|`"text\n"`<br /><br />or<br /><br />`@"c:\filename"`<br /><br />or<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />or<br /><br />`"string1" + "string2"`<br /><br />Viz také [řetězce](Strings.md).|
|byte|Znak ASCII|B|`'a'B`|
|Byte|Řetězec ASCII|B|`"text"B`|
|Řetězec nebo byte]|řetězec verbatim|předponu @|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="remarks"></a>Poznámky

Řetězce Unicode mohou obsahovat explicitní kódování, kterou lze zadat pomocí `\u` 16bitové šestnáctkové nebo UTF-32 kódování, kterou lze zadat pomocí `\U` za nímž následuje 32-bit šestnáctkový kód, který představuje Unicode náhradní pár.

Od verze F# 3.1, můžete použít `+` přihlásit ke kombinování řetězcových literálů. Můžete také použít bitového nebo (`|||`) operátor kombinování příznaků výčtu. Například následující kód je platný v F# 3.1:

```fsharp
[<Literal>]
let literal1 = "a" + "b"

[<Literal>]
let fileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let literal2 = 1 ||| 64

[<Literal>]
let literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

Použití jiných operátorů bitového typu není povoleno.

## <a name="named-literals"></a>Pojmenované literály

Hodnoty, které mají být konstantami, mohou být označeny [literálu](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atribut. Tento atribut má efekt sestavení hodnoty se zkompiluje jako konstanta.

Ve vzoru porovnávání výrazů identifikátory, které začínají malými písmeny, jsou vždy považovány za proměnné ke svázání, nikoli jako literály, takže obecně používejte počáteční velká písmena při definování literálů.

## <a name="integers-in-other-bases"></a>Celá čísla v jiných základů

Je taky možné specifikovat podepsaný 32bitová celá čísla v šestnáctkové soustavě, osmičkové nebo binární pomocí `0x`, `0o` nebo `0b` předpony v uvedeném pořadí.

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Podtržítka v numerických literálech

Počínaje F# 4.1, číslic můžete oddělit znakem podtržítka (`_`).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Viz také:

- [Core.literalattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)