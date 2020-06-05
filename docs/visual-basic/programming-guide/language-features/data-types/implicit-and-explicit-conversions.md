---
title: Implicitní a explicitní převody
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
ms.openlocfilehash: 2858dafd2531bd846ad89672348d103f385c4511
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84393828"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a>Implicitní a explicitní převody (Visual Basic)

*Implicitní převod* nevyžaduje ve zdrojovém kódu žádnou speciální syntaxi. V následujícím příkladu Visual Basic implicitně převede hodnotu `k` na hodnotu s plovoucí desetinnou čárkou s jednoduchou přesností, než ji přiřadíte do `q` .

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

*Explicitní převod* používá klíčové slovo konverze typu. Visual Basic poskytuje několik takových klíčových slov, která převeďte výraz v závorkách na požadovaný datový typ. Tato klíčová slova slouží jako funkce, ale kompilátor generuje kód vložený, takže provádění je mírně rychlejší než volání funkce.

V následujícím rozšíření výše uvedeného příkladu `CInt` převede klíčové slovo hodnotu `q` zpět na celé číslo před přiřazením do `k` .

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a>Klíčová slova převodu

Následující tabulka ukazuje dostupná klíčová slova pro převod.

|Typ – klíčové slovo převodu|Převede výraz na datový typ.|Povolené datové typy výrazu, který se má převést|
|---|---|---|
|`CBool`|[Boolean – datový typ](../../../language-reference/data-types/boolean-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `String` ,`Object`|
|`CByte`|[Byte – datový typ](../../../language-reference/data-types/byte-data-type.md)|Libovolný numerický typ (včetně `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CChar`|[Char – datový typ](../../../language-reference/data-types/char-data-type.md)|`String`, `Object`|
|`CDate`|[Date – datový typ](../../../language-reference/data-types/date-data-type.md)|`String`, `Object`|
|`CDbl`|[Double – datový typ](../../../language-reference/data-types/double-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CDec`|[Decimal – datový typ](../../../language-reference/data-types/decimal-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CInt`|[Integer – datový typ](../../../language-reference/data-types/integer-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CLng`|[Long – datový typ](../../../language-reference/data-types/long-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CObj`|[Datový typ objektu](../../../language-reference/data-types/object-data-type.md)|Libovolný typ|
|`CSByte`|[SByte – datový typ](../../../language-reference/data-types/sbyte-data-type.md)|Libovolný numerický typ (včetně `Byte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CShort`|[Short – datový typ](../../../language-reference/data-types/short-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CSng`|[Single – datový typ](../../../language-reference/data-types/single-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CStr`|[Datový typ String](../../../language-reference/data-types/string-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `Char` , `Char` pole, `Date` ,`Object`|
|`CType`|Typ zadaný za čárkou ( `,` )|Při převodu na *základní datový typ* (včetně pole základního typu) jsou stejné typy povolené pro odpovídající klíčové slovo převodu.<br /><br /> Při převodu na *složený datový typ*, rozhraní, které implementuje, a třídy, ze kterých dědí<br /><br /> Při převodu na třídu nebo strukturu, na které je přetížena `CType` , tato třída nebo struktura|
|`CUInt`|[UInteger – datový typ](../../../language-reference/data-types/uinteger-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CULng`|[ULong – datový typ](../../../language-reference/data-types/ulong-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|
|`CUShort`|[UShort – datový typ](../../../language-reference/data-types/ushort-data-type.md)|Libovolný číselný typ (včetně `Byte` , `SByte` a výčtové typy), `Boolean` , `String` ,`Object`|

## <a name="the-ctype-function"></a>Funkce CType

[Funkce CType](../../../language-reference/functions/ctype-function.md) pracuje na dvou argumentech. První je výraz, který má být převeden, a druhý je cílový datový typ nebo třída objektu. Všimněte si, že první argument musí být výraz, nikoli typ.

`CType`je *vložená funkce*, což znamená, že zkompilovaný kód provádí převod, často bez vyvolání volání funkce. Tím se zlepší výkon.

Porovnání `CType` s jinými klíčovými slovy pro převod typů naleznete v tématu [operátor DirectCast](../../../language-reference/operators/directcast-operator.md) a [operátor TryCast](../../../language-reference/operators/trycast-operator.md).

### <a name="elementary-types"></a>Základní typy

Následující příklad ukazuje použití `CType` .

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a>Složené typy

Můžete použít `CType` k převodu hodnot na složené datové typy i na základní typy. Můžete jej také použít k převeďte třídu objektu na typ jednoho z jeho rozhraní, jak je uvedeno v následujícím příkladu.

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a>Typy polí

`CType`lze také převést datové typy pole, jak je uvedeno v následujícím příkladu.

```vb
Dim v() As classV
Dim obArray() As Object
' Assume some object array has been assigned to obArray.
' Check for run-time type compatibility.
If TypeOf obArray Is classV()
    ' obArray can be converted to classV.
    v = CType(obArray, classV())
End If
```

Další informace a příklad najdete v tématu [převody polí](array-conversions.md).

### <a name="types-defining-ctype"></a>Typy definující CType

Můžete definovat `CType` pro třídu nebo strukturu, kterou jste definovali. To umožňuje převést hodnoty do a z typu vaší třídy nebo struktury. Další informace a příklad naleznete v tématu [How to: define a Conversion operátor](../procedures/how-to-define-a-conversion-operator.md).

> [!NOTE]
> Hodnoty používané s klíčovým slovem pro převod musí být platné pro cílový datový typ nebo dojde k chybě. Například pokud se pokusíte převést `Long` na `Integer` , hodnota `Long` musí být v rámci platného rozsahu pro `Integer` datový typ.

> [!CAUTION]
> Určení `CType` pro převod z jednoho typu třídy na jiný se v době běhu nezdařila, pokud typ zdroje není odvozen z cílového typu. Taková chyba vyvolá <xref:System.InvalidCastException> výjimku.

Pokud je však jeden z typů struktura nebo třída, kterou jste definovali, a pokud jste definovali `CType` v této struktuře nebo třídě, převod může být úspěšný, pokud splňuje požadavky vašeho `CType` . Viz [How to: define a Conversion operátor](../procedures/how-to-define-a-conversion-operator.md).

Provádění explicitního převodu je také označováno jako *přetypování* výrazu na daný datový typ nebo třídu objektu.

## <a name="see-also"></a>Viz také

- [Převody typů v jazyce Visual Basic](type-conversions.md)
- [Převody mezi řetězci a ostatními typy](conversions-between-strings-and-other-types.md)
- [Postupy: Převedení objektu na jiný typ v jazyce Visual Basic](how-to-convert-an-object-to-another-type.md)
- [Struktury](structures.md)
- [Datové typy](../../../language-reference/data-types/index.md)
- [Funkce pro převod typů](../../../language-reference/functions/type-conversion-functions.md)
- [Řešení potíží s datovými typy](troubleshooting-data-types.md)
