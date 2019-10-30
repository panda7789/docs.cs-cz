---
title: Literály
description: Seznamte se s typy literálů F# v programovacím jazyce.
ms.date: 06/28/2019
ms.openlocfilehash: 9792a24ac28eb402e35e78574cd6a2bf9526734d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041033"
---
# <a name="literals"></a>Literály

> [!NOTE]
> Odkazy na reference k rozhraní API v tomto článku vás převezmou na MSDN (teď).

Toto téma obsahuje tabulku, která ukazuje, jak zadat typ literálu v F#.

## <a name="literal-types"></a>Typy literálů

V následující tabulce jsou uvedeny typy literálů F#v. Znaky, které představují číslice v šestnáctkovém zápisu, nerozlišují velká a malá písmena; znaky, které identifikují typ, rozlišují velká a malá písmena.

|Typ|Popis|Přípona nebo předpona|Příklady|
|----|-----------|----------------|--------|
|sbyte|8bitové celé číslo se znaménkem|y|`86y`<br /><br />`0b00000101y`|
|byte|8bitové přirozené číslo bez znaménka|uy|`86uy`<br /><br />`0b00000101uy`|
|Int16|16bitové celé číslo se znaménkem|s|`86s`|
|UInt16|16bitové přirozené číslo bez znaménka|vylepšení|`86us`|
|int<br /><br />Uvedena|Podepsané 32 – celé číslo se znaménkem|l nebo None|`86`<br /><br />`86l`|
|uint<br /><br />UInt32|nepodepsané 32 – přirozené číslo v bitech|u nebo ul|`86u`<br /><br />`86ul`|
|nativeint –|nativní ukazatel na podepsané přirozené číslo|N|`123n`|
|unativeint –|nativní ukazatel jako přirozené číslo bez znaménka|instalován|`0x00002D3Fun`|
|Int64|Podepsané 64 – celé číslo se znaménkem|L|`86L`|
|UInt64|nepodepsané 64 – přirozené číslo v bitech|UL|`86UL`|
|Single, float32|32-bitové číslo s plovoucí desetinnou čárkou|F nebo f|`4.14F` nebo `4.14f`|
|||znaky|`0x00000000lf`|
|Plovák klepat|64-bitové číslo s plovoucí desetinnou čárkou|žádná|`4.14` nebo `2.3E+32` nebo `2.3e+32`|
|||ZNAKY|`0x0000000000000000LF`|
|bigint|celé číslo není omezeno na 64-bitovou reprezentaci|I|`9999999999999999999999999999I`|
|decimal|desetinné číslo reprezentované jako pevný bod nebo racionální číslo|M nebo m|`0.7833M` nebo `0.7833m`|
|Char|znak Unicode|žádná|`'a'` nebo `'\u0061'`|
|String|Řetězec Unicode|žádná|`"text\n"`<br /><br />or<br /><br />`@"c:\filename"`<br /><br />or<br /><br />`"""<book title="Paradise Lost">"""`<br /><br />or<br /><br />`"string1" + "string2"`<br /><br />Viz také [řetězce](Strings.md).|
|byte|Znak ASCII|B|`'a'B`|
|Byte []|Řetězec ASCII|B|`"text"B`|
|Řetězec nebo Byte []|řetězec doslovného řetězce|@ prefix|`@"\\server\share"` (Unicode)<br /><br />`@"\\server\share"B` (ASCII)|

## <a name="named-literals"></a>Pojmenované literály

Hodnoty, které mají být konstanty, mohou být označeny atributem [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) . Tento atribut má vliv, který způsobí, že se hodnota zkompiluje jako konstanta.

V výrazech porovnávání se vzorem se identifikátory začínající malým písmenem vždy považují za proměnné, které mají být vázány, nikoli jako literály, takže při definování literálů byste obecně měli použít počáteční velká písmena.

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a>Poznámky

Řetězce Unicode mohou obsahovat explicitní kódování, která lze zadat pomocí `\u` následovaný 16 bitovým hexadecimálním kódem (0000-FFFF) nebo kódováním UTF-32, které lze zadat pomocí `\U` následovaným 32 šestnáctkovým kódem, který představuje libovolnou znakovou sadu Unicode bod kódu (00000000-0010FFFF).

Použití jiných bitových operátorů kromě `|||` není povoleno.

## <a name="integers-in-other-bases"></a>Celá čísla v jiných základech

Podepsaná 32. celá čísla se znaménkem lze zadat také v šestnáctkovém, osmičkovém nebo binárním formátu pomocí `0x`, `0o` nebo předpony `0b`.

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a>Podtržítka v numerických literálech

Můžete oddělit číslice znakem podtržítka (`_`).

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a>Viz také:

- [Core. LiteralAttribute – – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
