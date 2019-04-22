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
ms.openlocfilehash: 82ff710629089cd14c7e982b4afa4301d0790811
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833994"
---
# <a name="implicit-and-explicit-conversions-visual-basic"></a><span data-ttu-id="c2f47-102">Implicitní a explicitní převody (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c2f47-102">Implicit and Explicit Conversions (Visual Basic)</span></span>
<span data-ttu-id="c2f47-103">*Implicitní převod* nevyžaduje žádnou zvláštní syntaxi ve zdrojovém kódu.</span><span class="sxs-lookup"><span data-stu-id="c2f47-103">An *implicit conversion* does not require any special syntax in the source code.</span></span> <span data-ttu-id="c2f47-104">V následujícím příkladu, Visual Basic implicitně převede hodnotu `k` na jednoduchou přesnost s plovoucí desetinnou čárkou hodnotu před přiřazením na `q`.</span><span class="sxs-lookup"><span data-stu-id="c2f47-104">In the following example, Visual Basic implicitly converts the value of `k` to a single-precision floating-point value before assigning it to `q`.</span></span>  
  
```  
Dim k As Integer  
Dim q As Double  
' Integer widens to Double, so you can do this with Option Strict On.  
k = 432  
q = k  
```  
  
 <span data-ttu-id="c2f47-105">*Explicitní převod* používá klíčové slovo převodu typu.</span><span class="sxs-lookup"><span data-stu-id="c2f47-105">An *explicit conversion* uses a type conversion keyword.</span></span> <span data-ttu-id="c2f47-106">Visual Basic poskytuje několik takových klíčová slova, která vynucení výrazu v závorkách do požadovaného datového typu.</span><span class="sxs-lookup"><span data-stu-id="c2f47-106">Visual Basic provides several such keywords, which coerce an expression in parentheses to the desired data type.</span></span> <span data-ttu-id="c2f47-107">Tato klíčová slova fungují jako funkce, ale kompilátor generuje vložený kód, takže spuštění je mírně rychlejší než pomocí volání funkce.</span><span class="sxs-lookup"><span data-stu-id="c2f47-107">These keywords act like functions, but the compiler generates the code inline, so execution is slightly faster than with a function call.</span></span>  
  
 <span data-ttu-id="c2f47-108">Následující rozšíření v předchozím příkladu `CInt` – klíčové slovo převede hodnotu `q` zpět na celé číslo než ji přiřadíte `k`.</span><span class="sxs-lookup"><span data-stu-id="c2f47-108">In the following extension of the preceding example, the `CInt` keyword converts the value of `q` back to an integer before assigning it to `k`.</span></span>  
  
```  
' q had been assigned the value 432 from k.  
q = Math.Sqrt(q)  
k = CInt(q)  
' k now has the value 21 (rounded square root of 432).  
```  
  
## <a name="conversion-keywords"></a><span data-ttu-id="c2f47-109">Klíčová slova převodu</span><span class="sxs-lookup"><span data-stu-id="c2f47-109">Conversion Keywords</span></span>  
 <span data-ttu-id="c2f47-110">V následující tabulce jsou uvedeny klíčová slova převodu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c2f47-110">The following table shows the available conversion keywords.</span></span>  
  
