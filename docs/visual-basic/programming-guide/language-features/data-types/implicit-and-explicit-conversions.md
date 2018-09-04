---
title: Implicitní a explicitní převody (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [Visual Basic], type
- variables [Visual Basic], changing data type
- casting
- conversions [Visual Basic], data type
- type conversion [Visual Basic], implicit conversions
- CType function [Visual Basic], conversions
- casting, data types
- data type conversion [Visual Basic], explicit
- type conversion [Visual Basic], explicit conversions
- data types [Visual Basic], casting
- conversions [Visual Basic], implicit
- explicit data type conversions [Visual Basic]
- conversions [Visual Basic]
- changing data types [Visual Basic]
- conversions [Visual Basic], explicit
- data type conversion [Visual Basic], implicit
- implicit data type conversions [Visual Basic]
ms.assetid: 77de1659-af8a-492c-967e-e7ef60ccce66
ms.openlocfilehash: 09d96b304ba3bcf2a9de2812ce37ae69dba73a41
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396591"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Implicitní a explicitní převody (Visual Basic)
*Implicitní převod* nevyžaduje žádnou zvláštní syntaxi ve zdrojovém kódu. V následujícím příkladu, Visual Basic implicitně převede hodnotu `k` na jednoduchou přesnost s plovoucí desetinnou čárkou hodnotu před přiřazením na `q`.  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 *Explicitní převod* používá klíčové slovo převodu typu. Visual Basic poskytuje několik takových klíčová slova, která vynucení výrazu v závorkách do požadovaného datového typu. Tato klíčová slova fungují jako funkce, ale kompilátor generuje vložený kód, takže spuštění je mírně rychlejší než pomocí volání funkce.  
  
 Následující rozšíření v předchozím příkladu `CInt` – klíčové slovo převede hodnotu `q` zpět na celé číslo než ji přiřadíte `k`.  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 V následující tabulce jsou uvedeny klíčová slova převodu k dispozici.  
  
|Typ převodu – klíčové slovo|Převede výraz na datový typ|Povolené datové typy výrazů má být převeden|  
|---|---|---|  
|`CBool`|[Datový typ Boolean](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `String`, `Object`|  
|`CByte`|[Datový typ Byte](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Jakýkoli číselný typ (včetně `SByte` a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CChar`|[Datový typ Char](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Datový typ Date](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Datový typ Double](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CDec`|[Datový typ Decimal](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CInt`|[Datový typ Integer](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CLng`|[Datový typ Long](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CObj`|[Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Jakýkoli typ|  
|`CSByte`|[Datový typ SByte](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Jakýkoli číselný typ (včetně `Byte` a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CShort`|[Datový typ Short](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CSng`|[Datový typ Single](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CStr`|[Datový typ String](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `Char`, `Char` pole, `Date`, `Object`|  
|`CType`|Zadaný typ za čárkou (`,`)|Při převodu na *základní datový typ* (včetně pole Základní typu), stejné typy povolen pro odpovídající klíčového slova převodu<br /><br /> Při převodu *složené datový typ*, implementuje rozhraní a třídy, ze které dědí<br /><br /> Při převodu na třídy nebo struktury, ve kterém můžete mít přetížené `CType`, této třídě nebo struktuře|  
|`CUInt`|[Datový typ UInteger](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CULng`|[Datový typ ULong](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
|`CUShort`|[Datový typ UShort](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`|  
  
## <a name="the-ctype-function"></a>CType – funkce  
 [Funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pracuje na dva argumenty. První je výraz, který má být převeden, a druhý je data cílové třídy typu nebo objekt. Všimněte si, že první argument musí být výraz, ne typ.  
  
 `CType` je *vložená funkce*, což znamená zkompilovaný kód provede převod, často bez generování událostí funkce volání. To zvyšuje výkon.  
  
 Porovnání `CType` s další typ převodu klíčová slova, přečtěte si téma [DirectCast operátor](../../../../visual-basic/language-reference/operators/directcast-operator.md) a [TryCast – operátor](../../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
### <a name="elementary-types"></a>Základní typy  
 Následující příklad ukazuje použití `CType`.  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>Složené typy  
 Můžete použít `CType` k převodu hodnoty na složené datové typy a také o základních typů. Můžete také použít ho k vynucení třídu objektu na typ jednoho z jeho rozhraní, jako v následujícím příkladu.  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>Typy polí  
 `CType` Můžete také převést pole datové typy, jako v následujícím příkladu.  
  
```  
Dim v() As classV  
Dim obArray() As Object  
' Assume some object array has been assigned to obArray.  
' Check for run-time type compatibility.  
If TypeOf obArray Is classV()  
    ' obArray can be converted to classV.  
    v = CType(obArray, classV())  
End If  
```  
  
 Další informace a příklad najdete v tématu [převody pole](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).  
  
### <a name="types-defining-ctype"></a>Typy definování CType  
 Můžete definovat `CType` na třídy nebo struktury, které jste definovali. To umožňuje převod hodnoty do a z typu třídy nebo struktury. Další informace a příklad najdete v tématu [postupy: definice operátora převodu](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
> [!NOTE]
>  Použít s klíčovým slovem převod hodnoty musí být platná pro cílový datový typ nebo dojde k chybě. Například, pokud se pokusíte převést `Long` k `Integer`, hodnota `Long` musí být v platném rozsahu pro `Integer` datového typu.  
  
> [!CAUTION]
>  Určení `CType` převést z jedné třídy typu na jiný selže v době běhu Pokud zdrojový typ není odvozen z cílového typu. Takové selhání vyvolá <xref:System.InvalidCastException> výjimky.  
  
 Nicméně je-li jeden z typů struktury nebo třídy, které jste definovali, a pokud jste definovali `CType` v této struktury nebo třídy, může převod úspěšné, pokud splňuje požadavky vaší `CType`. Zobrazit [postupy: definice operátora převodu](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
 Provedení explicitního převodu se taky říká *přetypování* výraz, který se daná data typu nebo objekt třídy.  
  
## <a name="see-also"></a>Viz také  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Převody mezi řetězci a ostatními typy](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Postupy: převedení objektu na jiný typ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
