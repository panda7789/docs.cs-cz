---
title: Literály (F#)
description: 'Další informace o literálu typy v programovacím jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: f28ca0ae7a0b092bbc039d23625b883faffd241c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564336"
---
# <a name="literals"></a>Literály

> [!NOTE]
Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN (prozatím).

Toto téma obsahuje tabulku, která ukazuje, jak zadat typ literál v jazyce F #.

## <a name="literal-types"></a>Typy literálu
V následující tabulce jsou uvedeny typy literálu v jazyce F #. Znaky, které představují číslic v šestnáctkové soustavě nerozlišují; znaky, které identifikují typ rozlišují velká a malá písmena.

|Typ|Popis|Přípony ani předpony|Příklady|
|----|-----------|----------------|--------|
|sbyte|8bitové celé číslo se znaménkem|y|`86y`<br /><br />`0b00000101y`|
|byte|nepodepsané 8bitové přirozený číslo|UY|`86uy`<br /><br />`0b00000101uy`|
|Int16|16bitové celé číslo se znaménkem|s|`86s`|
|UInt16|nepodepsané 16bitové přirozený číslo|nám|`86us`|
|int<br /><br />int32|32bitové celé číslo se znaménkem|l nebo hodnotu none|`86`<br /><br />`86l`|
|uint<br /><br />UInt32|nepodepsané 32bitové číslo přirozený|u nebo ul|`86u`<br /><br />`86ul`|
|unativeint –|Nativní ukazatel jako číslo bez znaménka přirozený|zrušení|`0x00002D3Fun`|
|int64|64bitové celé číslo se znaménkem|L|`86L`|
|UInt64|nepodepsané číslo přirozený 64-bit|UL|`86UL`|
|jeden, float32|32bitové číslo s plovoucí desetinnou|F nebo f|`4.14F` Nebo `4.14f`|
|||LF|`0x00000000lf`|
|float; Double|číslo s plovoucí desetinnou 64-bit|žádná|`4.14` nebo `2.3E+32` nebo `2.3e+32`|
|||LF|`0x0000000000000000LF`|
|bigint|mimo jiné k reprezentaci 64bitové celé číslo|I|`9999999999999999999999999999I`|
|decimal|desetinná čísla reprezentován jako dlouhodobý bod nebo racionální číslo|M nebo m|`0.7833M` Nebo `0.7833m`|
|Char|znak Unicode|žádná|`'a'`|
|String|Řetězec znaků Unicode|žádná|`"text\n"`<br /><br />or<br /><br />`@"c:\filename"`<br /><br />or<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />or<br /><br />`"string1" + "string2"`<br /><br />Viz také [řetězce](Strings.md).|
|byte|Znaků ASCII|B|`'a'B`|
|Byte|Řetězec ASCII|B|`"text"B`|
|Řetězec nebo byte]|řetězec typu verbatim|předponu @|`@"\\server\share"` (Kódování Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="remarks"></a>Poznámky
Řetězců v kódu Unicode může obsahovat explicitní kódování, kterou můžete zadat pomocí `\u` následovaný kódem v šestnáctkové soustavě 16bitové nebo kódování UTF-32, který můžete zadat pomocí `\U` následuje 32bitové šestnáctkové kód, který představuje typu Unicode náhradní pár.

Od verze F # 3.1, můžete použít `+` přihlásit spojí textové literály. Můžete také použít bitové hodnotě nebo (`|||`) operátor kombinovat příznaky výčtu. Například následující kód je právní v F # 3.1:

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

Použití jiné bitové operátory není povoleno.


## <a name="named-literals"></a>Pojmenované literály
Může být označen hodnoty, které by měla být konstanty [literálu](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atribut. Tento atribut má za následek způsobuje hodnotu sestavují jako konstanta.

Ve vzoru výraz identifikátory, které začínají malá písmena jsou vždy považovány za proměnné vázat, nikoli jako literály, takže obvykle používejte pro počáteční kapitálek definujete literály.

## <a name="integers-in-other-bases"></a>Celá čísla v jiných databázích

Podepsaná celá čísla 32-bit lze zadat také v šestnáctkové, osmičkové nebo binární pomocí `0x`, `0o` nebo `0b` předpony v uvedeném pořadí.

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Podtržítka v číselné literály

Od verze 4.1 F #, můžete oddělit číslic znak podtržítka (`_`).

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a>Viz také

[Core.literalattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
