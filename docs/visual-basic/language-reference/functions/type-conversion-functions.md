---
title: "Funkce pro převod typů (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 117cd4ce038a533715bbc86558545f0f223dd149
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-conversion-functions-visual-basic"></a>Funkce pro převod typů (Visual Basic)
Tyto funkce jsou kompilované vložené, což znamená, že kód převod je součástí kód, který se vyhodnotí výraz. Někdy je žádná volání procedury k provádění převodu, což zvyšuje výkon. Jednotlivé funkce převede výraz na určitého datového typu.  
  
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
 Požadováno. Jakýkoli výraz zdrojového datového typu.  
  
## <a name="return-value-data-type"></a>Vrátí hodnotu datový typ  
 Název funkce určuje datový typ hodnoty, které se vrátí, jak je znázorněno v následující tabulce.  
  
|Název funkce|Návratový datový typ|Rozsah pro `expression` argument|  
|-------------------|----------------------|-------------------------------------|  
|`CBool`|[Boolean – datový typ](../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Libovolný platný `Char` nebo `String` nebo číselný výraz.|  
|`CByte`|[Byte – datový typ](../../../visual-basic/language-reference/data-types/byte-data-type.md)|0 do 255 (bez znaménka); jsou zaokrouhleny zlomkové části. <sup>1</sup>|  
|`CChar`|[Char – datový typ](../../../visual-basic/language-reference/data-types/char-data-type.md)|Libovolný platný `Char` nebo `String` výraz; pouze první znak `String` je převést; hodnota může být 0 až 65535 (bez znaménka).|  
|`CDate`|[Date – datový typ](../../../visual-basic/language-reference/data-types/date-data-type.md)|Platný reprezentace data a času.|  
|`CDbl`|[Double – datový typ](../../../visual-basic/language-reference/data-types/double-data-type.md)|-1.79769313486231570E + 308 prostřednictvím - 4.94065645841246544E-324 pro záporné hodnoty; 4.94065645841246544E-324 prostřednictvím 1.79769313486231570E + 308 kladné hodnoty.|  
|`CDec`|[Decimal – datový typ](../../../visual-basic/language-reference/data-types/decimal-data-type.md)|+/-79,228,162,514,264,337,593,543,950,335 pro škálovat nula čísla, který je čísla bez desetinných míst. Pro 28 desetinná čísla je rozsah +/-7,9228162514264337593543950335. Nejmenší možný počet nenulové je 0,0000000000000000000000000001 (+/-1E-28).|  
|`CInt`|[Integer – datový typ](../../../visual-basic/language-reference/data-types/integer-data-type.md)|-2,147,483,648 prostřednictvím 2 147 483 647; jsou zaokrouhleny zlomkové části. <sup>1</sup>|  
|`CLng`|[Long – datový typ](../../../visual-basic/language-reference/data-types/long-data-type.md)|-9,223,372,036,854,775,808 prostřednictvím 9,223,372,036,854,775,807; jsou zaokrouhleny zlomkové části. <sup>1</sup>|  
|`CObj`|[Object – datový typ](../../../visual-basic/language-reference/data-types/object-data-type.md)|Jakýkoli platný výraz.|  
|`CSByte`|[SByte – datový typ](../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|-128 až 127; jsou zaokrouhleny zlomkové části. <sup>1</sup>|  
|`CShort`|[Short – datový typ](../../../visual-basic/language-reference/data-types/short-data-type.md)|-32 768 do 32 767; jsou zaokrouhleny zlomkové části. <sup>1</sup>|  
|`CSng`|[Single – datový typ](../../../visual-basic/language-reference/data-types/single-data-type.md)|-3.402823E + 38 prostřednictvím - 1, 401298E-45 pro záporné hodnoty; 1, 401298E-45 prostřednictvím 3.402823E + 38 kladné hodnoty.|  
|`CStr`|[String – datový typ](../../../visual-basic/language-reference/data-types/string-data-type.md)|Vrátí pro `CStr` závisí na `expression` argument. V tématu [návratové hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).|  
|`CUInt`|[Uinteger – datový typ](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|0 až 4 294 967 295 (bez znaménka); jsou zaokrouhleny zlomkové části. <sup>1</sup>|  
|`CULng`|[Ulong – datový typ](../../../visual-basic/language-reference/data-types/ulong-data-type.md)|0 až 18,446,744,073,709,551,615 (bez znaménka); jsou zaokrouhleny zlomkové části. <sup>1</sup>|  
|`CUShort`|[Ushort – datový typ](../../../visual-basic/language-reference/data-types/ushort-data-type.md)|0 až 65 535 (bez znaménka); jsou zaokrouhleny zlomkové části. <sup>1</sup>|  
  
 <sup>1</sup> zlomkové části mohou podléhat zvláštním typem zaokrouhlení volané *banker je zaokrouhlení*. Další informace najdete v části "Poznámky".  
  
## <a name="remarks"></a>Poznámky  
 Platí, měli byste použít funkce pro převod typů jazyka Visual Basic přednostně metod rozhraní .NET Framework, jako `ToString()`, buď na <xref:System.Convert> třídy nebo na strukturou jednotlivých typů nebo třídy. Funkce jazyka Visual Basic jsou navrženy pro optimální interakci s kód jazyka Visual Basic a také provádění zdrojového kódu kratší a snadněji číst. Kromě toho převod metod rozhraní .NET Framework vždy nevedou stejné výsledky jako funkce jazyka Visual Basic, například při převádění `Boolean` k `Integer`. Další informace najdete v tématu [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).  
  
## <a name="behavior"></a>Chování  
  
-   **Převod.** Obecně platí můžete funkce pro převod typů dat coerce výsledek operace datový typ. spíše než výchozí typ data. Například použít `CDec` vynutit decimal aritmetické v případech, kde jednoduchou přesností, dvojitá přesnost nebo celé číslo aritmetické by za normálních okolností probíhat.  
  
-   **Převody se nezdařilo.** Pokud `expression` předaný funkci je mimo rozsah datového typu, na která se má být převeden, <xref:System.OverflowException> dojde.  
  
-   **Zlomkové části.** Při převodu nonintegral hodnotu na integrální typ, funkce pro převod celé číslo (`CByte`, `CInt`, `CLng`, `CSByte`, `CShort`, `CUInt`, `CULng`, a `CUShort`) odebrat zlomkové součástí a zaokrouhlit hodnotu na nejbližší celé číslo.  
  
     Pokud zlomkové části přesně 0,5, funkce pro převod celé číslo zaokrouhlit, aby nejbližší sudé celé číslo. Například 0,5 zaokrouhlí na 0 a 1.5 a 2.5, které obě zaokrouhlit na 2. To se někdy nazývá *banker je zaokrouhlení*, a jejím účelem je kompenzovat odchylka, které můžou hromadit při přidávání mnoho taková čísla společně.  
  
     `CInt`a `CLng` se liší od <xref:Microsoft.VisualBasic.Conversion.Int%2A> a <xref:Microsoft.VisualBasic.Conversion.Fix%2A> funkce, které zkrátit, nikoli zaokrouhlit zlomkové části čísla. Navíc `Fix` a `Int` vždy vrátí hodnotu stejný datový typ. jako předáte v.  
  
-   **Datum a čas převody.** Použití <xref:Microsoft.VisualBasic.Information.IsDate%2A> funkce k určení, pokud hodnotu lze převést datum a čas. `CDate`rozpozná literály data a času literály, ale není číselné hodnoty. Převést Visual Basic 6.0 `Date` hodnotu `Date` hodnotu v jazyce Visual Basic 2005 nebo novější verze, můžete použít <xref:System.DateTime.FromOADate%2A?displayProperty=nameWithType> metoda.  
  
-   **Neutrální hodnoty data a času.** [Date – datový typ](../../../visual-basic/language-reference/data-types/date-data-type.md) vždy obsahuje informace o datu a času. Pro účely převod typů, Visual Basic považuje za 1/1/0001 (1. ledna roku 1) *neutrální hodnota* pro datum a 00:00:00 (půlnoc) se má nastavit neutrální hodnota pro dobu. Pokud převedete `Date` hodnotu na řetězec `CStr` nezahrnuje neutrální hodnoty ve výsledném řetězci. Například, pokud převedete `#January 1, 0001 9:30:00#` na řetězec, výsledkem je "9:30:00: 00"; potlačeno informace o datu. Informace o datu je však stále nachází na původní `Date` hodnotu a je možné obnovit s funkcemi, jako například <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> funkce.  
  
-   **Jazyková verze velkých a malých písmen.** Funkce pro převod typů zahrnující řetězce provést převody na základě aktuální nastavení jazykové verze pro aplikaci. Například `CDate` rozpoznává formáty data podle nastavení národního prostředí vašeho systému. Je nutné zadat den, měsíc a rok ve správném pořadí pro národní prostředí nebo datum nemusí být správně interpretovat. Pokud obsahuje řetězec den v týdnu, jako je například "Středa" nebyl rozpoznán formát dlouhého data.  
  
     Pokud musíte převést do nebo z řetězcovou reprezentaci hodnoty ve formátu, než jaké byla určená elementem národní prostředí, nebudete moct používat funkce pro převod typů jazyka Visual Basic. Chcete-li to provést, použijte `ToString(IFormatProvider)` a `Parse(String, IFormatProvider)` metody typu tuto hodnotu. Například použít <xref:System.Double.Parse%2A?displayProperty=nameWithType> při převodu řetězce `Double`a použijte <xref:System.Double.ToString%2A?displayProperty=nameWithType> při převodu hodnoty typu `Double` na řetězec.  
  
## <a name="ctype-function"></a>CType – funkce  
 [CType – funkce](../../../visual-basic/language-reference/functions/ctype-function.md) použije druhý argument, `typename`a převede `expression` k `typename`, kde `typename` můžou být datový typ, struktura, třída nebo rozhraní, na kterou existuje platná převod.  
  
 Porovnání `CType` s další typ převodu klíčová slova, přečtěte si téma [DirectCast – operátor](../../../visual-basic/language-reference/operators/directcast-operator.md) a [TryCast – operátor](../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
## <a name="cbool-example"></a>CBool – příklad  
 Následující příklad používá `CBool` funkce pro převod výrazy a `Boolean` hodnoty. Pokud je výsledkem výrazu nenulovou hodnotu, `CBool` vrátí `True`, jinak vrátí hodnotu `False`.  
  
 [!code-vb[VbVbalrFunctions#1](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_1.vb)]  
  
## <a name="cbyte-example"></a>CByte – příklad  
 Následující příklad používá `CByte` funkce pro převod výraz, který se `Byte`.  
  
 [!code-vb[VbVbalrFunctions#2](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_2.vb)]  
  
## <a name="cchar-example"></a>CChar – příklad  
 Následující příklad používá `CChar` funkce pro převod první znak `String` výraz, který se `Char` typu.  
  
 [!code-vb[VbVbalrFunctions#3](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_3.vb)]  
  
 Vstupní argument `CChar` musí být datového typu `Char` nebo `String`. Nemůžete použít `CChar` k převodu číslo znak, protože `CChar` nemůže přijímat číselným datovým typem. Následující příklad získá číslo představující bod kódu (kód znaku) a převede jej na odpovídající znak. Použije <xref:Microsoft.VisualBasic.Interaction.InputBox%2A> funkce získat řetězec číslic, `CInt` se převést řetězec na typ `Integer`, a `ChrW` převést na typ číslo `Char`.  
  
 [!code-vb[VbVbalrFunctions#4](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_4.vb)]  
  
## <a name="cdate-example"></a>CDate – příklad  
 Následující příklad používá `CDate` funkce pro převod řetězců na `Date` hodnoty. Obecně se nedoporučuje pevně kódováno data a časy jako řetězce (jak je uvedeno v tomto příkladu). Použijte literály datum a čas literály, jako je například #Feb 12, &#1969; a # 4:45:23 PM #, místo toho.  
  
 [!code-vb[VbVbalrFunctions#5](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_5.vb)]  
  
## <a name="cdbl-example"></a>CDbl – příklad  
 [!code-vb[VbVbalrFunctions#6](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_6.vb)]  
  
## <a name="cdec-example"></a>CDec – příklad  
 Následující příklad používá `CDec` funkce pro převod číselná hodnota, která `Decimal`.  
  
 [!code-vb[VbVbalrFunctions#7](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_7.vb)]  
  
## <a name="cint-example"></a>CInt – příklad  
 Následující příklad používá `CInt` funkce, která se převést hodnotu na `Integer`.  
  
 [!code-vb[VbVbalrFunctions#8](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_8.vb)]  
  
## <a name="clng-example"></a>CLng – příklad  
 Následující příklad používá `CLng` funkce pro převod hodnoty na `Long`.  
  
 [!code-vb[VbVbalrFunctions#9](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_9.vb)]  
  
## <a name="cobj-example"></a>Příklad CObj  
 Následující příklad používá `CObj` funkce pro převod číselná hodnota, která `Object`. `Object` Proměnnou obsahují jenom ukazatel čtyř bajtů, který odkazuje na `Double` hodnotu přiřazenou k němu.  
  
 [!code-vb[VbVbalrFunctions#10](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_10.vb)]  
  
## <a name="csbyte-example"></a>Csbyte – příklad  
 Následující příklad používá `CSByte` funkce pro převod číselná hodnota, která `SByte`.  
  
 [!code-vb[VbVbalrFunctions#11](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_11.vb)]  
  
## <a name="cshort-example"></a>Příklad CShort  
 Následující příklad používá `CShort` funkce pro převod číselná hodnota, která `Short`.  
  
 [!code-vb[VbVbalrFunctions#12](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_12.vb)]  
  
## <a name="csng-example"></a>CSng – příklad  
 Následující příklad používá `CSng` funkce pro převod hodnoty na `Single`.  
  
 [!code-vb[VbVbalrFunctions#13](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_13.vb)]  
  
## <a name="cstr-example"></a>Příklad CStr  
 Následující příklad používá `CStr` funkce pro převod číselná hodnota, která `String`.  
  
 [!code-vb[VbVbalrFunctions#14](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_14.vb)]  
  
 Následující příklad používá `CStr` funkce pro převod `Date` hodnoty k `String` hodnoty.  
  
 [!code-vb[VbVbalrFunctions#15](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_15.vb)]  
  
 `CStr`vždy vykreslí `Date` hodnotu ve formátu standard krátké pro aktuální národní prostředí, například "6/15/2003 4:35:47 PM". Ale `CStr` potlačí *neutrální hodnoty* z 1/1/0001 pro datum a 00:00:00 po dobu.  
  
 Další podrobnosti o hodnot vrácených `CStr`, najdete v části [vrátit hodnoty pro funkci CStr](../../../visual-basic/language-reference/functions/return-values-for-the-cstr-function.md).  
  
## <a name="cuint-example"></a>Cuint – příklad  
 Následující příklad používá `CUInt` funkce pro převod číselná hodnota, která `UInteger`.  
  
 [!code-vb[VbVbalrFunctions#16](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_16.vb)]  
  
## <a name="culng-example"></a>Culng – příklad  
 Následující příklad používá `CULng` funkce pro převod číselná hodnota, která `ULong`.  
  
 [!code-vb[VbVbalrFunctions#17](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/type-conversion-functions_17.vb)]  
  
## <a name="cushort-example"></a>Cushort – příklad  
 Následující příklad používá `CUShort` funkce pro převod číselná hodnota, která `UShort`.  
  
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
