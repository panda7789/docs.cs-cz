---
title: Přetypování a převody
description: Přečtěte si F# , jak programovací jazyk poskytuje operátory převodu pro aritmetické převody mezi různými primitivními typy.
ms.date: 05/16/2016
ms.openlocfilehash: ee4df588caabf58c7b9e18961e217ef8f15fcf93
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630431"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="d802e-103">Přetypování a převody (F#)</span><span class="sxs-lookup"><span data-stu-id="d802e-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="d802e-104">Toto téma popisuje podporu pro převody typu v F#nástroji.</span><span class="sxs-lookup"><span data-stu-id="d802e-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="d802e-105">Aritmetické typy</span><span class="sxs-lookup"><span data-stu-id="d802e-105">Arithmetic Types</span></span>

<span data-ttu-id="d802e-106">F#poskytuje operátory převodu pro aritmetické převody mezi různými primitivními typy, jako je například typ Integer a plovoucí desetinná čárka.</span><span class="sxs-lookup"><span data-stu-id="d802e-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="d802e-107">Operátory převodu integrálu a znaků mají kontrolované a nezaškrtnuté formuláře. operátory s plovoucí desetinnou čárkou a `enum` operátor převodu nejsou.</span><span class="sxs-lookup"><span data-stu-id="d802e-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="d802e-108">Nekontrolované formuláře jsou definovány v `Microsoft.FSharp.Core.Operators` a jsou definovány formuláře v. `Microsoft.FSharp.Core.Operators.Checked`</span><span class="sxs-lookup"><span data-stu-id="d802e-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="d802e-109">Kontroluje kontrolované formuláře pro přetečení a generuje výjimku za běhu, pokud výsledná hodnota překračuje limity cílového typu.</span><span class="sxs-lookup"><span data-stu-id="d802e-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="d802e-110">Každý z těchto operátorů má stejný název jako název cílového typu.</span><span class="sxs-lookup"><span data-stu-id="d802e-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="d802e-111">Například v následujícím kódu, ve kterém jsou typy explicitně opatřeny poznámkami, `byte` se zobrazí se dvěma různými významy.</span><span class="sxs-lookup"><span data-stu-id="d802e-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="d802e-112">První výskyt je typ a druhý je operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="d802e-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="d802e-113">V následující tabulce jsou uvedeny operátory převodu definované F#v.</span><span class="sxs-lookup"><span data-stu-id="d802e-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="d802e-114">Operátor</span><span class="sxs-lookup"><span data-stu-id="d802e-114">Operator</span></span>|<span data-ttu-id="d802e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="d802e-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="d802e-116">Převod na bajt, 8bitový typ bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="d802e-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="d802e-117">Převod na bajt se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="d802e-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="d802e-118">Převede na 16bitové celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="d802e-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="d802e-119">Převod na 16 bitů unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="d802e-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="d802e-120">Převede na celé číslo se znaménkem 32.</span><span class="sxs-lookup"><span data-stu-id="d802e-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="d802e-121">Převod na 32-bitovou unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="d802e-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="d802e-122">Převede na celé číslo se znaménkem 64.</span><span class="sxs-lookup"><span data-stu-id="d802e-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="d802e-123">Převod na 64-bitovou unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="d802e-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="d802e-124">Převést na nativní celé číslo.</span><span class="sxs-lookup"><span data-stu-id="d802e-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="d802e-125">Převod na nativní celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="d802e-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="d802e-126">Převeďte na 64 čísla s plovoucí desetinnou čárkou s dvojitou přesností IEEE.</span><span class="sxs-lookup"><span data-stu-id="d802e-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="d802e-127">Převod na 32 číslo s plovoucí desetinnou čárkou s jednoduchou přesností.</span><span class="sxs-lookup"><span data-stu-id="d802e-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="d802e-128">Převést na `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d802e-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="d802e-129">Převod na `System.Char`, znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="d802e-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="d802e-130">Převod na Výčtový typ.</span><span class="sxs-lookup"><span data-stu-id="d802e-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="d802e-131">Kromě integrovaných primitivních typů můžete použít tyto operátory s typy, které implementují `op_Explicit` nebo `op_Implicit` metody s příslušnými signaturami.</span><span class="sxs-lookup"><span data-stu-id="d802e-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="d802e-132">Například `int` operátor převodu funguje s jakýmkoli typem, který poskytuje statickou metodu `op_Explicit` , která přebírá typ jako parametr a vrací `int`.</span><span class="sxs-lookup"><span data-stu-id="d802e-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="d802e-133">Jako speciální výjimka pro obecné pravidlo, že metody nemohou být přetíženy pomocí návratového typu, můžete to provést pro `op_Explicit` a. `op_Implicit`</span><span class="sxs-lookup"><span data-stu-id="d802e-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="d802e-134">Výčtové typy</span><span class="sxs-lookup"><span data-stu-id="d802e-134">Enumerated Types</span></span>

