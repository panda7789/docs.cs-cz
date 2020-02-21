---
title: Přetypování a převody
description: Přečtěte si F# , jak programovací jazyk poskytuje operátory převodu pro aritmetické převody mezi různými primitivními typy.
ms.date: 02/20/2020
ms.openlocfilehash: 5f9727d14a7ae070e0f0f71fa0a0abe04f662071
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543583"
---
# <a name="casting-and-conversions-f"></a><span data-ttu-id="93367-103">Přetypování a převody (F#)</span><span class="sxs-lookup"><span data-stu-id="93367-103">Casting and Conversions (F#)</span></span>

<span data-ttu-id="93367-104">Toto téma popisuje podporu pro převody typu v F#nástroji.</span><span class="sxs-lookup"><span data-stu-id="93367-104">This topic describes support for type conversions in F#.</span></span>

## <a name="arithmetic-types"></a><span data-ttu-id="93367-105">Aritmetické typy</span><span class="sxs-lookup"><span data-stu-id="93367-105">Arithmetic Types</span></span>

<span data-ttu-id="93367-106">F#poskytuje operátory převodu pro aritmetické převody mezi různými primitivními typy, jako je například typ Integer a plovoucí desetinná čárka.</span><span class="sxs-lookup"><span data-stu-id="93367-106">F# provides conversion operators for arithmetic conversions between various primitive types, such as between integer and floating point types.</span></span> <span data-ttu-id="93367-107">Operátory převodu integrálu a znaků mají kontrolované a nezaškrtnuté formuláře. operátory s plovoucí desetinnou čárkou a operátor převodu `enum`.</span><span class="sxs-lookup"><span data-stu-id="93367-107">The integral and char conversion operators have checked and unchecked forms; the floating point operators and the `enum` conversion operator do not.</span></span> <span data-ttu-id="93367-108">Nezaškrtnuté formuláře jsou definovány v `Microsoft.FSharp.Core.Operators` a zaškrtnuté formuláře jsou definovány v `Microsoft.FSharp.Core.Operators.Checked`.</span><span class="sxs-lookup"><span data-stu-id="93367-108">The unchecked forms are defined in `Microsoft.FSharp.Core.Operators` and the checked forms are defined in `Microsoft.FSharp.Core.Operators.Checked`.</span></span> <span data-ttu-id="93367-109">Kontroluje kontrolované formuláře pro přetečení a generuje výjimku za běhu, pokud výsledná hodnota překračuje limity cílového typu.</span><span class="sxs-lookup"><span data-stu-id="93367-109">The checked forms check for overflow and generate a runtime exception if the resulting value exceeds the limits of the target type.</span></span>

<span data-ttu-id="93367-110">Každý z těchto operátorů má stejný název jako název cílového typu.</span><span class="sxs-lookup"><span data-stu-id="93367-110">Each of these operators has the same name as the name of the destination type.</span></span> <span data-ttu-id="93367-111">Například v následujícím kódu, ve kterém jsou typy explicitně opatřeny poznámkami, `byte` se zobrazí se dvěma různými významy.</span><span class="sxs-lookup"><span data-stu-id="93367-111">For example, in the following code, in which the types are explicitly annotated, `byte` appears with two different meanings.</span></span> <span data-ttu-id="93367-112">První výskyt je typ a druhý je operátor převodu.</span><span class="sxs-lookup"><span data-stu-id="93367-112">The first occurrence is the type and the second is the conversion operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4401.fs)]

<span data-ttu-id="93367-113">V následující tabulce jsou uvedeny operátory převodu definované F#v.</span><span class="sxs-lookup"><span data-stu-id="93367-113">The following table shows conversion operators defined in F#.</span></span>

