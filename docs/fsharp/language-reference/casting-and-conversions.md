---
title: Přetypování a převody (F#)
description: 'Zjistěte, jak programovací jazyk F # poskytuje operátory převodu pro aritmetické převody mezi různými primitivní typy.'
ms.date: 05/16/2016
ms.openlocfilehash: aca1a2523130ee485a7e7c9a6a45a410904cb246
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677926"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="14fac-103">Přetypování a převody (F#)</span><span class="sxs-lookup"><span data-stu-id="14fac-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="14fac-104">Toto téma popisuje podporu pro převody typů v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="14fac-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="14fac-105">Aritmetické typy</span><span class="sxs-lookup"><span data-stu-id="14fac-105">Arithmetic Types</span></span>

<span data-ttu-id="14fac-106">Jazyk F # poskytuje operátory převodu pro aritmetické převody mezi různými primitivní typy, jako například mezi celými čísly a typy plovoucího bodu.</span><span class="sxs-lookup"><span data-stu-id="14fac-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="14fac-107">Operátory převodu celé číslo a char kontrole a zaškrtnuté políčko formuláře; operátory s plovoucí desetinnou čárkou a `enum` operátor převodu tomu tak není.</span><span class="sxs-lookup"><span data-stu-id="14fac-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="14fac-108">Unchecked formuláře jsou definovány v `Microsoft.FSharp.Core.Operators` a kontrolovaný formuláře jsou definovány v `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="14fac-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="14fac-109">Checked formuláře kontrola přetečení a generovat výjimku při běhu, pokud výsledná hodnota překračuje omezení cílového typu.</span><span class="sxs-lookup"><span data-stu-id="14fac-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="14fac-110">Každý z těchto operátorů má stejný název jako název cílového typu.</span><span class="sxs-lookup"><span data-stu-id="14fac-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="14fac-111">Například v následujícím kódu, ve kterém jsou typy explicitně označena, `byte` zobrazí se dvě různé významy.</span><span class="sxs-lookup"><span data-stu-id="14fac-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="14fac-112">První výskyt je pro typ a druhý je operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="14fac-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="14fac-113">V následující tabulce jsou uvedeny operátory převodu, které jsou definovány v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="14fac-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="14fac-114">Operátor</span><span class="sxs-lookup"><span data-stu-id="14fac-114">Operator</span></span>|<span data-ttu-id="14fac-115">Popis</span><span class="sxs-lookup"><span data-stu-id="14fac-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="14fac-116">Převeďte na byte, typ bez znaménka 8 bitů.</span><span class="sxs-lookup"><span data-stu-id="14fac-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="14fac-117">Převod na bajty se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="14fac-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="14fac-118">Převeďte na celé číslo se znaménkem 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="14fac-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="14fac-119">Převeďte na celé číslo bez znaménka 16 bitů.</span><span class="sxs-lookup"><span data-stu-id="14fac-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="14fac-120">Převeďte na 32bitové celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="14fac-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="14fac-121">Převeďte na 32-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="14fac-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="14fac-122">Převeďte na 64bitové celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="14fac-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="14fac-123">Převeďte na 64-bit znaménka.</span><span class="sxs-lookup"><span data-stu-id="14fac-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="14fac-124">Převeďte na nativní celé číslo.</span><span class="sxs-lookup"><span data-stu-id="14fac-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="14fac-125">Převeďte na celé číslo bez znaménka nativní.</span><span class="sxs-lookup"><span data-stu-id="14fac-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="14fac-126">Převeďte na IEEE dvojité přesnosti 64bitovým kompilátorem plovoucí desetinné číslo s desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="14fac-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="14fac-127">Převeďte IEEE jednoduchou přesností 32-bit plovoucí desetinné číslo s desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="14fac-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="14fac-128">Převést na `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="14fac-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="14fac-129">Převést na `System.Char`, znaku Unicode.</span><span class="sxs-lookup"><span data-stu-id="14fac-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="14fac-130">Převeďte na typ výčtu.</span><span class="sxs-lookup"><span data-stu-id="14fac-130">Convert to an enumerated type.</span></span>|
<span data-ttu-id="14fac-131">Kromě předdefinované primitivní typy, můžete použít tyto operátory s typy, které implementují `op_Explicit` nebo `op_Implicit` metody s odpovídajícími podpisy.</span><span class="sxs-lookup"><span data-stu-id="14fac-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="14fac-132">Například `int` operátor převodu funguje s jakýmkoli typem, který poskytuje statické metody `op_Explicit` , která přebírá typ jako parametr a vrací `int`.</span><span class="sxs-lookup"><span data-stu-id="14fac-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="14fac-133">Jako speciální výjimky k obecným pravidlem, že metody nemohou být přetíženy návratovým typem, můžete udělat `op_Explicit` a `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="14fac-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="14fac-134">Výčtové typy</span><span class="sxs-lookup"><span data-stu-id="14fac-134">Enumerated Types</span></span>

<span data-ttu-id="14fac-135">`enum` Operátor je obecný operátor, který přijímá jeden parametr typu, který představuje typ `enum` k převodu.</span><span class="sxs-lookup"><span data-stu-id="14fac-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="14fac-136">Když ji převede na Výčtový typ, typ odvození se pokusí určit typ `enum` , který chcete převést.</span><span class="sxs-lookup"><span data-stu-id="14fac-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="14fac-137">V následujícím příkladu je proměnná `col1` není explicitně označena, ale jeho typ je odvozen z novější test rovnosti.</span><span class="sxs-lookup"><span data-stu-id="14fac-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="14fac-138">Kompilátor může odvodit proto, že převádíte na `Color` výčtu.</span><span class="sxs-lookup"><span data-stu-id="14fac-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="14fac-139">Alternativně můžete zadat poznámku typu, stejně jako u `col2` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="14fac-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="14fac-140">Cílový typ výčtu můžete také explicitně zadat jako parametr typu, stejně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="14fac-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="14fac-141">Všimněte si, že výčet přetypování pracovní pouze v případě, že základní typ výčtu je kompatibilní s typem převodu.</span><span class="sxs-lookup"><span data-stu-id="14fac-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="14fac-142">V následujícím kódu, že je převod neúspěšný kompilace z důvodu neshody mezi `int32` a `uint32`.</span><span class="sxs-lookup"><span data-stu-id="14fac-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="14fac-143">Další informace najdete v tématu [výčty](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="14fac-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="14fac-144">Přetypování typy objektů</span><span class="sxs-lookup"><span data-stu-id="14fac-144">Casting Object Types</span></span>

<span data-ttu-id="14fac-145">Převod mezi typy v hierarchii objektů je zásadní pro objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="14fac-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="14fac-146">Existují dva základní typy převodů: přetypování nahoru (upcasting) a přetypování dolů (přetypování na nižší).</span><span class="sxs-lookup"><span data-stu-id="14fac-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="14fac-147">Přetypování hierarchii znamená, že přetypování z odvozeného objektu odkaz na odkaz na základní objekt.</span><span class="sxs-lookup"><span data-stu-id="14fac-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="14fac-148">Takový výraz přetypování zaručeně funguje jako základní třída je v hierarchii dědičnosti odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="14fac-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="14fac-149">Přetypování dolů hierarchii z základní objekt odkazu na odkaz na objekt odvozené, bude úspěšné pouze v případě, že objekt je ve skutečnosti instance správné cíl (Odvozený) typ nebo typ odvozený z cílového typu.</span><span class="sxs-lookup"><span data-stu-id="14fac-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="14fac-150">Jazyk F # poskytuje operátory pro tyto typy převodů.</span><span class="sxs-lookup"><span data-stu-id="14fac-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="14fac-151">`:>` Operátor přetypování nahoru hierarchii a `:?>` operátor přetypování dolů v hierarchii.</span><span class="sxs-lookup"><span data-stu-id="14fac-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="14fac-152">Upcasting</span><span class="sxs-lookup"><span data-stu-id="14fac-152">Upcasting</span></span>

<span data-ttu-id="14fac-153">V řadě jazyků orientovaných upcasting je implicitní; v jazyce F # pravidla se mírně liší.</span><span class="sxs-lookup"><span data-stu-id="14fac-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="14fac-154">Upcasting se automaticky použije při předání argumentů metody na typu objektu.</span><span class="sxs-lookup"><span data-stu-id="14fac-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="14fac-155">Však pro funkce vazbou let v modulu upcasting není automaticky, pokud typ parametru není deklarována jako typ flexibilní.</span><span class="sxs-lookup"><span data-stu-id="14fac-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="14fac-156">Další informace najdete v tématu [flexibilní typy](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="14fac-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="14fac-157">`:>` Operátor provádí statickou přetypování, což znamená, že úspěch přetypování je určen v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="14fac-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="14fac-158">Pokud přetypování, která používá `:>` se zkompiluje úspěšně, je platný přetypování a nemá žádné riziko selhání za běhu.</span><span class="sxs-lookup"><span data-stu-id="14fac-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="14fac-159">Můžete také použít `upcast` operátor k provádění těchto převodů.</span><span class="sxs-lookup"><span data-stu-id="14fac-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="14fac-160">Následující výraz určuje převod hierarchie:</span><span class="sxs-lookup"><span data-stu-id="14fac-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="14fac-161">Pokud použijete operátor přetypování nahoru, kompilátor se pokusí odvodit typ, který převádíte z kontextu.</span><span class="sxs-lookup"><span data-stu-id="14fac-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="14fac-162">Pokud kompilátor nemůže určit cílový typ, kompilátor nahlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="14fac-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="14fac-163">Přetypování na nižší</span><span class="sxs-lookup"><span data-stu-id="14fac-163">Downcasting</span></span>

<span data-ttu-id="14fac-164">`:?>` Operátor provádí dynamické přetypování, což znamená, že úspěch přetypování je stanovena v době běhu.</span><span class="sxs-lookup"><span data-stu-id="14fac-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="14fac-165">Přetypování, která používá `:?>` operátor není zaregistrované v době kompilace, ale za běhu, je proveden pokus o přetypování na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="14fac-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="14fac-166">Pokud je objekt kompatibilní s cílovým typem, proběhne úspěšně přetypování.</span><span class="sxs-lookup"><span data-stu-id="14fac-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="14fac-167">Pokud objekt není kompatibilní s cílovým typem, modul runtime vyvolává `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="14fac-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="14fac-168">Můžete také použít `downcast` operátor pro převod dynamického typu.</span><span class="sxs-lookup"><span data-stu-id="14fac-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="14fac-169">Následující výraz určuje převod hierarchií směrem dolů na typ, který je odvozen z kontextu programu:</span><span class="sxs-lookup"><span data-stu-id="14fac-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="14fac-170">Jako u `upcast` operátora, pokud kompilátor nemůže odvodit typ konkrétní cíl z kontextu, oznámí chybu.</span><span class="sxs-lookup"><span data-stu-id="14fac-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="14fac-171">Následující kód ukazuje použití `:>` a `:?>` operátory.</span><span class="sxs-lookup"><span data-stu-id="14fac-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="14fac-172">Kód ukazuje, že `:?>` operátor je nejlepší použít při vědět, že převod bude úspěšné, protože ji vyvolá `InvalidCastException` Pokud převod selže.</span><span class="sxs-lookup"><span data-stu-id="14fac-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="14fac-173">Pokud si nejste jisti, že se převod úspěšný, typ testu, který používá `match` výrazu je lepší, protože se eliminuje režijní náklady na generování výjimku.</span><span class="sxs-lookup"><span data-stu-id="14fac-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="14fac-174">Protože obecný operátory `downcast` a `upcast` využívají odvození typu k určení typu argument a vrácená ve výše uvedeném kódu, můžete nahradit</span><span class="sxs-lookup"><span data-stu-id="14fac-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="14fac-175">with</span><span class="sxs-lookup"><span data-stu-id="14fac-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="14fac-176">V předchozím kódu, typ argumentu a návratové typy jsou `Derived1` a `Base1`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="14fac-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="14fac-177">Další informace o typu testů, naleznete v tématu [odpovídající výrazy](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="14fac-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="14fac-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14fac-178">See also</span></span>

- [<span data-ttu-id="14fac-179">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="14fac-179">F# Language Reference</span></span>](index.md)
