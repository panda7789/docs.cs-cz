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
ms.openlocfilehash: cbc9891170cde4b993a5dc890ed71c07a6f59f9e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129555"
---
# <a name="type-conversion-functions-visual-basic"></a>Funkce pro převod typů (Visual Basic)
Tyto funkce jsou zkompilovaný vloženě, což znamená, že kód převodu je součástí kódu, který se vyhodnotí výraz. Někdy není žádná volání procedury k provedení převodu, což zvyšuje výkon. Každá funkce převede výraz na určitý datový typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
 Povinný parametr. Libovolný výraz zdrojového datového typu.  
  
## <a name="return-value-data-type"></a>Vrátí hodnotu datového typu  
 Název funkce určuje datový typ, který vrátí, jak je znázorněno v následující tabulce.  
  
|Název funkce|Návratový typ dat|Rozsah pro `expression` argument|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Libovolný platný `Char` nebo `String` nebo číselný výraz.|  
|`CByte`|[Datový typ Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md)|<xref:System.Byte.MinValue?displayProperty=nameWithType> (0) prostřednictvím <xref:System.Byte.MaxValue?displayProperty=nameWithType> (255) (unsigned); jsou zaokrouhleny zlomkové části.<sup> 1</sup><br/><br/>Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon s plovoucí desetinnou čárkou s převodem `CByte` funkce, najdete v článku [poznámky](#remarks) části Další informace. Zobrazit [CInt příklad](#cint-example) oddílu příklad.|  
|`CChar`|[Datový typ Char](../../../visual-basic/language-reference/data-types/char-data-type.md)|Libovolný platný `Char` nebo `String` výrazu; pouze první znak `String` převeden; možné hodnoty jsou 0 až 65535 (unsigned).|  
|`CDate`|[Datový typ Date](../../../visual-basic/language-reference/data-types/date-data-type.md)|Libovolné platné vyjádření data a času.|  
|`CDbl`|[Datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570E + 308 do - 4.94065645841246544E-324 pro záporné hodnoty. 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 pro kladné hodnoty.|  
|`CDec`|[Datový typ Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+/-79,228,162,514,264,337,593,543,950,335 škálovaných nula čísel, tedy čísla bez desetinných míst. Pro 28 desetinná čísla jsou v rozsahu +/-7,9228162514264337593543950335. Nejmenší možný počet nenulové je 0,0000000000000000000000000001 (+/-1E-28).|  
|`CInt`|[Datový typ Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md)|<xref:System.Int32.MinValue?displayProperty=nameWithType> (-2,147,483,648) prostřednictvím <xref:System.Int32.MaxValue?displayProperty=nameWithType> (2 147 483 647); jsou zaokrouhleny zlomkové části.<sup> 1</sup> <br/><br/>Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod celého čísla s plovoucí desetinnou čárkou `CInt` funkce, najdete v článku [poznámky](#remarks) části Další informace. Zobrazit [CInt příklad](#cint-example) oddílu příklad. |  
|`CLng`|[Datový typ Long](../../../visual-basic/language-reference/data-types/long-data-type.md)|<xref:System.Int64.MaxValue?displayProperty=nameWithType> (-9,223,372,036,854,775,808) prostřednictvím <xref:System.Int64.MaxValue?displayProperty=nameWithType> (9,223,372,036,854,775,807); jsou zaokrouhleny zlomkové části.<sup> 1</sup><br/><br/>Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod 64bitové celé číslo s plovoucí desetinnou čárkou `CLng` funkce, najdete v článku [poznámky](#remarks) části Další informace. Zobrazit [CInt příklad](#cint-example) oddílu příklad.|  
|`CObj`|[Datový typ Object](../../../visual-basic/language-reference/data-types/object-data-type.md)|Libovolný platný výraz.|  
|`CSByte`|[Datový typ SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<xref:System.SByte.MinValue?displayProperty=nameWithType> (-128) prostřednictvím <xref:System.SByte.MaxValue?displayProperty=nameWithType> (127); jsou zaokrouhleny zlomkové části.<sup> 1</sup><br/><br/>Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod na bajty se znaménkem s plovoucí desetinnou čárkou `CSByte` funkce, najdete v článku [poznámky](#remarks) části Další informace. Zobrazit [CInt příklad](#cint-example) oddílu příklad.|  
|`CShort`|[Datový typ Short](../../../visual-basic/language-reference/data-types/short-data-type.md)|<xref:System.Int16.MinValue?displayProperty=nameWithType> (-32 768) prostřednictvím <xref:System.Int16.MaxValue?displayProperty=nameWithType> (32 767); jsou zaokrouhleny zlomkové části.<sup> 1</sup><br/><br/>Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod 16bitové celé číslo s plovoucí desetinnou čárkou `CShort` funkce, najdete v článku [poznámky](#remarks) části Další informace. Zobrazit [CInt příklad](#cint-example) oddílu příklad.|  
|`CSng`|[Datový typ Single](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823E + 38-1, 401298E-45 pro záporné hodnoty. 1, 401298E-45 prostřednictvím 3.402823E + 38 pro kladné hodnoty.|  
|`CStr`|[Datový typ String](../../../visual-basic/language-reference/data-types/string-data-type.md)|Vrátí `CStr` záviset `expression` argument. Zobrazit [návratové hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[Datový typ UInteger](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<xref:System.UInt32.MinValue?displayProperty=nameWithType> (0) prostřednictvím <xref:System.UInt32.MaxValue?displayProperty=nameWithType> (4 294 967 295) (unsigned); jsou zaokrouhleny zlomkové části.<sup> 1</sup><br/><br/>Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod na celé číslo bez znaménka s plovoucí desetinnou čárkou `CUInt` funkce, najdete v článku [poznámky](#remarks) části Další informace. Zobrazit [CInt příklad](#cint-example) oddílu příklad.|  
|`CULng`|[Datový typ ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<xref:System.UInt64.MinValue?displayProperty=nameWithType> (0) prostřednictvím <xref:System.UInt64.MaxValue?displayProperty=nameWithType> (18,446,744,073,709,551,615) (unsigned); jsou zaokrouhleny zlomkové části.<sup> 1</sup><br/><br/>Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod dlouhé celé číslo bez znaménka s plovoucí desetinnou čárkou `CULng` funkce, najdete v článku [poznámky](#remarks) části Další informace. Zobrazit [CInt příklad](#cint-example) oddílu příklad.|  
|`CUShort`|[Datový typ UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<xref:System.UInt16.MinValue?displayProperty=nameWithType> (0) prostřednictvím <xref:System.UInt16.MaxValue?displayProperty=nameWithType> (65 535) (unsigned); jsou zaokrouhleny zlomkové části.<sup> 1</sup><br/><br/>Počínaje 15.8 jazyka Visual Basic, Visual Basic optimalizuje výkon pro převod bez znaménka 16bitové celé číslo s plovoucí desetinnou čárkou `CUShort` funkce, najdete v článku [poznámky](#remarks) části Další informace. Zobrazit [CInt příklad](#cint-example) oddílu příklad.|  
  
 <sup>1</sup> zlomkové části můžou podléhat zvláštní druh zaokrouhlování volané *je bankovní zaokrouhlení*. Další informace viz "Poznámky".  
  
## <a name="remarks"></a>Poznámky  
 Jako pravidlo, používejte funkce pro převod typů jazyka Visual Basic preferenci metod rozhraní .NET Framework, jako `ToString()`– buď na <xref:System.Convert> třídy nebo na individuální typu struktury nebo třídy. Funkce jazyka Visual Basic jsou navrženy pro zajištění optimálního interakce s kódem jazyka Visual Basic a také využívají zdrojový kód kratší a snadněji čitelné. Kromě toho převod metod rozhraní .NET Framework vždy nevytváří stejné výsledky jako funkce jazyka Visual Basic, například při převodu `Boolean` k `Integer`. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  


Počínaje 15.8 jazyka Visual Basic, jehož výkon byl optimalizován převodu plovoucí-desetinnou-na-celé číslo se při předávání <xref:System.Single> nebo <xref:System.Double> hodnota vrácená pomocí následujících metod do jednoho z funkce pro převod celé číslo (`CByte`, `CShort`, `CInt`, `CLng`, `CSByte`, `CUShort`, `CUInt`, `CULng`):

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

Tyto optimalizace umožňuje kód, který provádí převody celé číslo, aby běžela dvakrát tak rychle hodně. Následující příklad znázorňuje tyto optimalizované převody plovoucí-desetinnou-na-celé číslo:

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
  
-   **Vynucení.** Obecně platí můžete použít funkce pro převod typů dat k vynucení výsledků na konkrétní datový typ spíše než výchozí datový typ operace. Například použít `CDec` přinutit desítkové aritmetické operace v případech, kdy jednoduchou přesností, dvojitá přesnost nebo celé číslo aritmetické by vám normálně trvalo místo.  
  
-   **Neúspěšné převody.** Pokud `expression` předaný funkci je mimo rozsah datového typu, na který se má převést <xref:System.OverflowException> vyvolá.  
  
-   **Zlomkové části.** Při převodu nonintegral hodnotu na integrální typ, funkce pro převod celé číslo (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, a `CUShort`) odeberte desetinná část a Zaokrouhlí hodnotu na nejbližší celé číslo.  
  
     Pokud zlomkové části je přesně 0,5, funkce pro převod celé číslo zaokrouhlit na nejbližší sudé celé číslo. Například 0,5 zaokrouhlí na 0 a 1.5 a 2.5, které obě zaokrouhlit na 2. To se někdy označuje jako *je bankovní zaokrouhlení*, a jejím účelem je jako kompenzaci za posun, která se můžou hromadit při přidávání mnoha těchto čísla společně.  
  
     `CInt` a `CLng` se liší od <xref:Microsoft.VisualBasic.Conversion.Int%2A> a <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funkce, které zkrátit, nikoli zaokrouhlit desetinnou část čísla. Navíc `Fix` a `Int` vždy vrátí hodnotu stejného datového typu jako předáním.  
  
-   **Datum a čas převody.** Použití <xref:Microsoft.VisualBasic.Information.IsDate%2A> funkce k určení, pokud hodnotu lze převést na datum a čas. `CDate` rozpozná literály data a času literály, ale není číselné hodnoty. K převodu jazyka Visual Basic 6.0 `Date` hodnota, která se `Date` hodnoty v jazyce Visual Basic 2005 nebo novější verze, můžete použít <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> metody.  
  
-   **Neutrální hodnoty data a času.** [Date – datový typ](../../../visual-basic/language-reference/data-types/date-data-type.md) vždy obsahuje informace o datu a času. Pro účely převodů, Visual Basic považuje za 1/1/0001 (od 1. ledna roku 1) *neutrální hodnotu* pro datum a 00:00:00 (půlnoc) bude neutrální hodnota pro dobu. Při převodu `Date` hodnotu na řetězec, `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci. Například, pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledek je "9:30:00: 00"; informace o datu je potlačeno. Informace o datu je však stále k dispozici v původní `Date` hodnotu a je možné obnovit pomocí funkcí, jako <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> funkce.  
  
-   **Citlivost jazykovou verzi.** Funkce pro převod typů zahrnující řetězce provádět převody na základě nastavení aktuální jazykové verze pro aplikaci. Například `CDate` rozpozná formáty kalendářního data podle nastavení národního prostředí vašeho systému. Je nutné zadat den, měsíc a rok ve správném pořadí pro vaše národní prostředí nebo datum nemusí být správně interpretovat. Pokud obsahuje řetězec den v týdnu, jako je například "Středa" nebyl rozpoznán formát dlouhého data.  
  
     Pokud je potřeba převést na nebo z řetězcové reprezentace hodnoty ve formátu kromě vlákna zadaného parametrem národní prostředí, nelze používat funkce pro převod typů jazyka Visual Basic. Chcete-li to provést, použijte `ToString(IFormatProvider)` a `Parse(String, IFormatProvider)` metody typu tuto hodnotu. Například použít <xref:System.Double.Parse%2A?displayProperty=nameWithType> při převodu na řetězec `Double`a použít <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na řetězec.  
  
## <a name="ctype-function"></a>CType – funkce  
 [Funkce CType](../../../visual-basic/language-reference/functions/ctype-function.md) přijímá jako druhý argument `typename`a převede `expression` k `typename`, kde `typename` může být datového typu, struktury, třídy nebo rozhraní, ke které existuje platný převod.  
  
 Porovnání `CType` s další typ převodu klíčová slova, přečtěte si téma [DirectCast operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) a [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>CBool – příklad  
 V následujícím příkladu `CBool` funkce převedete výrazy `Boolean` hodnoty. Pokud je výraz vyhodnocen na nenulovou hodnotu, `CBool` vrátí `True`; v opačném případě vrátí `False`.  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a>CByte – příklad  
 V následujícím příkladu `CByte` funkce převodu výrazu `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a>CChar – příklad  
 V následujícím příkladu `CChar` funkce pro převod první znak `String` výraz, který se `Char` typu.  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 Vstupní argument `CChar` musí být datového typu `Char` nebo `String`. Nemůžete použít `CChar` pro převod čísla na znak, protože `CChar` nemůže přijmout číselným datovým typem. Následující příklad získá číslo představující bod kódu. (kód znaku) a převede ho na odpovídající znak. Používá <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> funkce získat řetězec číslic, `CInt` pro převod řetězce na typ `Integer`, a `ChrW` převést číslo na typ `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a>CDate – příklad  
 V následujícím příkladu `CDate` funkce pro převod řetězců na `Date` hodnoty. Obecně není doporučeno pevně kódováno pomocí data a času jako řetězce (jak je znázorněno v tomto příkladu). Použijte literály data a času literály, například #Feb 12, 1969 # a # 4:45:23 hodin #, místo toho.  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a>CDbl – příklad  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a>CDec – příklad  
 V následujícím příkladu `CDec` funkce pro převod číselná hodnota, která `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a>Příklad CInt  
 V následujícím příkladu `CInt` funkce, která se převést hodnotu na `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  

## <a name="clng-example"></a>CLng – příklad
 V následujícím příkladu `CLng` funkce pro převod hodnot `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a>Příklad CObj  
 V následujícím příkladu `CObj` funkce pro převod číselná hodnota, která `Object`. `Object` Sám obsahují jenom ukazatel čtyř bajtů, která odkazuje na `Double` přiřazena hodnota.  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a>Csbyte – příklad  
 V následujícím příkladu `CSByte` funkce pro převod číselná hodnota, která `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a>Příklad CShort  
 V následujícím příkladu `CShort` funkce pro převod číselná hodnota, která `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a>CSng – příklad  
 V následujícím příkladu `CSng` funkce pro převod hodnot `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a>Příklad CStr  
 V následujícím příkladu `CStr` funkce pro převod číselná hodnota, která `String`.  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 V následujícím příkladu `CStr` funkce pro převod `Date` hodnoty `String` hodnoty.  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 `CStr` vždy vykreslí `Date` hodnotu ve standardní krátkého formátu pro aktuální národní prostředí, například "6/15/2003 4:35:47 PM". Ale `CStr` potlačí *neutrální hodnoty* z 1/1/0001 pro datum a 00:00:00 po dobu.  
  
 Další podrobnosti o hodnot vrácených `CStr`, naleznete v tématu [vrátit hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Cuint – příklad  
 V následujícím příkladu `CUInt` funkce pro převod číselná hodnota, která `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a>Culng – příklad  
 V následujícím příkladu `CULng` funkce pro převod číselná hodnota, která `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a>Cushort – příklad  
 V následujícím příkladu `CUShort` funkce pro převod číselná hodnota, která `UShort`.  
  
 [!code-vb[VbVbalrFunctions#18](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_18.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Int%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Fix%2A>  
 <xref:Microsoft.VisualBasic.Strings.Format%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Oct%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Str%2A>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [Převodní funkce](../../../visual-basic/language-reference/functions/conversion-functions.md)  
 [Převody typů v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
