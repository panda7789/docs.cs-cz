---
title: Funkce pro převod typů (Visual Basic)
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
ms.openlocfilehash: 6b448fa23368f7a0848c44362337b0ccc70b6162
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592078"
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
  
## <a name="part"></a>Částí  
 `expression`  
 Povinný parametr. Libovolný výraz zdrojového datového typu.  
  
## <a name="return-value-data-type"></a>Datový typ vrácené hodnoty  
 Název funkce určuje datový typ hodnoty, kterou vrátí, jak je znázorněno v následující tabulce.  
  
|Název funkce|Návratový typ dat|Rozsah pro argument `expression`|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Jakékoli platné `Char` nebo `String` nebo číselný výraz.|  
|`CByte`|[Datový typ Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) až <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (bez znaménka); zlomkové části jsou zaokrouhleny. <sup>1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na převod bajtů pomocí funkce `CByte`; Další informace najdete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|  
|`CChar`|[Datový typ Char](../../../visual-basic/language-reference/data-types/char-data-type.md)|Libovolný platný výraz `Char` nebo `String`; Převede se pouze první znak `String`. hodnota může být 0 až 65535 (bez znaménka).|  
|`CDate`|[Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|Jakákoli platná reprezentace data a času.|  
|`CDbl`|[Datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570 e + 308 do-4.94065645841246544 E-324 pro záporné hodnoty; 4.94065645841246544 e-324 až 1.79769313486231570 E + 308 pro kladné hodnoty.|  
|`CDec`|[Datový typ Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+/-79,228,162,514,264,337,593,543,950,335 pro čísla s nulovou škálou, tj. čísla bez desetinných míst. Pro čísla s 28 desetinnými místy je rozsah +/-7.9228162514264337593543950335. Nejmenší možné nenulové číslo je 0,0000000000000000000000000001 (+/-1E-28).|  
|`CInt`|[Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2 147 483 648) až <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); zlomkové části jsou zaokrouhleny. <sup>1</sup> <br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na převod celého čísla pomocí funkce `CInt`; Další informace najdete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) . |  
|`CLng`|[Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MinValue?displayProperty=nameWithType> (-9223372036854775808) až <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9 223 372 036 854 775 807); zlomkové části jsou zaokrouhleny. <sup>1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon s plovoucí desetinnou čárkou na 64 celočíselný převod pomocí funkce `CLng`; Další informace najdete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|  
|`CObj`|[Datový typ Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|Libovolný platný výraz.|  
|`CSByte`|[Datový typ SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) až <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); zlomkové části jsou zaokrouhleny. <sup>1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na podepsaný bajtový převod pomocí funkce `CSByte`; Další informace najdete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|  
|`CShort`|[Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32 768) až <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); zlomkové části jsou zaokrouhleny. <sup>1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na 16bitový celočíselný převod pomocí funkce `CShort`; Další informace najdete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|  
|`CSng`|[Datový typ Single](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823 e + + 38 do-1.401298 E-45 pro záporné hodnoty; 1.401298 e-45 až 3.402823 E + 38 pro kladné hodnoty.|  
|`CStr`|[Datový typ String](../../../visual-basic/language-reference/data-types/string-data-type.md)|Vrátí hodnotu pro `CStr` závisí na argumentu `expression`. Viz [návratové hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) až <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (bez znaménka); zlomkové části jsou zaokrouhleny. <sup>1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na unsigned integer konverzi pomocí funkce `CUInt`; Další informace najdete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|  
|`CULng`|[Datový typ ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) až <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18446744073709551615) (bez znaménka); zlomkové části jsou zaokrouhleny. <sup>1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na nepodepsaný dlouhý celočíselný převod pomocí funkce `CULng`; Další informace najdete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|  
|`CUShort`|[Datový typ UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) až <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (bez znaménka); zlomkové části jsou zaokrouhleny. <sup>1</sup><br/><br/>Počínaje Visual Basic 15,8 Visual Basic optimalizuje výkon plovoucí desetinné čárky na 16bitový celočíselný převod pomocí funkce `CUShort`; Další informace najdete v části [poznámky](#remarks) . Příklad najdete v části s [Příklady CInt](#cint-example) .|  
  
 <sup>1</sup> zlomkové části mohou být předmětem zvláštního typu zaokrouhlení s názvem *zaokrouhlování bank*. Další informace najdete v části "poznámky".  
  
## <a name="remarks"></a>Poznámky  
 Jako pravidlo byste měli použít funkce pro Visual Basic pro převod typu v předvolbách k metodám .NET Framework, jako je například `ToString()`, buď na třídě <xref:System.Convert>, nebo na samostatné struktuře typu nebo třídě. Funkce Visual Basic jsou navržené pro optimální interakci s kódem Visual Basic a zároveň usnadňují čtení zdrojového kódu. Kromě toho metody převodu .NET Framework nevytváří vždy stejné výsledky jako funkce Visual Basic, například při převodu `Boolean` na `Integer`. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  

Počínaje Visual Basic 15,8 je výkon konverze s plovoucí desetinnou čárkou na celé číslo optimalizovaný, Pokud předáte hodnotu <xref:System.Single> nebo <xref:System.Double> vrácenou následujícími metodami do jedné z funkcí konverze celého čísla (`CByte`, `CShort`, `CInt`, @no__ t-5, `CSByte`, `CUShort`, `CUInt`, `CULng`):

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
  
- **Konverze za.** Obecně můžete použít funkce pro převod datového typu k převedení výsledku operace na určitý datový typ, nikoli na výchozí datový typ. Například použijte `CDec` k vynucení desítkové aritmetické operace v případech, kdy by došlo k normálnímu vykonání aritmetické operace s jednoduchou přesností, dvojitou přesností nebo celočíselnou.  
  
- **Převody se nezdařily.** Pokud je `expression` předané funkci mimo rozsah datového typu, na který má být převeden, dojde k chybě <xref:System.OverflowException>.  
  
- **Zlomkové části.** Když převedete neceločíselnou hodnotu na celočíselný typ, funkce převodu celého čísla (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng` a `CUShort`) odstraní zlomkovou část a zaokrouhlí hodnotu na nejbližší celé číslo.  
  
     Pokud je Zlomková část přesně 0,5, funkce pro převod celého čísla zaokrouhlí na nejbližší sudé celé číslo. Například 0,5 se zaokrouhlí na 0 a 1,5 a 2,5 se zaokrouhlí na 2. Tento postup se někdy označuje jako *zaokrouhlování bank*a jeho účelem je kompenzovat posun, který by se mohl nashromáždit při přidávání mnoha takových čísel dohromady.  
  
     `CInt` a `CLng` se liší od funkcí <xref:Microsoft.VisualBasic.Conversion.Int%2A> a <xref:Microsoft.VisualBasic.Conversion.Fix%2A>, které se zkrátí místo zaokrouhlení na zlomek čísla. Také `Fix` a `Int` vždy vrátí hodnotu stejného datového typu jako při předání.  
  
- **Převody data a času.** Pomocí funkce <xref:Microsoft.VisualBasic.Information.IsDate%2A> určíte, zda je možné hodnotu převést na datum a čas. `CDate` rozpoznává literály data a časové literály, ale ne číselné hodnoty. K převedení hodnoty Visual Basic 6,0 `Date` na hodnotu `Date` v Visual Basic 2005 nebo novějších verzích můžete použít metodu <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType>.  
  
- **Neutrální hodnoty data a času.** [Datový typ datum](../../../visual-basic/language-reference/data-types/date-data-type.md) vždy obsahuje informace o datu a čase. Pro účely konverze typu Visual Basic považuje 1/1/0001 (1. ledna of year) za *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) jako neutrální hodnotu pro čas. Pokud převedete hodnotu `Date` na řetězec, `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci. Například Pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledek je "9:30:00 dop."; informace o datu jsou potlačeny. Informace o datu jsou však stále přítomny v původní hodnotě @no__t 0 a lze je obnovit pomocí funkcí, jako je funkce <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>.  
  
- **Citlivostní jazyková verze.** Funkce pro převod typů zahrnující řetězce provádějí převody na základě aktuálního nastavení jazykové verze aplikace. Například `CDate` rozpoznává formáty data podle nastavení národního prostředí systému. Je nutné zadat den, měsíc a rok ve správném pořadí pro vaše národní prostředí nebo datum nemusí být interpretováno správně. Formát dlouhého data není rozpoznán, pokud obsahuje řetězec dne v týdnu, například "Středa".  
  
     Pokud potřebujete převést na nebo z řetězcové reprezentace hodnoty v jiném formátu, než který je určen národním prostředím, nemůžete použít funkce pro převod typu Visual Basic. Chcete-li to provést, použijte metody `ToString(IFormatProvider)` a `Parse(String, IFormatProvider)` tohoto typu hodnoty. Například při převodu řetězce na `Double` použijte <xref:System.Double.Parse%2A?displayProperty=nameWithType> a při převodu hodnoty typu `Double` na řetězec použijte <xref:System.Double.ToString%2A?displayProperty=nameWithType>.  
  
## <a name="ctype-function"></a>CType – funkce  
 [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md) přebírá druhý argument, `typename` a převede `expression` na `typename`, kde `typename` může být libovolný datový typ, struktura, třída nebo rozhraní, na které existuje platný převod.  
  
 Porovnání `CType` s jinými klíčovými slovy převodu typů naleznete v tématu [operátor DirectCast](../../../visual-basic/language-reference/operators/directcast-operator.md) a [operátor TryCast](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>Příklad CBool  
 V následujícím příkladu se pomocí funkce `CBool` převádí výrazy na hodnoty `Boolean`. Pokud je výraz vyhodnocen jako nenulová hodnota, `CBool` vrátí `True`; v opačném případě vrátí `False`.  
  
 [!code-vb[VbVbalrFunctions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#1)]  
  
## <a name="cbyte-example"></a>Příklad CByte  
 Následující příklad používá funkci `CByte` k převedení výrazu na `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#2)]  
  
## <a name="cchar-example"></a>Příklad CChar  
 Následující příklad používá funkci `CChar` k převedení prvního znaku `String` na typ `Char`.  
  
 [!code-vb[VbVbalrFunctions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#3)]  
  
 Vstupní argument pro `CChar` musí být datového typu `Char` nebo `String`. @No__t-0 nelze použít k převodu čísla na znak, protože `CChar` nemůže přijmout číselný datový typ. Následující příklad získá číslo představující bod kódu (kód znaku) a převede ho na odpovídající znak. Pomocí funkce <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> Získá řetězec číslic, `CInt` pro převod řetězce na typ `Integer` a `ChrW` pro převod čísla na typ `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#4)]  
  
## <a name="cdate-example"></a>Příklad CDate  
 V následujícím příkladu je použita funkce `CDate` pro převod řetězců na hodnoty `Date`. Obecně se nedoporučuje používat data a časy pevně zakódování jako řetězce (jak je znázorněno v tomto příkladu). Použijte literály data a časová literály, například #Feb 12, 1969 # a #4:45:23 PM #, místo toho.  
  
 [!code-vb[VbVbalrFunctions#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#5)]  
  
## <a name="cdbl-example"></a>Příklad CDbl  
 [!code-vb[VbVbalrFunctions#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#6)]  
  
## <a name="cdec-example"></a>Příklad CDec  
 V následujícím příkladu je použita funkce `CDec` pro převod číselné hodnoty na `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#7)]  
  
## <a name="cint-example"></a>Příklad CInt  
 Následující příklad používá funkci `CInt` k převedení hodnoty na `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#8)]  

## <a name="clng-example"></a>Příklad CLng
 V následujícím příkladu je použita funkce `CLng` pro převod hodnot na `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#9)]  
  
## <a name="cobj-example"></a>Příklad CObj  
 V následujícím příkladu je použita funkce `CObj` pro převod číselné hodnoty na `Object`. Proměnná `Object` obsahuje pouze ukazatel se čtyřmi bajty, který odkazuje na přiřazenou hodnotu `Double`.  
  
 [!code-vb[VbVbalrFunctions#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#10)]  
  
## <a name="csbyte-example"></a>Příklad CSByte  
 V následujícím příkladu je použita funkce `CSByte` pro převod číselné hodnoty na `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#11)]  
  
## <a name="cshort-example"></a>Příklad CShort  
 V následujícím příkladu je použita funkce `CShort` pro převod číselné hodnoty na `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#12)]  
  
## <a name="csng-example"></a>Příklad CSng  
 V následujícím příkladu je použita funkce `CSng` pro převod hodnot na `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#13)]  
  
## <a name="cstr-example"></a>Příklad CStr  
 V následujícím příkladu je použita funkce `CStr` pro převod číselné hodnoty na `String`.  
  
 [!code-vb[VbVbalrFunctions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#14)]  
  
 Následující příklad používá funkci `CStr` k převodu hodnot `Date` na hodnoty `String`.  
  
 [!code-vb[VbVbalrFunctions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#15)]  
  
 `CStr` vždy vykreslí hodnotu `Date` ve standardním krátkém formátu pro aktuální národní prostředí, například "6/15/2003 4:35:47 PM". @No__t-0 však potlačí *neutrální hodnoty* 1/1/0001 pro datum a 00:00:00 pro čas.  
  
 Další informace o hodnotách vrácených `CStr` naleznete v tématu [návratové hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Příklad CUInt  
 V následujícím příkladu je použita funkce `CUInt` pro převod číselné hodnoty na `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#16)]  
  
## <a name="culng-example"></a>Příklad CULng  
 V následujícím příkladu je použita funkce `CULng` pro převod číselné hodnoty na `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#17)]  
  
## <a name="cushort-example"></a>Příklad CUShort  
 V následujícím příkladu je použita funkce `CUShort` pro převod číselné hodnoty na `UShort`.  
  
 [!code-vb[VbVbalrFunctions#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrFunctions/VB/Class1.vb#18)]  
  
## <a name="see-also"></a>Viz také:

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
- [Převodní funkce](../../../visual-basic/language-reference/functions/conversion-functions.md)
- [Převody typu v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
