---
title: "Implicitní a explicitní převody (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6e9dd698e1cc84464cd12d33767feec960c511ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Implicitní a explicitní převody (Visual Basic)
*Implicitní převod* nevyžaduje žádnou zvláštní syntaxi ve zdrojovém kódu. V následujícím příkladu [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] implicitně převede hodnotu `k` na hodnotu s plovoucí desetinnou čárkou jednoduchou přesností před přiřazením jeho `q`.  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 *Explicitní převod* používá klíčového slova převodu typu. [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]poskytuje několik takové klíčová slova, která coerce výrazu v závorkách na požadovaný datový typ. Tato klíčová slova fungovat stejně jako funkce, ale kompilátor generuje vložený kód tak, aby provádění mírně rychlejší než se volání funkce.  
  
 V následující rozšíření v předchozím příkladu `CInt` – klíčové slovo převede hodnotu `q` zpět na celé číslo před přiřazením jeho `k`.  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a>Klíčová slova převodu  
 V následující tabulce jsou klíčová slova převodu k dispozici.  
  
|Typ převodu – klíčové slovo|Převede výraz na datový typ|Povolené datové typy výraz, který má být převeden|  
|---|---|---|  
|`CBool`|[Boolean – datový typ](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `String`,`Object`|  
|`CByte`|[Byte – datový typ](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|Všechny číselného typu (včetně `SByte` a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CChar`|[Char – datový typ](../../../../visual-basic/language-reference/data-types/char-data-type.md)|`String`, `Object`|  
|`CDate`|[Date – datový typ](../../../../visual-basic/language-reference/data-types/date-data-type.md)|`String`, `Object`|  
|`CDbl`|[Double – datový typ](../../../../visual-basic/language-reference/data-types/double-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CDec`|[Decimal – datový typ](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CInt`|[Integer – datový typ](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CLng`|[Long – datový typ](../../../../visual-basic/language-reference/data-types/long-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CObj`|[Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md)|Jakýkoli typ|  
|`CSByte`|[SByte – datový typ](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|Všechny číselného typu (včetně `Byte` a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CShort`|[Short – datový typ](../../../../visual-basic/language-reference/data-types/short-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CSng`|[Single – datový typ](../../../../visual-basic/language-reference/data-types/single-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CStr`|[String – datový typ](../../../../visual-basic/language-reference/data-types/string-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `Char`, `Char` pole, `Date`,`Object`|  
|`CType`|Zadaný typ následující čárkou (`,`)|Při převodu na *základní datový typ* (včetně pole Základní typ), stejné typy jako povolený pro odpovídající převod klíčové slovo<br /><br /> Při převodu na *složeného datového typu*, implementuje rozhraní a třídy, ze kterých dědí<br /><br /> Při převodu na třídu nebo strukturu, ve kterém mají přetížený `CType`, že třídu nebo strukturu|  
|`CUInt`|[Uinteger – datový typ](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CULng`|[Ulong – datový typ](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
|`CUShort`|[Ushort – datový typ](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|Všechny číselného typu (včetně `Byte`, `SByte`a vytvořit její výčet typů), `Boolean`, `String`,`Object`|  
  
## <a name="the-ctype-function"></a>CType – funkce  
 [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) funguje na dva argumenty. První je výraz, který má být převeden, a druhá dat cílové třídy typu nebo objektu. Všimněte si, že první argument musí být výraz není typu.  
  
 `CType`je *vložená funkce*znamená zkompilovaný kód umožňuje převod, často bez generování událostí funkce volání. To zvyšuje výkon.  
  
 Porovnání `CType` s další typ převodu klíčová slova, přečtěte si téma [DirectCast – operátor](../../../../visual-basic/language-reference/operators/directcast-operator.md) a [TryCast – operátor](../../../../visual-basic/language-reference/operators/trycast-operator.md).  
  
### <a name="elementary-types"></a>Základní typy  
 Následující příklad ukazuje použití `CType`.  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a>Složené typy  
 Můžete použít `CType` k převodu hodnoty na také složené datové typy, základní typy. Můžete ji použít i k coerce třídu objektu typu některého z rozhraní, jako v následujícím příkladu.  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a>Typy polí  
 `CType`Můžete také převést pole datové typy, jako v následujícím příkladu.  
  
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
  
 Další informace a příklady naleznete v tématu [převody pole](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).  
  
### <a name="types-defining-ctype"></a>Definování CType typy  
 Můžete definovat `CType` na třídu nebo strukturu jste definovali. Tímto způsobem lze převést hodnoty do a z typ třídu nebo strukturu. Další informace a příklady naleznete v tématu [postupy: definice operátora převodu](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
> [!NOTE]
>  Hodnoty používané s klíčovým slovem převod musí být platná pro cílový datový typ, nebo dojde k chybě. Například, pokud se pokusíte převést `Long` k `Integer`, hodnota `Long` musí být v platném rozsahu pro `Integer` datový typ.  
  
> [!CAUTION]
>  Určení `CType` převést z typu jednu třídu jiné selže v době běhu Pokud typ zdroje není odvozena od typ cíle. Takové selhání vyvolá <xref:System.InvalidCastException> výjimka.  
  
 Ale pokud jeden z typů struktura nebo třídy, které jste definovali, a pokud jste definovali `CType` na struktur nebo třídu, můžete převodu z úspěšné, v případě, že splňují požadavky vašeho `CType`. V tématu [postupy: definice operátora převodu](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).  
  
 Provádění explicitní převod je také označován jako *přetypování* výraz, který se daná data typu nebo objektu třídy.  
  
## <a name="see-also"></a>Viz také  
 [Převody typů v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Převody mezi řetězci a ostatními typy](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)  
 [Postupy: převedení objektu na jiný typ v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Řešení potíží s datové typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
