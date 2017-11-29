---
title: "Měrné jednotky (F#)"
description: "Zjistěte, jak plovoucí desetinná čárka a číslo se znaménkem hodnoty v jazyce F # mohou být přidruženy jednotky míry, které jsou obvykle používány k označení Délka svazku a velkokapacitních."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: cb2eb658-df6c-422e-afad-97422609c773
ms.openlocfilehash: 2d0683e864c5684a78c02e177c296d3067295723
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="units-of-measure"></a><span data-ttu-id="4c992-104">Měrné jednotky</span><span class="sxs-lookup"><span data-stu-id="4c992-104">Units of Measure</span></span>

<span data-ttu-id="4c992-105">Plovoucí desetinná čárka a číslo se znaménkem hodnoty v jazyce F # může mít přidružené jednotky míry, které jsou obvykle používány k označení délku svazku, hromadně, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4c992-105">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="4c992-106">Pomocí počty jednotek, povolíte kompilátor ověřit, že aritmetické vztahy mají správnou jednotky, která pomáhá zabránit programování chyby.</span><span class="sxs-lookup"><span data-stu-id="4c992-106">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>


## <a name="syntax"></a><span data-ttu-id="4c992-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c992-107">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="4c992-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c992-108">Remarks</span></span>
<span data-ttu-id="4c992-109">Definuje předchozí syntaxe *název jednotky* jako jednotku míry.</span><span class="sxs-lookup"><span data-stu-id="4c992-109">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="4c992-110">Volitelná součást se používá k definování novou míru z hlediska dříve definovaném jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-110">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="4c992-111">Například následující řádek definuje míry `cm` (centimetr).</span><span class="sxs-lookup"><span data-stu-id="4c992-111">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="4c992-112">Následující řádek definuje míry `ml` (milliliter) jako krychlový centimetru (`cm^3`).</span><span class="sxs-lookup"><span data-stu-id="4c992-112">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="4c992-113">V předchozích syntaxi *měr* je vzorec, který zahrnuje jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-113">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="4c992-114">Ve vzorcích, které zahrnují jednotky, integrální zajišťuje jsou podporovány (kladné a záporné), mezery mezi jednotky znamenat součin dvou jednotky `*` také určuje produktem jednotky, a `/` označuje podíl jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-114">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="4c992-115">Pro vzájemné jednotku, můžete použít buď power záporné celé číslo nebo `/` určující oddělení mezi čítači a jmenovatel vzorec jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-115">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="4c992-116">Několik jednotek v jmenovatel by měl být uzavřeny v závorkách.</span><span class="sxs-lookup"><span data-stu-id="4c992-116">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="4c992-117">Jednotky oddělené mezerami po `/` se interpretují jako součást jmenovatel, ale žádné jednotky následující `*` se interpretují jako součást čítači.</span><span class="sxs-lookup"><span data-stu-id="4c992-117">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="4c992-118">1 můžete použít ve výrazech jednotek, buď udávajících bezrozměrný množství, samostatně nebo společně s další jednotky, například v čítači.</span><span class="sxs-lookup"><span data-stu-id="4c992-118">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="4c992-119">Například jednotky pro na míru by byla zapsána jako `1/s`, kde `s` určuje v sekundách.</span><span class="sxs-lookup"><span data-stu-id="4c992-119">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="4c992-120">V jednotce vzorce nejsou použity závorky.</span><span class="sxs-lookup"><span data-stu-id="4c992-120">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="4c992-121">Nezadáte číselný převod konstanty ve vzorcích jednotky; Můžete však definovat převod konstanty u jednotek samostatně a použít na jednotku zaškrtnutí výpočty.</span><span class="sxs-lookup"><span data-stu-id="4c992-121">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="4c992-122">Jednotka vzorce, které mají stejný význam může být napsán v různých způsobů ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="4c992-122">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="4c992-123">Proto kompilátor převede jednotky vzorce konzistentní formulář, který převede záporné zajišťuje recipročních, jednotky skupiny na jednom čítači a jmenovatel a seřadí podle abecedy jednotky v čítači a jmenovatel.</span><span class="sxs-lookup"><span data-stu-id="4c992-123">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="4c992-124">Například jednotky vzorce `kg m s^-2` a `m /s s * kg` se převedou na `kg m/s^2`.</span><span class="sxs-lookup"><span data-stu-id="4c992-124">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="4c992-125">Ve výrazech plovoucí bod použijete měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-125">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="4c992-126">Pomocí čísla s plovoucí desetinnou společně s přidružené jednotky míry zvyšuje úroveň zabezpečení typů a pomáhá zabránit chybách neshoda jednotky, ke kterým může dojít ve vzorcích, když používáte slabě typovaná čísla s plovoucí desetinnou.</span><span class="sxs-lookup"><span data-stu-id="4c992-126">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="4c992-127">Pokud píšete plovoucí bodu výraz, který používá jednotky, musí odpovídat jednotky ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="4c992-127">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="4c992-128">Literály se vzorcem jednotky v lomených závorkách může opatřit poznámkami, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="4c992-128">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="4c992-129">Nevkládejte mezeru mezi číslo a lomená závorka; však může zahrnovat příponou literálu, jako `f`, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4c992-129">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="4c992-130">Tyto poznámky změní typ literálové z jeho primitivní typ (například `float`) typu rozměry, jako `float<cm>` nebo v tomto případě `float<miles/hour>`.</span><span class="sxs-lookup"><span data-stu-id="4c992-130">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="4c992-131">Jednotka anotaci objektu `<1>` označuje bezrozměrný množství a její typ je ekvivalentní primitivní typ bez parametru jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-131">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="4c992-132">Typ měrné jednotky plovoucí desetinné čárky nebo podepsané integrální typ společně s poznámky další jednotky, uvedeným v závorkách.</span><span class="sxs-lookup"><span data-stu-id="4c992-132">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="4c992-133">Proto při psaní typ převodu z `g` (gram) k `kg` (kg), které popisují typy následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="4c992-133">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="4c992-134">Měrné jednotky se používají pro jednotku kompilace kontrola ale nejsou trvalé v běhové prostředí.</span><span class="sxs-lookup"><span data-stu-id="4c992-134">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="4c992-135">Proto že nemají vliv výkon.</span><span class="sxs-lookup"><span data-stu-id="4c992-135">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="4c992-136">Měrné jednotky lze použít k libovolnému typu, nikoli pouze plovoucí typy bodů; však pouze plovoucí typy bodů podepsané integrální typy a počty podporu dimenzovány decimal typy.</span><span class="sxs-lookup"><span data-stu-id="4c992-136">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="4c992-137">Proto pouze má smysl používat jednotky, na primitivní typy a agregace, které obsahují tyto primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="4c992-137">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="4c992-138">Následující příklad ukazuje použití měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-138">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
<span data-ttu-id="4c992-139">Následující příklad kódu ukazuje, jak převést z bezrozměrný číslo s plovoucí desetinnou čárkou rozměry hodnotu s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="4c992-139">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="4c992-140">Jste právě vynásobit 1.0, dimenze použití rozhraní 1.0.</span><span class="sxs-lookup"><span data-stu-id="4c992-140">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="4c992-141">Můžete to abstraktní do funkce jako `degreesFahrenheit`.</span><span class="sxs-lookup"><span data-stu-id="4c992-141">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="4c992-142">Navíc pokud předáte rozměry hodnoty na funkce, které očekávají bezrozměrný čísla s plovoucí desetinnou, musíte zrušit jednotky nebo přetypovat na `float` pomocí `float` operátor.</span><span class="sxs-lookup"><span data-stu-id="4c992-142">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="4c992-143">V tomto příkladu budete provádět dělení po `1.0<degC>` pro argumenty, které mají `printf` protože `printf` očekává bezrozměrný počty.</span><span class="sxs-lookup"><span data-stu-id="4c992-143">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="4c992-144">Následující příklad relace se zobrazuje výstup z a vstupy pro tento kód.</span><span class="sxs-lookup"><span data-stu-id="4c992-144">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="4c992-145">Pomocí obecné jednotky</span><span class="sxs-lookup"><span data-stu-id="4c992-145">Using Generic Units</span></span>
<span data-ttu-id="4c992-146">Obecné funkce, které provozují může zapisovat na data, která je přidružená Měrná jednotka má.</span><span class="sxs-lookup"><span data-stu-id="4c992-146">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="4c992-147">To uděláte tak, že zadáte typu společně s Obecné jednotky jako parametr typu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4c992-147">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="4c992-148">Vytváření typů agregace s Obecné jednotky</span><span class="sxs-lookup"><span data-stu-id="4c992-148">Creating Aggregate Types with Generic Units</span></span>
<span data-ttu-id="4c992-149">Následující kód ukazuje, jak vytvořit typ agregace, který se skládá z jednotlivých hodnot s plovoucí desetinnou mající jednotkách, které jsou obecné.</span><span class="sxs-lookup"><span data-stu-id="4c992-149">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="4c992-150">To umožňuje vytvořit jeden typ, který funguje s různými jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-150">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="4c992-151">Obecné jednotky navíc zachovávají bezpečnost typů tím zajistí, že obecného typu, který má jednu sadu jednotky je jiného typu než stejné obecného typu pomocí jiné sady jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-151">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="4c992-152">Základ pro tento postup je, že `Measure` atribut lze použít pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="4c992-152">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a><span data-ttu-id="4c992-153">Jednotky při běhu</span><span class="sxs-lookup"><span data-stu-id="4c992-153">Units at Runtime</span></span>
<span data-ttu-id="4c992-154">Měrné jednotky se používají pro kontrolu statického typu.</span><span class="sxs-lookup"><span data-stu-id="4c992-154">Units of measure are used for static type checking.</span></span> <span data-ttu-id="4c992-155">Když hodnot s plovoucí desetinnou kompilovány, jednotky, jsou odstraněny, tak s jednotkami jsou ztraceny za běhu.</span><span class="sxs-lookup"><span data-stu-id="4c992-155">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="4c992-156">Pokusy o implementovat funkce, které závisí na Kontrola jednotky v době běhu proto není možné.</span><span class="sxs-lookup"><span data-stu-id="4c992-156">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="4c992-157">Například implementace `ToString` funkce vytiskněte jednotky není možné.</span><span class="sxs-lookup"><span data-stu-id="4c992-157">For example, implementing a `ToString` function to print out the units is not possible.</span></span>