<span data-ttu-id="d802e-135">Operátor je obecný operátor, který přebírá jeden parametr typu, který představuje typ `enum` pro převod na. `enum`</span><span class="sxs-lookup"><span data-stu-id="d802e-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="d802e-136">Když se převede na Výčtový typ, pokusy o odvození typu určují typ `enum` , na který chcete převést.</span><span class="sxs-lookup"><span data-stu-id="d802e-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="d802e-137">V následujícím příkladu není proměnná `col1` explicitně Poznáma, ale její typ je odvozen z pozdějšího testu rovnosti.</span><span class="sxs-lookup"><span data-stu-id="d802e-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="d802e-138">Proto kompilátor může odvodit, že převádíte na `Color` výčet.</span><span class="sxs-lookup"><span data-stu-id="d802e-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="d802e-139">Alternativně můžete zadat anotaci typu, jak je uvedeno `col2` v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d802e-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="d802e-140">Cílový typ výčtu můžete zadat také explicitně jako parametr typu, jak je uvedeno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="d802e-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="d802e-141">Všimněte si, že přetypování výčtu funguje pouze v případě, že podkladový typ výčtu je kompatibilní s převáděným typem.</span><span class="sxs-lookup"><span data-stu-id="d802e-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="d802e-142">V následujícím kódu se převod nezdařil, protože se neshoduje mezi `int32` a. `uint32`</span><span class="sxs-lookup"><span data-stu-id="d802e-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="d802e-143">Další informace naleznete v tématu [výčty](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="d802e-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="d802e-144">Přetypování typů objektů</span><span class="sxs-lookup"><span data-stu-id="d802e-144">Casting Object Types</span></span>

<span data-ttu-id="d802e-145">Převod mezi typy v hierarchii objektů je zásadní pro objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="d802e-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="d802e-146">Existují dva základní typy převodů: přetypování (přetypování) a přetypování (potřeby).</span><span class="sxs-lookup"><span data-stu-id="d802e-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="d802e-147">Při přetypování hierarchie znamená přetypování z odvozeného objektu na odkaz na základní objekt.</span><span class="sxs-lookup"><span data-stu-id="d802e-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="d802e-148">Takovému přetypování je zaručeno, že bude fungovat, pokud je základní třída v hierarchii dědičnosti odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="d802e-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="d802e-149">Přetypování dolů v hierarchii ze základního objektu na odkaz na odvozený objekt je úspěšný pouze v případě, že objekt je ve skutečnosti instancí správného cílového (odvozeného) typu nebo typu odvozeného z cílového typu.</span><span class="sxs-lookup"><span data-stu-id="d802e-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="d802e-150">F#poskytuje operátory pro tyto typy převodů.</span><span class="sxs-lookup"><span data-stu-id="d802e-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="d802e-151">Operátor přetypování hierarchii nahoru `:?>` a operátor přetypování dolů v hierarchii. `:>`</span><span class="sxs-lookup"><span data-stu-id="d802e-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="d802e-152">Přetypování</span><span class="sxs-lookup"><span data-stu-id="d802e-152">Upcasting</span></span>