|<span data-ttu-id="93367-114">Operátor</span><span class="sxs-lookup"><span data-stu-id="93367-114">Operator</span></span>|<span data-ttu-id="93367-115">Popis</span><span class="sxs-lookup"><span data-stu-id="93367-115">Description</span></span>|
|--------|-----------|
|`byte`|<span data-ttu-id="93367-116">Převod na bajt, 8bitový typ bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="93367-116">Convert to byte, an 8-bit unsigned type.</span></span>|
|`sbyte`|<span data-ttu-id="93367-117">Převod na bajt se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="93367-117">Convert to signed byte.</span></span>|
|`int16`|<span data-ttu-id="93367-118">Převede na 16bitové celé číslo se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="93367-118">Convert to a 16-bit signed integer.</span></span>|
|`uint16`|<span data-ttu-id="93367-119">Převod na 16 bitů unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="93367-119">Convert to a 16-bit unsigned integer.</span></span>|
|`int32, int`|<span data-ttu-id="93367-120">Převede na celé číslo se znaménkem 32.</span><span class="sxs-lookup"><span data-stu-id="93367-120">Convert to a 32-bit signed integer.</span></span>|
|`uint32`|<span data-ttu-id="93367-121">Převod na 32-bitovou unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="93367-121">Convert to a 32-bit unsigned integer.</span></span>|
|`int64`|<span data-ttu-id="93367-122">Převede na celé číslo se znaménkem 64.</span><span class="sxs-lookup"><span data-stu-id="93367-122">Convert to a 64-bit signed integer.</span></span>|
|`uint64`|<span data-ttu-id="93367-123">Převod na 64-bitovou unsigned integer.</span><span class="sxs-lookup"><span data-stu-id="93367-123">Convert to a 64-bit unsigned integer.</span></span>|
|`nativeint`|<span data-ttu-id="93367-124">Převést na nativní celé číslo.</span><span class="sxs-lookup"><span data-stu-id="93367-124">Convert to a native integer.</span></span>|
|`unativeint`|<span data-ttu-id="93367-125">Převod na nativní celé číslo bez znaménka.</span><span class="sxs-lookup"><span data-stu-id="93367-125">Convert to an unsigned native integer.</span></span>|
|`float, double`|<span data-ttu-id="93367-126">Převeďte na 64 čísla s plovoucí desetinnou čárkou s dvojitou přesností IEEE.</span><span class="sxs-lookup"><span data-stu-id="93367-126">Convert to a 64-bit double-precision IEEE floating point number.</span></span>|
|`float32, single`|<span data-ttu-id="93367-127">Převod na 32 číslo s plovoucí desetinnou čárkou s jednoduchou přesností.</span><span class="sxs-lookup"><span data-stu-id="93367-127">Convert to a 32-bit single-precision IEEE floating point number.</span></span>|
|`decimal`|<span data-ttu-id="93367-128">Převést na `System.Decimal`.</span><span class="sxs-lookup"><span data-stu-id="93367-128">Convert to `System.Decimal`.</span></span>|
|`char`|<span data-ttu-id="93367-129">Převést na `System.Char`, znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="93367-129">Convert to `System.Char`, a Unicode character.</span></span>|
|`enum`|<span data-ttu-id="93367-130">Převod na Výčtový typ.</span><span class="sxs-lookup"><span data-stu-id="93367-130">Convert to an enumerated type.</span></span>|

<span data-ttu-id="93367-131">Kromě integrovaných primitivních typů můžete použít tyto operátory s typy, které implementují `op_Explicit` nebo `op_Implicit` metody s příslušnými signaturami.</span><span class="sxs-lookup"><span data-stu-id="93367-131">In addition to built-in primitive types, you can use these operators with types that implement `op_Explicit` or `op_Implicit` methods with appropriate signatures.</span></span> <span data-ttu-id="93367-132">Například operátor převodu `int` pracuje s jakýmkoli typem, který poskytuje statickou metodu `op_Explicit`, která přebírá typ jako parametr a vrací `int`.</span><span class="sxs-lookup"><span data-stu-id="93367-132">For example, the `int` conversion operator works with any type that provides a static method `op_Explicit` that takes the type as a parameter and returns `int`.</span></span> <span data-ttu-id="93367-133">Jako speciální výjimka pro obecné pravidlo, že metody nemohou být přetíženy návratovým typem, můžete to provést pro `op_Explicit` a `op_Implicit`.</span><span class="sxs-lookup"><span data-stu-id="93367-133">As a special exception to the general rule that methods cannot be overloaded by return type, you can do this for `op_Explicit` and `op_Implicit`.</span></span>

## <a name="enumerated-types"></a><span data-ttu-id="93367-134">Výčtové typy</span><span class="sxs-lookup"><span data-stu-id="93367-134">Enumerated Types</span></span>

