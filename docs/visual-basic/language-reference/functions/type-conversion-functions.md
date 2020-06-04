---
title: Funkce pro převod typů
ms.date: 10/24/2018
f1_keywords:
- vb.CUShort
- vb.csng
- vb.CDate
- CByte
- CSng
- vb.CDec
- CBool
- CStr
- vb.CULng
- CDec
- CVErr
- CDbl
- CShort
- vb.CObj
- vb.CVErr
- CULng
- vb.cdbl
- vb.cbool
- CObj
- CDate
- CLng
- vb.cstr
- vb.cbyte
- vb.clng
- vb.CChar
- CUShort
- vb.CUInt
- vb.cint
- vb.CShort
- CInt
- CUInt
- CChar
helpviewer_keywords:
- CDate function
- CByte function
- Integer data type [Visual Basic], converting
- string conversion [Visual Basic], conversion functions
- fractions
- data types [Visual Basic], converting
- text, converting
- CDec function
- Char data type [Visual Basic], converting
- type conversion [Visual Basic], functions for
- Single data type [Visual Basic], converting
- numbers [Visual Basic], rounding
- rounding numbers [Visual Basic], type conversion
- CUShort function
- Long data type [Visual Basic], converting
- return values [Visual Basic], data types
- single-precision numbers [Visual Basic], converting
- data type conversion [Visual Basic], functions for
- CStr function
- times [Visual Basic], converting
- CSng function
- conversions [Visual Basic], type conversion functions
- CBool function
- CDbl function
- CUInt function
- Currency data type [Visual Basic], conversion functions
- numbers [Visual Basic], converting
- Double data type [Visual Basic], converting
- CLng function
- CSByte function
- double-precision numbers
- Decimal data type [Visual Basic], converting
- Boolean data type [Visual Basic], converting
- integers [Visual Basic], type conversion functions
- dates [Visual Basic], converting
- CULng function
- CInt function
- Date data type [Visual Basic], converting
- Byte data type [Visual Basic], converting
- String data type [Visual Basic], converting
- CChar function
- banker's rounding
- Short data type [Visual Basic], converting
- rounding numbers [Visual Basic], banker's rounding
- type conversion [Visual Basic], Visual Basic vs. .NET Framework
ms.assetid: d9d8d165-f967-44ff-a6cd-598e4740a99e
ms.openlocfilehash: 5c0cfae01da02222d0827e81ec1ed35ce353ead1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415372"
---
# <a name="type-conversion-functions-visual-basic"></a>Funkce pro převod typů (Visual Basic)

Tyto funkce jsou kompilovány vložené, což znamená, že kód převodu je součástí kódu, který vyhodnocuje výraz. Někdy neexistuje žádné volání procedury k provedení převodu, což zvyšuje výkon. Každá funkce převede výraz na konkrétní datový typ.

## <a name="syntax"></a>Syntaxe

```vb
CBool(expression)
CByte(expression)
CChar(expression)
CDate(expression)
CDbl(expression)
CDec(expression)
CInt(expression)
CLng(expression)
CObj(expression)
CSByte(expression)
CShort(expression)
CSng(expression)
CStr(expression)
CUInt(expression)
CULng(expression)
CUShort(expression)
```

## <a name="part"></a>Část

`expression`  
Povinná hodnota. Libovolný výraz zdrojového datového typu.

## <a name="return-value-data-type"></a>Datový typ vrácené hodnoty

Název funkce určuje datový typ hodnoty, kterou vrátí, jak je znázorněno v následující tabulce.