<span data-ttu-id="d802e-153">V mnoha objektově orientovaných jazycích je přetypování implicitní. v F#nástroji se pravidla mírně liší.</span><span class="sxs-lookup"><span data-stu-id="d802e-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="d802e-154">Při předávání argumentů metodám typu objektu je přetypování použito automaticky.</span><span class="sxs-lookup"><span data-stu-id="d802e-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="d802e-155">Pro funkce vázané na let v modulu však není automatické přetypování automatické, pokud typ parametru není deklarován jako flexibilní typ.</span><span class="sxs-lookup"><span data-stu-id="d802e-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="d802e-156">Další informace naleznete v tématu [flexibilní typy](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="d802e-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="d802e-157">`:>` Operátor provádí statické přetypování, což znamená, že úspěch přetypování je určen v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="d802e-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="d802e-158">Pokud je přetypování, `:>` které používá kompilování, úspěšné, jedná se o platné přetypování a v době běhu se nejedná o možnost selhání.</span><span class="sxs-lookup"><span data-stu-id="d802e-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="d802e-159">K provedení takového převodu můžete `upcast` použít také operátor.</span><span class="sxs-lookup"><span data-stu-id="d802e-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="d802e-160">Následující výraz určuje převod hierarchie:</span><span class="sxs-lookup"><span data-stu-id="d802e-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="d802e-161">Při použití operátoru přetypování se kompilátor pokusí odvodit typ, na který převádíte z kontextu.</span><span class="sxs-lookup"><span data-stu-id="d802e-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="d802e-162">Pokud kompilátor nemůže určit cílový typ, kompilátor ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="d802e-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span>

### <a name="downcasting"></a><span data-ttu-id="d802e-163">Potřeby</span><span class="sxs-lookup"><span data-stu-id="d802e-163">Downcasting</span></span>

<span data-ttu-id="d802e-164">`:?>` Operátor provádí dynamické přetypování, což znamená, že úspěch přetypování je určen v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d802e-164">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="d802e-165">Přetypování, které používá `:?>` operátor, není kontrolováno v době kompilace; v době běhu je však proveden pokus o přetypování na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="d802e-165">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="d802e-166">Pokud je objekt kompatibilní s cílovým typem, přetypování je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="d802e-166">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="d802e-167">Pokud objekt není kompatibilní s cílovým typem, modul runtime vyvolá `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="d802e-167">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="d802e-168">Pomocí `downcast` operátoru můžete také provést převod dynamického typu.</span><span class="sxs-lookup"><span data-stu-id="d802e-168">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="d802e-169">Následující výraz určuje převod mimo hierarchii na typ, který je odvozen z kontextu programu:</span><span class="sxs-lookup"><span data-stu-id="d802e-169">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="d802e-170">`upcast` Jako operátor, pokud kompilátor nemůže odvodit konkrétní cílový typ z kontextu, hlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="d802e-170">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span>

<span data-ttu-id="d802e-171">Následující kód ilustruje použití `:>` operátorů a. `:?>`</span><span class="sxs-lookup"><span data-stu-id="d802e-171">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="d802e-172">Kód ukazuje, že `:?>` je operátor nejlépe použit, pokud víte, že převod proběhne úspěšně, protože vyvolá `InvalidCastException` v případě, že převod selže.</span><span class="sxs-lookup"><span data-stu-id="d802e-172">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="d802e-173">Pokud si nejste jisti, že převod proběhne úspěšně, test typu, který používá `match` výraz, je lepší, protože se vyhne režii generování výjimky.</span><span class="sxs-lookup"><span data-stu-id="d802e-173">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="d802e-174">Vzhledem k tomu `downcast` , `upcast` že obecné operátory a spoléhají na odvození typu k určení argumentu a návratového typu, ve výše uvedeném kódu, můžete nahradit</span><span class="sxs-lookup"><span data-stu-id="d802e-174">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="d802e-175">with</span><span class="sxs-lookup"><span data-stu-id="d802e-175">with</span></span>

```fsharp
let base1 = upcast d1
```

<span data-ttu-id="d802e-176">V předchozím kódu jsou `Derived1` typ argumentu a návratové typy a `Base1`v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d802e-176">In the previous code, the argument type and return types are `Derived1` and `Base1`, respectively.</span></span>

<span data-ttu-id="d802e-177">Další informace o typech testů naleznete v tématu [Match Expressions](match-Expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d802e-177">For more information about type tests, see [Match Expressions](match-Expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d802e-178">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d802e-178">See also</span></span>

- [<span data-ttu-id="d802e-179">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="d802e-179">F# Language Reference</span></span>](index.md)
