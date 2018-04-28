---
title: Přetypování a převody (F#)
description: 'Zjistěte, jak programovací jazyk F # poskytuje operátory převodu pro aritmetické převody mezi různými primitivní typy.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 410c7da2b7ae8a09c58e8c89b24d0093a7f33a5c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="0276c-103">Přetypování a převody (F#)</span><span class="sxs-lookup"><span data-stu-id="0276c-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="0276c-104">Toto téma popisuje podporu pro převody typů v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="0276c-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="0276c-105">Aritmetické typy</span><span class="sxs-lookup"><span data-stu-id="0276c-105">Arithmetic Types</span></span>
<span data-ttu-id="0276c-106">F # poskytuje operátory převodu pro aritmetické převody mezi různými primitivní typy, jako třeba mezi celé číslo a plovoucí typy bodů.</span><span class="sxs-lookup"><span data-stu-id="0276c-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="0276c-107">Operátory převodu integrální a char mají zaškrtnuto a nezaškrtnuto forms; procedura bodu operátory a `enum` operátor převodu nepodporují.</span><span class="sxs-lookup"><span data-stu-id="0276c-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="0276c-108">Nezaškrtnuté formuláře jsou definovány v `Microsoft.FSharp.Core.Operators` a zaškrtnuté formuláře jsou definovány v `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="0276c-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="0276c-109">Checked formuláře zkontrolujte přetečení a generovat výjimku modulu runtime, pokud výsledná hodnota překročí omezení na typ cíle.</span><span class="sxs-lookup"><span data-stu-id="0276c-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="0276c-110">Každý z těchto operátorů má stejný název jako název cílového typu.</span><span class="sxs-lookup"><span data-stu-id="0276c-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="0276c-111">Například v následujícím kódu, ve kterém jsou typy explicitně poznámky, `byte` se zobrazí se dva různé významy.</span><span class="sxs-lookup"><span data-stu-id="0276c-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="0276c-112">První výskyt je typ a druhý je operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="0276c-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="0276c-113">V následující tabulce jsou definované v F # operátory převodu.</span><span class="sxs-lookup"><span data-stu-id="0276c-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="0276c-114">Operátor</span><span class="sxs-lookup"><span data-stu-id="0276c-114">Operator</span></span>|<span data-ttu-id="0276c-115">Popis</span><span class="sxs-lookup"><span data-stu-id="0276c-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="0276c-116">Převeďte na bajtů, 8bitové typu bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="0276c-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="0276c-117">Převeďte na podepsané bajtů.</span><span class="sxs-lookup"><span data-stu-id="0276c-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="0276c-118">Převeďte na 16bitové celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="0276c-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="0276c-119">Převeďte na celé číslo bez znaménka 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="0276c-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="0276c-120">Převeďte na 32bitové celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="0276c-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="0276c-121">Převeďte na celé číslo bez znaménka 32-bit.</span><span class="sxs-lookup"><span data-stu-id="0276c-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="0276c-122">Převeďte na 64bitové celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="0276c-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="0276c-123">Převeďte na celé číslo bez znaménka 64-bit.</span><span class="sxs-lookup"><span data-stu-id="0276c-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="0276c-124">Převeďte na nativní celé číslo.</span><span class="sxs-lookup"><span data-stu-id="0276c-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="0276c-125">Převeďte na celé číslo bez znaménka nativní.</span><span class="sxs-lookup"><span data-stu-id="0276c-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="0276c-126">Převeďte 64-bit Dvojitá přesnost IEEE bodu číslo s plovoucí čárkou.</span><span class="sxs-lookup"><span data-stu-id="0276c-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="0276c-127">Převeďte 32-bit jednoduchou přesností IEEE bodu číslo s plovoucí čárkou.</span><span class="sxs-lookup"><span data-stu-id="0276c-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="0276c-128">Převést na `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="0276c-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="0276c-129">Převést na `System.Char`, znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="0276c-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="0276c-130">Převeďte na výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="0276c-130">Convert to an enumerated type.</span></span>|
<span data-ttu-id="0276c-131">Kromě předdefinovaných primitivní typy, můžete použít tyto operátory s typy, které implementují `op_Explicit` nebo `op_Implicit` metody s odpovídajícími podpisy.</span><span class="sxs-lookup"><span data-stu-id="0276c-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="0276c-132">Například `int` operátor převodu pracuje s žádný typ, který poskytuje statickou metodu `op_Explicit` který přebere typ jako parametr a vrátí `int`.</span><span class="sxs-lookup"><span data-stu-id="0276c-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="0276c-133">Speciální výjimkou obecně platí, že metody nemohou být přetíženy o návratový typ, můžete k tomu `op_Explicit` a `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="0276c-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="0276c-134">Výčtové typy</span><span class="sxs-lookup"><span data-stu-id="0276c-134">Enumerated Types</span></span>
<span data-ttu-id="0276c-135">`enum` Operátor je obecný operátor, který přijímá jeden parametr typu, který představuje typ `enum` převést.</span><span class="sxs-lookup"><span data-stu-id="0276c-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="0276c-136">Když se převede na Výčtový typ, zadejte odvození pokusí zjistit typ `enum` , kterou chcete převést.</span><span class="sxs-lookup"><span data-stu-id="0276c-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="0276c-137">V následujícím příkladu, proměnná `col1` není explicitně označena, ale jeho typ je odvozen z novější test rovnosti.</span><span class="sxs-lookup"><span data-stu-id="0276c-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="0276c-138">Proto můžete kompilátor odvodit převádíte na `Color` výčtu.</span><span class="sxs-lookup"><span data-stu-id="0276c-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="0276c-139">Alternativně můžete poskytnout anotaci typu stejně jako u `col2` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0276c-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]
    
<span data-ttu-id="0276c-140">Můžete také určit typ výčtu cíl explicitně jako parametr typu, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="0276c-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="0276c-141">Všimněte si, že výčtu vrhá pracovní pouze v případě, že je kompatibilní s typem převáděné s podkladovým typem výčtu.</span><span class="sxs-lookup"><span data-stu-id="0276c-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="0276c-142">V následujícím kódu, převod se nepovede zkompilovat z důvodu neshody mezi `int32` a `uint32`.</span><span class="sxs-lookup"><span data-stu-id="0276c-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="0276c-143">Další informace najdete v tématu [výčty](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="0276c-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="0276c-144">Přetypování typy objektů</span><span class="sxs-lookup"><span data-stu-id="0276c-144">Casting Object Types</span></span>
<span data-ttu-id="0276c-145">Převod mezi typy v hierarchii objektu je nezbytné, aby objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="0276c-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="0276c-146">Existují dva základní typy převody: přetypování nahoru (přetypování nahoru) a přetypování dolů (přetypování dolů).</span><span class="sxs-lookup"><span data-stu-id="0276c-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="0276c-147">Přetypování nahoru hierarchie znamená přetypování z odvozené objekt odkazů na základní objekt odkaz.</span><span class="sxs-lookup"><span data-stu-id="0276c-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="0276c-148">Takové přetypování záruku, že fungovat, dokud základní třída je v hierarchii dědičnosti odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="0276c-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="0276c-149">Přetypování dolů hierarchii, postupně od základní objekt odkaz na objekt odvozené odkaz, bude úspěšné pouze v případě, že objekt je ve skutečnosti instance typu správnou cílovou (Odvozený) nebo typu odvozeného od cílového typu.</span><span class="sxs-lookup"><span data-stu-id="0276c-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="0276c-150">F # poskytuje operátory pro tyto typy převody.</span><span class="sxs-lookup"><span data-stu-id="0276c-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="0276c-151">`:>` Operátor vrhá nahoru v hierarchii a `:?>` operátor vrhá hierarchií směrem dolů.</span><span class="sxs-lookup"><span data-stu-id="0276c-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="0276c-152">Přetypování nahoru</span><span class="sxs-lookup"><span data-stu-id="0276c-152">Upcasting</span></span>
<span data-ttu-id="0276c-153">V mnoha jazycích objektově orientované je implicitní; přetypování nahoru v F # pravidla se mírně liší.</span><span class="sxs-lookup"><span data-stu-id="0276c-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="0276c-154">Předání argumentů metody na typ objektu, který je automaticky použito přetypování nahoru.</span><span class="sxs-lookup"><span data-stu-id="0276c-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="0276c-155">Ale pro umožňují vazby funkce v modulu, přetypování nahoru není automatické, pokud typ parametru je deklarován jako typ flexibilní.</span><span class="sxs-lookup"><span data-stu-id="0276c-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="0276c-156">Další informace najdete v tématu [flexibilní typy](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="0276c-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="0276c-157">`:>` Operátor provádí statického přetypování, což znamená, že v době kompilace je určen úspěch přetypování.</span><span class="sxs-lookup"><span data-stu-id="0276c-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="0276c-158">Pokud přetypování, který používá `:>` zkompiluje úspěšně, je platný přetypování a nemá žádné riziko selhání za běhu.</span><span class="sxs-lookup"><span data-stu-id="0276c-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="0276c-159">Můžete také `upcast` operátor proveďte takový převod.</span><span class="sxs-lookup"><span data-stu-id="0276c-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="0276c-160">Následující výraz určuje převod nahoru v hierarchii:</span><span class="sxs-lookup"><span data-stu-id="0276c-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="0276c-161">Pokud použijete operátor přetypování nahoru, pokusí se kompilátor odvození typu, který převádíte na z kontextu.</span><span class="sxs-lookup"><span data-stu-id="0276c-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="0276c-162">Pokud kompilátor se nepodařilo určit typ cíle, kompilátor ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="0276c-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="0276c-163">Přetypování dolů</span><span class="sxs-lookup"><span data-stu-id="0276c-163">Downcasting</span></span>
<span data-ttu-id="0276c-164">`:?>` Operátor provádí dynamický přetypování, což znamená, že v době běhu je určen úspěch přetypování.</span><span class="sxs-lookup"><span data-stu-id="0276c-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="0276c-165">Přetypování, který používá `:?>` operátor kontrolována v době kompilace; ale v době běhu je proveden pokus o převést na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="0276c-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="0276c-166">Pokud je objekt kompatibilní s typem cíl, bude úspěšná přetypování.</span><span class="sxs-lookup"><span data-stu-id="0276c-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="0276c-167">Pokud objekt není kompatibilní s typem cíl, modul runtime vyvolává `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="0276c-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="0276c-168">Můžete také `downcast` operátor provést převod dynamického typu.</span><span class="sxs-lookup"><span data-stu-id="0276c-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="0276c-169">Následující výraz určuje převod hierarchií směrem dolů na typ, který je odvozeno z kontextu program:</span><span class="sxs-lookup"><span data-stu-id="0276c-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="0276c-170">Jako u `upcast` operátor, pokud kompilátor nelze odvodit typ specifické cíle z kontextu, ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="0276c-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="0276c-171">Následující kód ukazuje použití `:>` a `:?>` operátory.</span><span class="sxs-lookup"><span data-stu-id="0276c-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="0276c-172">Kód ukazuje, že `:?>` operátor je nejvhodnější při vědět, převod bude úspěšné, protože je vyvolává `InvalidCastException` Pokud převod selže.</span><span class="sxs-lookup"><span data-stu-id="0276c-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="0276c-173">Pokud si nejste jisti, že bude převodu z úspěšné, typ testu, který používá `match` výrazu je lepší, protože při ní nedochází režii generování výjimku.</span><span class="sxs-lookup"><span data-stu-id="0276c-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="0276c-174">Protože obecné operátory `downcast` a `upcast` spoléhají na odvození typu určit typ argumentu a vraťte se ve výše uvedeném kódu, můžete nahradit</span><span class="sxs-lookup"><span data-stu-id="0276c-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="0276c-175">with</span><span class="sxs-lookup"><span data-stu-id="0276c-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="0276c-176">V předchozí kód typ argumentu a návratové typy jsou `Derived1` a `Base1`, v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="0276c-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="0276c-177">Další informace o testech typu najdete v tématu [výrazy shody](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="0276c-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0276c-178">Viz také</span><span class="sxs-lookup"><span data-stu-id="0276c-178">See Also</span></span>
[<span data-ttu-id="0276c-179">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="0276c-179">F# Language Reference</span></span>](index.md)
