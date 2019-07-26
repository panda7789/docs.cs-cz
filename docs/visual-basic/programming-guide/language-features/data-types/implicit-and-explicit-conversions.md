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
ms.openlocfilehash: 4bcf2d76a2983294f244b72f286842a92fb5e64e
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512869"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="8b6c6-102">Implicitní a explicitní převody (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-102">Implicit and Explicit Conversions (Visual Basic)</span></span>

<span data-ttu-id="8b6c6-103">*Implicitní převod* nevyžaduje ve zdrojovém kódu žádnou speciální syntaxi.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="8b6c6-104">V následujícím příkladu Visual Basic implicitně převede hodnotu `k` na hodnotu s plovoucí desetinnou čárkou s jednoduchou přesností, než ji přiřadíte do. `q`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>

```vb
Dim k As Integer
Dim q As Double
' Integer widens to Double, so you can do this with Option Strict On.
k = 432
q = k
```

<span data-ttu-id="8b6c6-105">*Explicitní převod* používá klíčové slovo konverze typu.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="8b6c6-106">Visual Basic poskytuje několik takových klíčových slov, která převeďte výraz v závorkách na požadovaný datový typ.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="8b6c6-107">Tato klíčová slova slouží jako funkce, ale kompilátor generuje kód vložený, takže provádění je mírně rychlejší než volání funkce.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>

<span data-ttu-id="8b6c6-108">V následujícím rozšíření výše uvedeného příkladu `CInt` převede klíčové slovo `q` hodnotu zpět na celé číslo před přiřazením do `k`.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>

```vb
' q had been assigned the value 432 from k.
q = Math.Sqrt(q)
k = CInt(q)
' k now has the value 21 (rounded square root of 432).
```

## <a name="conversion-keywords"></a><span data-ttu-id="8b6c6-109">Klíčová slova převodu</span><span class="sxs-lookup"><span data-stu-id="8b6c6-109">Conversion Keywords</span></span>

<span data-ttu-id="8b6c6-110">Následující tabulka ukazuje dostupná klíčová slova pro převod.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-110">The following table shows the available conversion keywords.</span></span>