|<span data-ttu-id="c2f47-111">Typ převodu – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="c2f47-111">Type conversion keyword</span></span>|<span data-ttu-id="c2f47-112">Převede výraz na datový typ</span><span class="sxs-lookup"><span data-stu-id="c2f47-112">Converts an expression to data type</span></span>|<span data-ttu-id="c2f47-113">Povolené datové typy výrazů má být převeden</span><span class="sxs-lookup"><span data-stu-id="c2f47-113">Allowable data types of expression to be converted</span></span>|  
|---|---|---|  
|`CBool`|[<span data-ttu-id="c2f47-114">Datový typ Boolean</span><span class="sxs-lookup"><span data-stu-id="c2f47-114">Boolean Data Type</span></span>](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)|<span data-ttu-id="c2f47-115">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-115">Any numeric type (including `Byte`, `SByte`, and enumerated types), `String`, `Object`</span></span>|  
|`CByte`|[<span data-ttu-id="c2f47-116">Datový typ Byte</span><span class="sxs-lookup"><span data-stu-id="c2f47-116">Byte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/byte-data-type.md)|<span data-ttu-id="c2f47-117">Jakýkoli číselný typ (včetně `SByte` a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-117">Any numeric type (including `SByte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CChar`|[<span data-ttu-id="c2f47-118">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="c2f47-118">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)|<span data-ttu-id="c2f47-119">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-119">`String`, `Object`</span></span>|  
|`CDate`|[<span data-ttu-id="c2f47-120">Datový typ Date</span><span class="sxs-lookup"><span data-stu-id="c2f47-120">Date Data Type</span></span>](../../../../visual-basic/language-reference/data-types/date-data-type.md)|<span data-ttu-id="c2f47-121">`String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-121">`String`, `Object`</span></span>|  
|`CDbl`|[<span data-ttu-id="c2f47-122">Datový typ Double</span><span class="sxs-lookup"><span data-stu-id="c2f47-122">Double Data Type</span></span>](../../../../visual-basic/language-reference/data-types/double-data-type.md)|<span data-ttu-id="c2f47-123">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-123">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CDec`|[<span data-ttu-id="c2f47-124">Datový typ Decimal</span><span class="sxs-lookup"><span data-stu-id="c2f47-124">Decimal Data Type</span></span>](../../../../visual-basic/language-reference/data-types/decimal-data-type.md)|<span data-ttu-id="c2f47-125">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-125">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CInt`|[<span data-ttu-id="c2f47-126">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="c2f47-126">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)|<span data-ttu-id="c2f47-127">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-127">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CLng`|[<span data-ttu-id="c2f47-128">Datový typ Long</span><span class="sxs-lookup"><span data-stu-id="c2f47-128">Long Data Type</span></span>](../../../../visual-basic/language-reference/data-types/long-data-type.md)|<span data-ttu-id="c2f47-129">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-129">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CObj`|[<span data-ttu-id="c2f47-130">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="c2f47-130">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)|<span data-ttu-id="c2f47-131">Jakýkoli typ</span><span class="sxs-lookup"><span data-stu-id="c2f47-131">Any type</span></span>|  
|`CSByte`|[<span data-ttu-id="c2f47-132">Datový typ SByte</span><span class="sxs-lookup"><span data-stu-id="c2f47-132">SByte Data Type</span></span>](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md)|<span data-ttu-id="c2f47-133">Jakýkoli číselný typ (včetně `Byte` a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-133">Any numeric type (including `Byte` and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CShort`|[<span data-ttu-id="c2f47-134">Datový typ Short</span><span class="sxs-lookup"><span data-stu-id="c2f47-134">Short Data Type</span></span>](../../../../visual-basic/language-reference/data-types/short-data-type.md)|<span data-ttu-id="c2f47-135">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-135">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CSng`|[<span data-ttu-id="c2f47-136">Datový typ Single</span><span class="sxs-lookup"><span data-stu-id="c2f47-136">Single Data Type</span></span>](../../../../visual-basic/language-reference/data-types/single-data-type.md)|<span data-ttu-id="c2f47-137">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-137">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CStr`|[<span data-ttu-id="c2f47-138">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="c2f47-138">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)|<span data-ttu-id="c2f47-139">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `Char`, `Char` pole, `Date`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-139">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `Char`, `Char` array, `Date`, `Object`</span></span>|  
|`CType`|<span data-ttu-id="c2f47-140">Zadaný typ za čárkou (`,`)</span><span class="sxs-lookup"><span data-stu-id="c2f47-140">Type specified following the comma (`,`)</span></span>|<span data-ttu-id="c2f47-141">Při převodu na *základní datový typ* (včetně pole Základní typu), stejné typy povolen pro odpovídající klíčového slova převodu</span><span class="sxs-lookup"><span data-stu-id="c2f47-141">When converting to an *elementary data type* (including an array of an elementary type), the same types as allowed for the corresponding conversion keyword</span></span><br /><br /> <span data-ttu-id="c2f47-142">Při převodu *složené datový typ*, implementuje rozhraní a třídy, ze které dědí</span><span class="sxs-lookup"><span data-stu-id="c2f47-142">When converting to a *composite data type*, the interfaces it implements and the classes from which it inherits</span></span><br /><br /> <span data-ttu-id="c2f47-143">Při převodu na třídy nebo struktury, ve kterém můžete mít přetížené `CType`, této třídě nebo struktuře</span><span class="sxs-lookup"><span data-stu-id="c2f47-143">When converting to a class or structure on which you have overloaded `CType`, that class or structure</span></span>|  
|`CUInt`|[<span data-ttu-id="c2f47-144">Datový typ UInteger</span><span class="sxs-lookup"><span data-stu-id="c2f47-144">UInteger Data Type</span></span>](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md)|<span data-ttu-id="c2f47-145">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-145">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CULng`|[<span data-ttu-id="c2f47-146">Datový typ ULong</span><span class="sxs-lookup"><span data-stu-id="c2f47-146">ULong Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ulong-data-type.md)|<span data-ttu-id="c2f47-147">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-147">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
|`CUShort`|[<span data-ttu-id="c2f47-148">Datový typ UShort</span><span class="sxs-lookup"><span data-stu-id="c2f47-148">UShort Data Type</span></span>](../../../../visual-basic/language-reference/data-types/ushort-data-type.md)|<span data-ttu-id="c2f47-149">Jakýkoli číselný typ (včetně `Byte`, `SByte`a vytvořit výčet typů), `Boolean`, `String`, `Object`</span><span class="sxs-lookup"><span data-stu-id="c2f47-149">Any numeric type (including `Byte`, `SByte`, and enumerated types), `Boolean`, `String`, `Object`</span></span>|  
  
## <a name="the-ctype-function"></a><span data-ttu-id="c2f47-150">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="c2f47-150">The CType Function</span></span>  
 <span data-ttu-id="c2f47-151">[Funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) pracuje na dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="c2f47-151">The [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md) operates on two arguments.</span></span> <span data-ttu-id="c2f47-152">První je výraz, který má být převeden, a druhý je data cílové třídy typu nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="c2f47-152">The first is the expression to be converted, and the second is the destination data type or object class.</span></span> <span data-ttu-id="c2f47-153">Všimněte si, že první argument musí být výraz, ne typ.</span><span class="sxs-lookup"><span data-stu-id="c2f47-153">Note that the first argument must be an expression, not a type.</span></span>  
  
 <span data-ttu-id="c2f47-154">`CType` je *vložená funkce*, což znamená zkompilovaný kód provede převod, často bez generování událostí funkce volání.</span><span class="sxs-lookup"><span data-stu-id="c2f47-154">`CType` is an *inline function*, meaning the compiled code makes the conversion, often without generating a function call.</span></span> <span data-ttu-id="c2f47-155">To zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="c2f47-155">This improves performance.</span></span>  
  
 <span data-ttu-id="c2f47-156">Porovnání `CType` s další typ převodu klíčová slova, přečtěte si téma [DirectCast operátor](../../../../visual-basic/language-reference/operators/directcast-operator.md) a [TryCast – operátor](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c2f47-156">For a comparison of `CType` with the other type conversion keywords, see [DirectCast Operator](../../../../visual-basic/language-reference/operators/directcast-operator.md) and [TryCast Operator](../../../../visual-basic/language-reference/operators/trycast-operator.md).</span></span>  
  
### <a name="elementary-types"></a><span data-ttu-id="c2f47-157">Základní typy</span><span class="sxs-lookup"><span data-stu-id="c2f47-157">Elementary Types</span></span>  
 <span data-ttu-id="c2f47-158">Následující příklad ukazuje použití `CType`.</span><span class="sxs-lookup"><span data-stu-id="c2f47-158">The following example demonstrates the use of `CType`.</span></span>  
  
```  
k = CType(q, Integer)  
' The following statement coerces w to the specific object class Label.  
f = CType(w, Label)  
```  
  
### <a name="composite-types"></a><span data-ttu-id="c2f47-159">Složené typy</span><span class="sxs-lookup"><span data-stu-id="c2f47-159">Composite Types</span></span>  
 <span data-ttu-id="c2f47-160">Můžete použít `CType` k převodu hodnoty na složené datové typy a také o základních typů.</span><span class="sxs-lookup"><span data-stu-id="c2f47-160">You can use `CType` to convert values to composite data types as well as to elementary types.</span></span> <span data-ttu-id="c2f47-161">Můžete také použít ho k vynucení třídu objektu na typ jednoho z jeho rozhraní, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c2f47-161">You can also use it to coerce an object class to the type of one of its interfaces, as in the following example.</span></span>  
  
```  
' Assume class cZone implements interface iZone.  
Dim h As Object  
' The first argument to CType must be an expression, not a type.  
Dim cZ As cZone  
' The following statement coerces a cZone object to its interface iZone.  
h = CType(cZ, iZone)  
```  
  
### <a name="array-types"></a><span data-ttu-id="c2f47-162">Typy polí</span><span class="sxs-lookup"><span data-stu-id="c2f47-162">Array Types</span></span>  
 <span data-ttu-id="c2f47-163">`CType` Můžete také převést pole datové typy, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c2f47-163">`CType` can also convert array data types, as in the following example.</span></span>  
  
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
  
 <span data-ttu-id="c2f47-164">Další informace a příklad najdete v tématu [převody pole](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="c2f47-164">For more information and an example, see [Array Conversions](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md).</span></span>  
  
### <a name="types-defining-ctype"></a><span data-ttu-id="c2f47-165">Typy definování CType</span><span class="sxs-lookup"><span data-stu-id="c2f47-165">Types Defining CType</span></span>  
 <span data-ttu-id="c2f47-166">Můžete definovat `CType` na třídy nebo struktury, které jste definovali.</span><span class="sxs-lookup"><span data-stu-id="c2f47-166">You can define `CType` on a class or structure you have defined.</span></span> <span data-ttu-id="c2f47-167">To umožňuje převod hodnoty do a z typu třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="c2f47-167">This allows you to convert values to and from the type of your class or structure.</span></span> <span data-ttu-id="c2f47-168">Další informace a příklad najdete v tématu [jak: Definice operátora převodu](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c2f47-168">For more information and an example, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2f47-169">Použít s klíčovým slovem převod hodnoty musí být platná pro cílový datový typ nebo dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="c2f47-169">Values used with a conversion keyword must be valid for the destination data type, or an error occurs.</span></span> <span data-ttu-id="c2f47-170">Například, pokud se pokusíte převést `Long` k `Integer`, hodnota `Long` musí být v platném rozsahu pro `Integer` datového typu.</span><span class="sxs-lookup"><span data-stu-id="c2f47-170">For example, if you attempt to convert a `Long` to an `Integer`, the value of the `Long` must be within the valid range for the `Integer` data type.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c2f47-171">Určení `CType` převést z jedné třídy typu na jiný selže v době běhu Pokud zdrojový typ není odvozen z cílového typu.</span><span class="sxs-lookup"><span data-stu-id="c2f47-171">Specifying `CType` to convert from one class type to another fails at run time if the source type does not derive from the destination type.</span></span> <span data-ttu-id="c2f47-172">Takové selhání vyvolá <xref:System.InvalidCastException> výjimky.</span><span class="sxs-lookup"><span data-stu-id="c2f47-172">Such a failure throws an <xref:System.InvalidCastException> exception.</span></span>  
  
 <span data-ttu-id="c2f47-173">Nicméně je-li jeden z typů struktury nebo třídy, které jste definovali, a pokud jste definovali `CType` v této struktury nebo třídy, může převod úspěšné, pokud splňuje požadavky vaší `CType`.</span><span class="sxs-lookup"><span data-stu-id="c2f47-173">However, if one of the types is a structure or class you have defined, and if you have defined `CType` on that structure or class, a conversion can succeed if it satisfies the requirements of your `CType`.</span></span> <span data-ttu-id="c2f47-174">Zobrazit [jak: Definice operátora převodu](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c2f47-174">See [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
 <span data-ttu-id="c2f47-175">Provedení explicitního převodu se taky říká *přetypování* výraz, který se daná data typu nebo objekt třídy.</span><span class="sxs-lookup"><span data-stu-id="c2f47-175">Performing an explicit conversion is also known as *casting* an expression to a given data type or object class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f47-176">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2f47-176">See also</span></span>

- [<span data-ttu-id="c2f47-177">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2f47-177">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="c2f47-178">Převody mezi řetězci a ostatními typy</span><span class="sxs-lookup"><span data-stu-id="c2f47-178">Conversions Between Strings and Other Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/conversions-between-strings-and-other-types.md)
- [<span data-ttu-id="c2f47-179">Postupy: Převést objekt na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2f47-179">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="c2f47-180">Struktury</span><span class="sxs-lookup"><span data-stu-id="c2f47-180">Structures</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="c2f47-181">Datové typy</span><span class="sxs-lookup"><span data-stu-id="c2f47-181">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="c2f47-182">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="c2f47-182">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="c2f47-183">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="c2f47-183">Troubleshooting Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