<span data-ttu-id="93367-135">Operátor `enum` je obecný operátor, který přijímá jeden parametr typu, který představuje typ `enum` pro převod na.</span><span class="sxs-lookup"><span data-stu-id="93367-135">The `enum` operator is a generic operator that takes one type parameter that represents the type of the `enum` to convert to.</span></span> <span data-ttu-id="93367-136">Když se převede na Výčtový typ, pokusy o odvození typu určují typ `enum`, na který chcete převést.</span><span class="sxs-lookup"><span data-stu-id="93367-136">When it converts to an enumerated type, type inference attempts to determine the type of the `enum` that you want to convert to.</span></span> <span data-ttu-id="93367-137">V následujícím příkladu není proměnná `col1` explicitně Poznáma, ale její typ je odvozen z pozdějšího testu rovnosti.</span><span class="sxs-lookup"><span data-stu-id="93367-137">In the following example, the variable `col1` is not explicitly annotated, but its type is inferred from the later equality test.</span></span> <span data-ttu-id="93367-138">Proto může kompilátor odvodit, že převedete na výčet `Color`.</span><span class="sxs-lookup"><span data-stu-id="93367-138">Therefore, the compiler can deduce that you are converting to a `Color` enumeration.</span></span> <span data-ttu-id="93367-139">Alternativně můžete zadat anotaci typu, jak je uvedeno v následujícím příkladu `col2`.</span><span class="sxs-lookup"><span data-stu-id="93367-139">Alternatively, you can supply a type annotation, as with `col2` in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4402.fs)]

<span data-ttu-id="93367-140">Cílový typ výčtu můžete zadat také explicitně jako parametr typu, jak je uvedeno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="93367-140">You can also specify the target enumeration type explicitly as a type parameter, as in the following code:</span></span>

```fsharp
let col3 = enum<Color> 3
```

<span data-ttu-id="93367-141">Všimněte si, že přetypování výčtu funguje pouze v případě, že podkladový typ výčtu je kompatibilní s převáděným typem.</span><span class="sxs-lookup"><span data-stu-id="93367-141">Note that the enumeration casts work only if the underlying type of the enumeration is compatible with the type being converted.</span></span> <span data-ttu-id="93367-142">V následujícím kódu se převod nezdařil, protože se neshoduje mezi `int32` a `uint32`.</span><span class="sxs-lookup"><span data-stu-id="93367-142">In the following code, the conversion fails to compile because of the mismatch between `int32` and `uint32`.</span></span>

```fsharp
// Error: types are incompatible
let col4 : Color = enum 2u
```