|Název funkce|Návratový typ dat|Rozsah `expression` argumentu|
|-------------------|----------------------|-------------------------------------|
|`CBool`|[Boolean – datový typ](../data-types/boolean-data-type.md)|Libovolný platný `Char` nebo `String` číselný výraz.|
|`CByte`|[Byte – datový typ](../data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType>(0) až <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (bez znaménka); zlomkové části jsou zaokrouhleny.<sup> 1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na převod pomocí `CByte` funkce. Další informace naleznete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|
|`CChar`|[Char – datový typ](../data-types/char-data-type.md)|Libovolný platný `Char` `String` výraz nebo; pouze první znak `String` je převeden; hodnota může být 0 až 65535 (bez znaménka).|
|`CDate`|[Date – datový typ](../data-types/date-data-type.md)|Jakákoli platná reprezentace data a času.|
|`CDbl`|[Double – datový typ](../data-types/double-data-type.md)|-1.79769313486231570 e + 308 do-4.94065645841246544 E-324 pro záporné hodnoty; 4.94065645841246544 e-324 až 1.79769313486231570 E + 308 pro kladné hodnoty.|
|`CDec`|[Decimal – datový typ](../data-types/decimal-data-type.md)|+/-79,228,162,514,264,337,593,543,950,335 pro čísla s nulovou škálou, tj. čísla bez desetinných míst. Pro čísla s 28 desetinnými místy je rozsah +/-7.9228162514264337593543950335. Nejmenší možné nenulové číslo je 0,0000000000000000000000000001 (+/-1E-28).|
|`CInt`|[Integer – datový typ](../data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType>(-2 147 483 648) až <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); zlomkové části se zaokrouhlují.<sup> 1</sup> <br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon konverze s plovoucí desetinnou čárkou pomocí `CInt` funkce. Další informace naleznete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) . |
|`CLng`|[Long – datový typ](../data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType>(-9223372036854775808) až <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9 223 372 036 854 775 807); zlomkové části jsou zaokrouhleny.<sup> 1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon konverze s plovoucí desetinnou čárkou na 64 pomocí `CLng` funkce. Další informace naleznete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|
|`CObj`|[Datový typ objektu](../data-types/object-data-type.md)|Libovolný platný výraz|
|`CSByte`|[SByte – datový typ](../data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType>(-128) až <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); zlomkové části se zaokrouhlují.<sup> 1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na předepsanou bajtů s `CSByte` funkcí; další informace naleznete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|
|`CShort`|[Short – datový typ](../data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType>(-32 768) až <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); zlomkové části se zaokrouhlují.<sup> 1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na 16bitový celočíselný převod pomocí `CShort` funkce; Další informace naleznete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|
|`CSng`|[Single – datový typ](../data-types/single-data-type.md)|-3.402823 e + + 38 do-1.401298 E-45 pro záporné hodnoty; 1.401298 e-45 až 3.402823 E + 38 pro kladné hodnoty.|
|`CStr`|[Datový typ String](../data-types/string-data-type.md)|Vrátí pro `CStr` záviset na `expression` argumentu. Viz [návratové hodnoty pro funkci CStr](return-values-for-the-cstr-function.md).|
|`CUInt`|[UInteger – datový typ](../data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType>(0) až <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (bez znaménka); zlomkové části jsou zaokrouhleny.<sup> 1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na unsigned integer konverzi s `CUInt` funkcí; další informace naleznete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|
|`CULng`|[ULong – datový typ](../data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType>(0) až <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (bez znaménka); zlomkové části jsou zaokrouhleny.<sup> 1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na nepodepsaný dlouhý převod celého čísla s `CULng` funkcí; další informace naleznete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|
|`CUShort`|[UShort – datový typ](../data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType>(0) až <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (bez znaménka); zlomkové části jsou zaokrouhleny.<sup> 1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na nepodepsaný 16bitový celočíselný převod s `CUShort` funkcí; další informace naleznete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|

<sup>1</sup> zlomkové části mohou být předmětem zvláštního typu zaokrouhlení s názvem *zaokrouhlování bank*. Další informace najdete v části "poznámky".

## <a name="remarks"></a>Poznámky

Jako pravidlo byste měli použít funkce pro převod typu Visual Basic v předvolbách pro metody .NET Framework, jako je například `ToString()` , buď na <xref:System.Convert> třídu, nebo na samostatné struktuře typu nebo třídě. Funkce Visual Basic jsou navržené pro optimální interakci s kódem Visual Basic a zároveň usnadňují čtení zdrojového kódu. Kromě toho metody převodu .NET Framework nevytváří vždy stejné výsledky jako funkce Visual Basic, například při převodu `Boolean` na `Integer` . Další informace najdete v tématu [řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).

Počínaje Visual Basic 15,8 se výkon konverze s plovoucí desetinnou čárkou na celé číslo optimalizuje, když předáte <xref:System.Single> hodnotu nebo <xref:System.Double> vrácenou následujícími metodami do jedné z funkcí konverze celého čísla ( `CByte` , `CShort` , `CInt` , `CLng` , `CSByte` , `CUShort` , `CUInt` , `CULng` ):

- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Fix(System.Single)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Double)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Object)?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Conversion.Int(System.Single)?displayProperty=nameWithType>
- <xref:System.Math.Ceiling(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Floor(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Round(System.Double)?displayProperty=nameWithType>
- <xref:System.Math.Truncate(System.Double)?displayProperty=nameWithType>

Tato optimalizace umožňuje kódu, který provede velký počet převodů celých čísel, aby běžel dvakrát jako rychlý. Následující příklad znázorňuje tyto optimalizované převody s plovoucí desetinnou čárkou na celé číslo:

```vb
Dim s As Single = 173.7619
Dim d As Double = s

Dim i1 As Integer = CInt(Fix(s))               ' Result: 173
Dim b1 As Byte = CByte(Int(d))                 ' Result: 173
Dim s1 AS Short = CShort(Math.Truncate(s))     ' Result: 173
Dim i2 As Integer = CInt(Math.Ceiling(d))      ' Result: 174
Dim i3 As Integer = CInt(Math.Round(s))        ' Result: 174
```

## <a name="behavior"></a>Chování

- **Konverze za.** Obecně můžete použít funkce pro převod datového typu k převedení výsledku operace na určitý datový typ, nikoli na výchozí datový typ. Například použijte `CDec` k vynucení desítkové aritmetické operace v případech, kde by normálně probíhat jednoduchá přesnost, dvojitá přesnost nebo aritmetická celočíselná hodnota.

- **Převody se nezdařily.** Pokud `expression` je předaná funkce mimo rozsah datového typu, na který má být převeden, <xref:System.OverflowException> dojde k chybě.

- **Zlomkové části.** Když převedete neceločíselnou hodnotu na celočíselný typ, funkce převodu celého čísla ( `CByte` , `CInt` , `CLng` , `CSByte` , `CShort` , `CUInt` , `CULng` , a `CUShort` ) odstraní zlomkovou část a zaokrouhlí hodnotu na nejbližší celé číslo.

     Pokud je Zlomková část přesně 0,5, funkce pro převod celého čísla zaokrouhlí na nejbližší sudé celé číslo. Například 0,5 se zaokrouhlí na 0 a 1,5 a 2,5 se zaokrouhlí na 2. Tento postup se někdy označuje jako *zaokrouhlování bank*a jeho účelem je kompenzovat posun, který by se mohl nashromáždit při přidávání mnoha takových čísel dohromady.

     `CInt`a `CLng` liší se od <xref:Microsoft.VisualBasic.Conversion.Int%2A> <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funkcí a, které se zkrátí, spíše než zaokrouhlit, zlomkovou část čísla. Také `Fix` a `Int` vždy vracet hodnotu stejného datového typu jako při předání.

- **Převody data a času.** <xref:Microsoft.VisualBasic.Information.IsDate%2A>Funkci lze použít k určení, zda je možné hodnotu převést na datum a čas. `CDate`rozpoznává literály data a časové literály, ale ne číselné hodnoty. Chcete-li převést hodnotu Visual Basic 6,0 `Date` na `Date` hodnotu v Visual Basic 2005 nebo novějších verzích, lze použít <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> metodu.

- **Neutrální hodnoty data a času.** [Datový typ datum](../data-types/date-data-type.md) vždy obsahuje informace o datu a čase. Pro účely konverze typu Visual Basic považuje 1/1/0001 (1. ledna of year) za *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) jako neutrální hodnotu pro čas. Převedete-li `Date` hodnotu na řetězec, `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci. Například Pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledkem je "9:30:00 dop.", informace o datu jsou potlačeny. Informace o datu jsou však stále přítomny v původní `Date` hodnotě a lze je obnovit pomocí funkcí, jako je <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> funkce.

- **Citlivostní jazyková verze.** Funkce pro převod typů zahrnující řetězce provádějí převody na základě aktuálního nastavení jazykové verze aplikace. Například `CDate` rozpoznává formáty data podle nastavení národního prostředí systému. Je nutné zadat den, měsíc a rok ve správném pořadí pro vaše národní prostředí nebo datum nemusí být interpretováno správně. Formát dlouhého data není rozpoznán, pokud obsahuje řetězec dne v týdnu, například "Středa".

     Pokud potřebujete převést na nebo z řetězcové reprezentace hodnoty v jiném formátu, než který je určen národním prostředím, nemůžete použít funkce pro převod typu Visual Basic. K tomu použijte `ToString(IFormatProvider)` metody a tohoto `Parse(String, IFormatProvider)` typu hodnoty. Například použijte <xref:System.Double.Parse%2A?displayProperty=nameWithType> při převodu řetězce na a `Double` použít <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na řetězec.

## <a name="ctype-function"></a>CType – funkce

[Funkce CType](ctype-function.md) přebírá druhý argument, `typename` a převede `expression` na `typename` , kde `typename` může být libovolný datový typ, struktura, třída nebo rozhraní, na které existuje platný převod.

Porovnání `CType` s jinými klíčovými slovy pro převod typů naleznete v tématu [operátor DirectCast](../operators/directcast-operator.md) a [operátor TryCast](../operators/trycast-operator.md).

## <a name="cbool-example"></a>Příklad CBool

Následující příklad používá `CBool` funkci k převodu výrazů na `Boolean` hodnoty. Pokud je výraz vyhodnocen jako nenulová hodnota, `CBool` vrátí `True` , jinak vrátí `False` .

[!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]

## <a name="cbyte-example"></a>Příklad CByte

Následující příklad používá `CByte` funkci pro převod výrazu na `Byte` .

[!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]

## <a name="cchar-example"></a>Příklad CChar

Následující příklad používá `CChar` funkci k převodu prvního znaku `String` výrazu na `Char` typ.

[!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]

Vstupní argument pro `CChar` musí být datového typu `Char` nebo `String` . Nelze použít `CChar` k převedení čísla na znak, protože `CChar` nemůže přijmout číselný datový typ. Následující příklad získá číslo představující bod kódu (kód znaku) a převede ho na odpovídající znak. Pomocí <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> funkce získá řetězec číslic, `CInt` převede řetězec na typ `Integer` a `ChrW` převede číslo na typ `Char` .

[!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]

## <a name="cdate-example"></a>Příklad CDate

V následujícím příkladu je použita `CDate` funkce pro převod řetězců na `Date` hodnoty. Obecně se nedoporučuje používat data a časy pevně zakódování jako řetězce (jak je znázorněno v tomto příkladu). Použijte literály data a časová literály, například #Feb 12, 1969 # a #4:45:23 PM #, místo toho.

[!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]

## <a name="cdbl-example"></a>Příklad CDbl

[!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]

## <a name="cdec-example"></a>Příklad CDec

Následující příklad používá `CDec` funkci k převodu číselné hodnoty na `Decimal` .

[!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]

## <a name="cint-example"></a>Příklad CInt

Následující příklad používá `CInt` funkci pro převod hodnoty na `Integer` .

[!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]

## <a name="clng-example"></a>Příklad CLng

V následujícím příkladu je použita `CLng` funkce pro převod hodnot na `Long` .

[!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]

## <a name="cobj-example"></a>Příklad CObj

Následující příklad používá `CObj` funkci k převodu číselné hodnoty na `Object` . `Object`Proměnná sama obsahuje pouze ukazatel se čtyřmi bajty, který odkazuje na hodnotu, která `Double` je k ní přiřazena.

[!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]

## <a name="csbyte-example"></a>Příklad CSByte

Následující příklad používá `CSByte` funkci k převodu číselné hodnoty na `SByte` .

[!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]

## <a name="cshort-example"></a>Příklad CShort

Následující příklad používá `CShort` funkci k převodu číselné hodnoty na `Short` .

[!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]

## <a name="csng-example"></a>Příklad CSng

V následujícím příkladu je použita `CSng` funkce pro převod hodnot na `Single` .

[!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]

## <a name="cstr-example"></a>Příklad CStr

Následující příklad používá `CStr` funkci k převodu číselné hodnoty na `String` .

[!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]

Následující příklad používá `CStr` funkci pro převod `Date` hodnot na `String` hodnoty.

[!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]

`CStr`vždy vykreslí `Date` hodnotu ve standardním krátkém formátu pro aktuální národní prostředí, například "6/15/2003 4:35:47 PM". Potlačí ale `CStr` *neutrální hodnoty* 1/1/0001 pro datum a 00:00:00 pro čas.

Další informace o hodnotách vrácených v naleznete `CStr` v tématu [návratové hodnoty pro funkci CStr](return-values-for-the-cstr-function.md).

## <a name="cuint-example"></a>Příklad CUInt

Následující příklad používá `CUInt` funkci k převodu číselné hodnoty na `UInteger` .

[!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]

## <a name="culng-example"></a>Příklad CULng

Následující příklad používá `CULng` funkci k převodu číselné hodnoty na `ULong` .

[!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]

## <a name="cushort-example"></a>Příklad CUShort

Následující příklad používá `CUShort` funkci k převodu číselné hodnoty na `UShort` .

[!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- <xref:Microsoft.VisualBasic.Conversion.Int%2A>
- <xref:Microsoft.VisualBasic.Conversion.Fix%2A>
- <xref:Microsoft.VisualBasic.Strings.Format%2A>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:Microsoft.VisualBasic.Conversion.Oct%2A>
- <xref:Microsoft.VisualBasic.Conversion.Str%2A>
- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [Převodní funkce](conversion-functions.md)
- [Převody typů v jazyce Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