|<span data-ttu-id="8b6c6-111">Typ – klíčové slovo převodu</span><span class="sxs-lookup"><span data-stu-id="8b6c6-111">Type conversion keyword</span></span>|<span data-ttu-id="8b6c6-112">Převede výraz na datový typ.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-112">Converts an expression to data type</span></span>|<span data-ttu-id="8b6c6-113">Povolené datové typy výrazu, který se má převést</span><span class="sxs-lookup"><span data-stu-id="8b6c6-113">Allowable data types of expression to be converted</span></span>|
|---|---|---|
|`CBool`|[<span data-ttu-id="8b6c6-114">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="8b6c6-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="8b6c6-115">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|
|`CByte`|[<span data-ttu-id="8b6c6-116">Datový typ Byte</span><span class="sxs-lookup"><span data-stu-id="8b6c6-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="8b6c6-117">Libovolný numerický typ (včetně `SByte` a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CChar`|[<span data-ttu-id="8b6c6-118">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="8b6c6-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="8b6c6-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-119">`String`, `Object`</span></span>|
|`CDate`|[<span data-ttu-id="8b6c6-120">Datový typ Date</span><span class="sxs-lookup"><span data-stu-id="8b6c6-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="8b6c6-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-121">`String`, `Object`</span></span>|
|`CDbl`|[<span data-ttu-id="8b6c6-122">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="8b6c6-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="8b6c6-123">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CDec`|[<span data-ttu-id="8b6c6-124">Datový typ Decimal</span><span class="sxs-lookup"><span data-stu-id="8b6c6-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="8b6c6-125">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CInt`|[<span data-ttu-id="8b6c6-126">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="8b6c6-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="8b6c6-127">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CLng`|[<span data-ttu-id="8b6c6-128">Datový typ Long</span><span class="sxs-lookup"><span data-stu-id="8b6c6-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="8b6c6-129">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CObj`|[<span data-ttu-id="8b6c6-130">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="8b6c6-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="8b6c6-131">Libovolný typ</span><span class="sxs-lookup"><span data-stu-id="8b6c6-131">Any type</span></span>|
|`CSByte`|[<span data-ttu-id="8b6c6-132">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="8b6c6-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="8b6c6-133">Libovolný numerický typ (včetně `Byte` a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CShort`|[<span data-ttu-id="8b6c6-134">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="8b6c6-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="8b6c6-135">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CSng`|[<span data-ttu-id="8b6c6-136">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="8b6c6-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="8b6c6-137">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CStr`|[<span data-ttu-id="8b6c6-138">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="8b6c6-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="8b6c6-139">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `Char`, `Char` pole, `Date`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|
|`CType`|<span data-ttu-id="8b6c6-140">Typ zadaný za čárkou (`,`)</span><span class="sxs-lookup"><span data-stu-id="8b6c6-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="8b6c6-141">Při převodu na *základní datový typ* (včetně pole základního typu) jsou stejné typy povolené pro odpovídající klíčové slovo převodu.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="8b6c6-142">Při převodu na *složený datový typ*, rozhraní, které implementuje, a třídy, ze kterých dědí</span><span class="sxs-lookup"><span data-stu-id="8b6c6-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="8b6c6-143">Při převodu na třídu nebo strukturu, na které je přetížena `CType`, tato třída nebo struktura</span><span class="sxs-lookup"><span data-stu-id="8b6c6-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|
|`CUInt`|[<span data-ttu-id="8b6c6-144">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="8b6c6-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="8b6c6-145">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CULng`|[<span data-ttu-id="8b6c6-146">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="8b6c6-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="8b6c6-147">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|
|`CUShort`|[<span data-ttu-id="8b6c6-148">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="8b6c6-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="8b6c6-149">Libovolný číselný typ (včetně `Byte`, `SByte`a výčtové typy), `Boolean`, `String`,`Object`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|

## <a name="the-ctype-function"></a><span data-ttu-id="8b6c6-150">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="8b6c6-150">The CType Function</span></span>

<span data-ttu-id="8b6c6-151">[Funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pracuje na dvou argumentech.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="8b6c6-152">První je výraz, který má být převeden, a druhý je cílový datový typ nebo třída objektu.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="8b6c6-153">Všimněte si, že první argument musí být výraz, nikoli typ.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-153">Note that the first argument must be an expression, not a type.</span></span>

<span data-ttu-id="8b6c6-154">`CType`je *vložená funkce*, což znamená, že zkompilovaný kód provádí převod, často bez vyvolání volání funkce.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="8b6c6-155">Tím se zlepší výkon.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-155">This improves performance.</span></span>

<span data-ttu-id="8b6c6-156">Porovnání `CType` s jinými klíčovými slovy pro převod typů naleznete v tématu [operátor DirectCast](../../../../visual-basic/language-reference/operators/directcast-operator.md) a [operátor TryCast](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="8b6c6-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>

### <a name="elementary-types"></a><span data-ttu-id="8b6c6-157">Základní typy</span><span class="sxs-lookup"><span data-stu-id="8b6c6-157">Elementary Types</span></span>

<span data-ttu-id="8b6c6-158">Následující příklad ukazuje použití `CType`.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-158">The following example demonstrates the use of `CType`.</span></span>

```vb
k = CType(q, Integer)
' The following statement coerces w to the specific object class Label.
f = CType(w, Label)
```

### <a name="composite-types"></a><span data-ttu-id="8b6c6-159">Složené typy</span><span class="sxs-lookup"><span data-stu-id="8b6c6-159">Composite Types</span></span>

<span data-ttu-id="8b6c6-160">Můžete použít `CType` k převodu hodnot na složené datové typy i na základní typy.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="8b6c6-161">Můžete jej také použít k převeďte třídu objektu na typ jednoho z jeho rozhraní, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>

```vb
' Assume class cZone implements interface iZone.
Dim h As Object
' The first argument to CType must be an expression, not a type.
Dim cZ As cZone
' The following statement coerces a cZone object to its interface iZone.
h = CType(cZ, iZone)
```

### <a name="array-types"></a><span data-ttu-id="8b6c6-162">Typy polí</span><span class="sxs-lookup"><span data-stu-id="8b6c6-162">Array Types</span></span>

<span data-ttu-id="8b6c6-163">`CType`lze také převést datové typy pole, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-163">`CType` can also convert array data types, as in the following example.</span></span>

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

<span data-ttu-id="8b6c6-164">Další informace a příklad najdete v tématu [převody polí](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="8b6c6-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>

### <a name="types-defining-ctype"></a><span data-ttu-id="8b6c6-165">Typy definující CType</span><span class="sxs-lookup"><span data-stu-id="8b6c6-165">Types Defining CType</span></span>

<span data-ttu-id="8b6c6-166">Můžete definovat `CType` pro třídu nebo strukturu, kterou jste definovali.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="8b6c6-167">To umožňuje převést hodnoty do a z typu vaší třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="8b6c6-168">Další informace a příklad naleznete v tématu [How to: Definujte operátor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)převodu.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>

> [!NOTE]
> <span data-ttu-id="8b6c6-169">Hodnoty používané s klíčovým slovem pro převod musí být platné pro cílový datový typ nebo dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="8b6c6-170">Například pokud se `Long` pokusíte převést `Integer`na `Long` , hodnota `Integer` musí být v rámci platného rozsahu pro datový typ.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>

> [!CAUTION]
> <span data-ttu-id="8b6c6-171">Určení `CType` pro převod z jednoho typu třídy na jiný se v době běhu nezdařila, pokud typ zdroje není odvozen z cílového typu.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="8b6c6-172">Taková chyba vyvolá <xref:System.InvalidCastException> výjimku.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>

<span data-ttu-id="8b6c6-173">Pokud je však jeden z typů struktura nebo třída, kterou jste definovali, a pokud jste definovali `CType` v této struktuře nebo třídě, převod může být úspěšný, pokud splňuje požadavky vašeho. `CType`</span><span class="sxs-lookup"><span data-stu-id="8b6c6-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="8b6c6-174">Viz [jak: Definujte operátor](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)převodu.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>

<span data-ttu-id="8b6c6-175">Provádění explicitního převodu je také označováno  jako přetypování výrazu na daný datový typ nebo třídu objektu.</span><span class="sxs-lookup"><span data-stu-id="8b6c6-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b6c6-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b6c6-176">See also</span></span>

- [<span data-ttu-id="8b6c6-177">Převody typu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b6c6-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="8b6c6-178">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="8b6c6-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="8b6c6-179">Postupy: Převést objekt na jiný typ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8b6c6-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="8b6c6-180">Struktury</span><span class="sxs-lookup"><span data-stu-id="8b6c6-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="8b6c6-181">Datové typy</span><span class="sxs-lookup"><span data-stu-id="8b6c6-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="8b6c6-182">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="8b6c6-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="8b6c6-183">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="8b6c6-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