<span data-ttu-id="93367-143">Další informace naleznete v tématu [výčty](enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="93367-143">For more information, see [Enumerations](enumerations.md).</span></span>

## <a name="casting-object-types"></a><span data-ttu-id="93367-144">Přetypování typů objektů</span><span class="sxs-lookup"><span data-stu-id="93367-144">Casting Object Types</span></span>

<span data-ttu-id="93367-145">Převod mezi typy v hierarchii objektů je zásadní pro objektově orientované programování.</span><span class="sxs-lookup"><span data-stu-id="93367-145">Conversion between types in an object hierarchy is fundamental to object-oriented programming.</span></span> <span data-ttu-id="93367-146">Existují dva základní typy převodů: přetypování (přetypování) a přetypování (potřeby).</span><span class="sxs-lookup"><span data-stu-id="93367-146">There are two basic types of conversions: casting up (upcasting) and casting down (downcasting).</span></span> <span data-ttu-id="93367-147">Při přetypování hierarchie znamená přetypování z odvozeného objektu na odkaz na základní objekt.</span><span class="sxs-lookup"><span data-stu-id="93367-147">Casting up a hierarchy means casting from a derived object reference to a base object reference.</span></span> <span data-ttu-id="93367-148">Takovému přetypování je zaručeno, že bude fungovat, pokud je základní třída v hierarchii dědičnosti odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="93367-148">Such a cast is guaranteed to work as long as the base class is in the inheritance hierarchy of the derived class.</span></span> <span data-ttu-id="93367-149">Přetypování dolů v hierarchii ze základního objektu na odkaz na odvozený objekt je úspěšný pouze v případě, že objekt je ve skutečnosti instancí správného cílového (odvozeného) typu nebo typu odvozeného z cílového typu.</span><span class="sxs-lookup"><span data-stu-id="93367-149">Casting down a hierarchy, from a base object reference to a derived object reference, succeeds only if the object actually is an instance of the correct destination (derived) type or a type derived from the destination type.</span></span>

<span data-ttu-id="93367-150">F#poskytuje operátory pro tyto typy převodů.</span><span class="sxs-lookup"><span data-stu-id="93367-150">F# provides operators for these types of conversions.</span></span> <span data-ttu-id="93367-151">Operátor `:>` přetypování hierarchii a operátor `:?>` přetypování dolů na hierarchii.</span><span class="sxs-lookup"><span data-stu-id="93367-151">The `:>` operator casts up the hierarchy, and the `:?>` operator casts down the hierarchy.</span></span>

### <a name="upcasting"></a><span data-ttu-id="93367-152">Přetypování</span><span class="sxs-lookup"><span data-stu-id="93367-152">Upcasting</span></span>

<span data-ttu-id="93367-153">V mnoha objektově orientovaných jazycích je přetypování implicitní. v F#nástroji se pravidla mírně liší.</span><span class="sxs-lookup"><span data-stu-id="93367-153">In many object-oriented languages, upcasting is implicit; in F#, the rules are slightly different.</span></span> <span data-ttu-id="93367-154">Při předávání argumentů metodám typu objektu je přetypování použito automaticky.</span><span class="sxs-lookup"><span data-stu-id="93367-154">Upcasting is applied automatically when you pass arguments to methods on an object type.</span></span> <span data-ttu-id="93367-155">Pro funkce vázané na let v modulu však není automatické přetypování automatické, pokud typ parametru není deklarován jako flexibilní typ.</span><span class="sxs-lookup"><span data-stu-id="93367-155">However, for let-bound functions in a module, upcasting is not automatic, unless the parameter type is declared as a flexible type.</span></span> <span data-ttu-id="93367-156">Další informace naleznete v tématu [flexibilní typy](flexible-Types.md).</span><span class="sxs-lookup"><span data-stu-id="93367-156">For more information, see [Flexible Types](flexible-Types.md).</span></span>

<span data-ttu-id="93367-157">Operátor `:>` provádí statické přetypování, což znamená, že úspěch přetypování je určen v době kompilace.</span><span class="sxs-lookup"><span data-stu-id="93367-157">The `:>` operator performs a static cast, which means that the success of the cast is determined at compile time.</span></span> <span data-ttu-id="93367-158">Pokud přetypování, které používá `:>`, je úspěšně zkompilováno, jedná se o platné přetypování a v době běhu není pravděpodobné selhání.</span><span class="sxs-lookup"><span data-stu-id="93367-158">If a cast that uses `:>` compiles successfully, it is a valid cast and has no chance of failure at run time.</span></span>

<span data-ttu-id="93367-159">K provedení takového převodu můžete použít také operátor `upcast`.</span><span class="sxs-lookup"><span data-stu-id="93367-159">You can also use the `upcast` operator to perform such a conversion.</span></span> <span data-ttu-id="93367-160">Následující výraz určuje převod hierarchie:</span><span class="sxs-lookup"><span data-stu-id="93367-160">The following expression specifies a conversion up the hierarchy:</span></span>

```fsharp
upcast expression
```

<span data-ttu-id="93367-161">Při použití operátoru přetypování se kompilátor pokusí odvodit typ, na který převádíte z kontextu.</span><span class="sxs-lookup"><span data-stu-id="93367-161">When you use the upcast operator, the compiler attempts to infer the type you are converting to from the context.</span></span> <span data-ttu-id="93367-162">Pokud kompilátor nemůže určit cílový typ, kompilátor ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="93367-162">If the compiler is unable to determine the target type, the compiler reports an error.</span></span> <span data-ttu-id="93367-163">Může být vyžadována anotace typu.</span><span class="sxs-lookup"><span data-stu-id="93367-163">A type annotation may be required.</span></span>

### <a name="downcasting"></a><span data-ttu-id="93367-164">Potřeby</span><span class="sxs-lookup"><span data-stu-id="93367-164">Downcasting</span></span>

<span data-ttu-id="93367-165">Operátor `:?>` provádí dynamické přetypování, což znamená, že úspěch přetypování je určen v době běhu.</span><span class="sxs-lookup"><span data-stu-id="93367-165">The `:?>` operator performs a dynamic cast, which means that the success of the cast is determined at run time.</span></span> <span data-ttu-id="93367-166">Přetypování, které používá operátor `:?>`, není kontrolováno v době kompilace; v době spuštění se ale za běhu provede pokus o přetypování na zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="93367-166">A cast that uses the `:?>` operator is not checked at compile time; but at run time, an attempt is made to cast to the specified type.</span></span> <span data-ttu-id="93367-167">Pokud je objekt kompatibilní s cílovým typem, přetypování je úspěšné.</span><span class="sxs-lookup"><span data-stu-id="93367-167">If the object is compatible with the target type, the cast succeeds.</span></span> <span data-ttu-id="93367-168">Pokud objekt není kompatibilní s cílovým typem, modul runtime vyvolá `InvalidCastException`.</span><span class="sxs-lookup"><span data-stu-id="93367-168">If the object is not compatible with the target type, the runtime raises an `InvalidCastException`.</span></span>

<span data-ttu-id="93367-169">Pomocí operátoru `downcast` lze také provést převod dynamického typu.</span><span class="sxs-lookup"><span data-stu-id="93367-169">You can also use the `downcast` operator to perform a dynamic type conversion.</span></span> <span data-ttu-id="93367-170">Následující výraz určuje převod mimo hierarchii na typ, který je odvozen z kontextu programu:</span><span class="sxs-lookup"><span data-stu-id="93367-170">The following expression specifies a conversion down the hierarchy to a type that is inferred from program context:</span></span>

```fsharp
downcast expression
```

<span data-ttu-id="93367-171">Jako operátor `upcast`, pokud kompilátor nemůže odvodit konkrétní cílový typ z kontextu, ohlásí chybu.</span><span class="sxs-lookup"><span data-stu-id="93367-171">As for the `upcast` operator, if the compiler cannot infer a specific target type from the context, it reports an error.</span></span> <span data-ttu-id="93367-172">Může být vyžadována anotace typu.</span><span class="sxs-lookup"><span data-stu-id="93367-172">A type annotation may be required.</span></span>

<span data-ttu-id="93367-173">Následující kód ilustruje použití operátorů `:>` a `:?>`.</span><span class="sxs-lookup"><span data-stu-id="93367-173">The following code illustrates the use of the `:>` and `:?>` operators.</span></span> <span data-ttu-id="93367-174">Kód ilustruje, že operátor `:?>` je nejlépe použit, pokud víte, že převod proběhne úspěšně, protože vyvolá `InvalidCastException`, pokud převod selže.</span><span class="sxs-lookup"><span data-stu-id="93367-174">The code illustrates that the `:?>` operator is best used when you know that conversion will succeed, because it throws `InvalidCastException` if the conversion fails.</span></span> <span data-ttu-id="93367-175">Pokud si nejste jisti, že převod proběhne úspěšně, test typu, který používá výraz `match` je lepší, protože se vyhne režii vygenerování výjimky.</span><span class="sxs-lookup"><span data-stu-id="93367-175">If you do not know that a conversion will succeed, a type test that uses a `match` expression is better because it avoids the overhead of generating an exception.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4403.fs)]

<span data-ttu-id="93367-176">Vzhledem k tomu, že obecné operátory `downcast` a `upcast` spoléhají na odvození typu k určení argumentu a návratového typu ve výše uvedeném kódu, můžete nahradit</span><span class="sxs-lookup"><span data-stu-id="93367-176">Because generic operators `downcast` and `upcast` rely on type inference to determine the argument and return type, in the above code, you can replace</span></span>

```fsharp
let base1 = d1 :> Base1
```

<span data-ttu-id="93367-177">with</span><span class="sxs-lookup"><span data-stu-id="93367-177">with</span></span>

```fsharp
let base1: Base1 = upcast d1
```

<span data-ttu-id="93367-178">Všimněte si, že je požadována anotace typu, protože `upcast` sama o sobě nemohla určit základní třídu.</span><span class="sxs-lookup"><span data-stu-id="93367-178">Note that a type annotation is required, since `upcast` by itself could not determine the base class.</span></span>

## <a name="see-also"></a><span data-ttu-id="93367-179">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93367-179">See also</span></span>

- [<span data-ttu-id="93367-180">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="93367-180">F# Language Reference</span></span>](index.md)