## <a name="conversions"></a><span data-ttu-id="4c992-158">Převody</span><span class="sxs-lookup"><span data-stu-id="4c992-158">Conversions</span></span>
<span data-ttu-id="4c992-159">Převést typ, který má jednotky (například `float<'u>`) na typ, který nemá jednotky, můžete použít funkci standardní převod.</span><span class="sxs-lookup"><span data-stu-id="4c992-159">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="4c992-160">Například můžete použít `float` převést `float` hodnotu, která nemá jednotek, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4c992-160">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="4c992-161">Převést hodnotu unitless na hodnotu, která má jednotky, můžete hodnotu 1 nebo 1.0, která je označena vynásobit v odpovídajících jednotkách.</span><span class="sxs-lookup"><span data-stu-id="4c992-161">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="4c992-162">Pro psaní interoperabilita vrstev, existují však také některé explicitní funkce, které můžete použít k převodu unitless hodnoty na hodnoty s jednotky.</span><span class="sxs-lookup"><span data-stu-id="4c992-162">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="4c992-163">Toto jsou v [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modulu.</span><span class="sxs-lookup"><span data-stu-id="4c992-163">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="4c992-164">Například pro převod unitless `float` k `float<cm>`, použijte [floatwithmeasure –](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4c992-164">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a><span data-ttu-id="4c992-165">Jednotky, v F # Power Pack</span><span class="sxs-lookup"><span data-stu-id="4c992-165">Units of Measure in the F# Power Pack</span></span>
<span data-ttu-id="4c992-166">Jednotka knihovny je k dispozici v PowerPack F #.</span><span class="sxs-lookup"><span data-stu-id="4c992-166">A unit library is available in the F# PowerPack.</span></span> <span data-ttu-id="4c992-167">Jednotka knihovny zahrnuje jednotek SI a fyzické konstanty.</span><span class="sxs-lookup"><span data-stu-id="4c992-167">The unit library includes SI units and physical constants.</span></span>


## <a name="see-also"></a><span data-ttu-id="4c992-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="4c992-168">See Also</span></span>
[<span data-ttu-id="4c992-169">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="4c992-169">F# Language Reference</span></span>](index.md)
