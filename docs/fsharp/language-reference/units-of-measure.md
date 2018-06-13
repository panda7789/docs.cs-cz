---
title: Měrné jednotky (F#)
description: 'Zjistěte, jak plovoucí desetinná čárka a číslo se znaménkem hodnoty v jazyce F # mohou být přidruženy jednotky míry, které jsou obvykle používány k označení Délka svazku a velkokapacitních.'
ms.date: 05/16/2016
ms.openlocfilehash: 3e47c92100c1dd99161be709a065913f501854f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564948"
---
# <a name="units-of-measure"></a><span data-ttu-id="55888-103">Měrné jednotky</span><span class="sxs-lookup"><span data-stu-id="55888-103">Units of Measure</span></span>

<span data-ttu-id="55888-104">Plovoucí desetinná čárka a číslo se znaménkem hodnoty v jazyce F # může mít přidružené jednotky míry, které jsou obvykle používány k označení délku svazku, hromadně, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="55888-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="55888-105">Pomocí počty jednotek, povolíte kompilátor ověřit, že aritmetické vztahy mají správnou jednotky, která pomáhá zabránit programování chyby.</span><span class="sxs-lookup"><span data-stu-id="55888-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>


## <a name="syntax"></a><span data-ttu-id="55888-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="55888-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="55888-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="55888-107">Remarks</span></span>
<span data-ttu-id="55888-108">Definuje předchozí syntaxe *název jednotky* jako jednotku míry.</span><span class="sxs-lookup"><span data-stu-id="55888-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="55888-109">Volitelná součást se používá k definování novou míru z hlediska dříve definovaném jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="55888-110">Například následující řádek definuje míry `cm` (centimetr).</span><span class="sxs-lookup"><span data-stu-id="55888-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="55888-111">Následující řádek definuje míry `ml` (milliliter) jako krychlový centimetru (`cm^3`).</span><span class="sxs-lookup"><span data-stu-id="55888-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="55888-112">V předchozích syntaxi *měr* je vzorec, který zahrnuje jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="55888-113">Ve vzorcích, které zahrnují jednotky, integrální zajišťuje jsou podporovány (kladné a záporné), mezery mezi jednotky znamenat součin dvou jednotky `*` také určuje produktem jednotky, a `/` označuje podíl jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="55888-114">Pro vzájemné jednotku, můžete použít buď power záporné celé číslo nebo `/` určující oddělení mezi čítači a jmenovatel vzorec jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="55888-115">Několik jednotek v jmenovatel by měl být uzavřeny v závorkách.</span><span class="sxs-lookup"><span data-stu-id="55888-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="55888-116">Jednotky oddělené mezerami po `/` se interpretují jako součást jmenovatel, ale žádné jednotky následující `*` se interpretují jako součást čítači.</span><span class="sxs-lookup"><span data-stu-id="55888-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="55888-117">1 můžete použít ve výrazech jednotek, buď udávajících bezrozměrný množství, samostatně nebo společně s další jednotky, například v čítači.</span><span class="sxs-lookup"><span data-stu-id="55888-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="55888-118">Například jednotky pro na míru by byla zapsána jako `1/s`, kde `s` určuje v sekundách.</span><span class="sxs-lookup"><span data-stu-id="55888-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="55888-119">V jednotce vzorce nejsou použity závorky.</span><span class="sxs-lookup"><span data-stu-id="55888-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="55888-120">Nezadáte číselný převod konstanty ve vzorcích jednotky; Můžete však definovat převod konstanty u jednotek samostatně a použít na jednotku zaškrtnutí výpočty.</span><span class="sxs-lookup"><span data-stu-id="55888-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="55888-121">Jednotka vzorce, které mají stejný význam může být napsán v různých způsobů ekvivalentní.</span><span class="sxs-lookup"><span data-stu-id="55888-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="55888-122">Proto kompilátor převede jednotky vzorce konzistentní formulář, který převede záporné zajišťuje recipročních, jednotky skupiny na jednom čítači a jmenovatel a seřadí podle abecedy jednotky v čítači a jmenovatel.</span><span class="sxs-lookup"><span data-stu-id="55888-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="55888-123">Například jednotky vzorce `kg m s^-2` a `m /s s * kg` se převedou na `kg m/s^2`.</span><span class="sxs-lookup"><span data-stu-id="55888-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="55888-124">Ve výrazech plovoucí bod použijete měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="55888-125">Pomocí čísla s plovoucí desetinnou společně s přidružené jednotky míry zvyšuje úroveň zabezpečení typů a pomáhá zabránit chybách neshoda jednotky, ke kterým může dojít ve vzorcích, když používáte slabě typovaná čísla s plovoucí desetinnou.</span><span class="sxs-lookup"><span data-stu-id="55888-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="55888-126">Pokud píšete plovoucí bodu výraz, který používá jednotky, musí odpovídat jednotky ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="55888-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="55888-127">Literály se vzorcem jednotky v lomených závorkách může opatřit poznámkami, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="55888-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="55888-128">Nevkládejte mezeru mezi číslo a lomená závorka; však může zahrnovat příponou literálu, jako `f`, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="55888-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="55888-129">Tyto poznámky změní typ literálové z jeho primitivní typ (například `float`) typu rozměry, jako `float<cm>` nebo v tomto případě `float<miles/hour>`.</span><span class="sxs-lookup"><span data-stu-id="55888-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="55888-130">Jednotka anotaci objektu `<1>` označuje bezrozměrný množství a její typ je ekvivalentní primitivní typ bez parametru jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="55888-131">Typ měrné jednotky plovoucí desetinné čárky nebo podepsané integrální typ společně s poznámky další jednotky, uvedeným v závorkách.</span><span class="sxs-lookup"><span data-stu-id="55888-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="55888-132">Proto při psaní typ převodu z `g` (gram) k `kg` (kg), které popisují typy následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="55888-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="55888-133">Měrné jednotky se používají pro jednotku kompilace kontrola ale nejsou trvalé v běhové prostředí.</span><span class="sxs-lookup"><span data-stu-id="55888-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="55888-134">Proto že nemají vliv výkon.</span><span class="sxs-lookup"><span data-stu-id="55888-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="55888-135">Měrné jednotky lze použít k libovolnému typu, nikoli pouze plovoucí typy bodů; však pouze plovoucí typy bodů podepsané integrální typy a počty podporu dimenzovány decimal typy.</span><span class="sxs-lookup"><span data-stu-id="55888-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="55888-136">Proto pouze má smysl používat jednotky, na primitivní typy a agregace, které obsahují tyto primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="55888-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="55888-137">Následující příklad ukazuje použití měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]
    
<span data-ttu-id="55888-138">Následující příklad kódu ukazuje, jak převést z bezrozměrný číslo s plovoucí desetinnou čárkou rozměry hodnotu s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="55888-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="55888-139">Jste právě vynásobit 1.0, dimenze použití rozhraní 1.0.</span><span class="sxs-lookup"><span data-stu-id="55888-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="55888-140">Můžete to abstraktní do funkce jako `degreesFahrenheit`.</span><span class="sxs-lookup"><span data-stu-id="55888-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="55888-141">Navíc pokud předáte rozměry hodnoty na funkce, které očekávají bezrozměrný čísla s plovoucí desetinnou, musíte zrušit jednotky nebo přetypovat na `float` pomocí `float` operátor.</span><span class="sxs-lookup"><span data-stu-id="55888-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="55888-142">V tomto příkladu budete provádět dělení po `1.0<degC>` pro argumenty, které mají `printf` protože `printf` očekává bezrozměrný počty.</span><span class="sxs-lookup"><span data-stu-id="55888-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="55888-143">Následující příklad relace se zobrazuje výstup z a vstupy pro tento kód.</span><span class="sxs-lookup"><span data-stu-id="55888-143">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="55888-144">Pomocí obecné jednotky</span><span class="sxs-lookup"><span data-stu-id="55888-144">Using Generic Units</span></span>
<span data-ttu-id="55888-145">Obecné funkce, které provozují může zapisovat na data, která je přidružená Měrná jednotka má.</span><span class="sxs-lookup"><span data-stu-id="55888-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="55888-146">To uděláte tak, že zadáte typu společně s Obecné jednotky jako parametr typu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="55888-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]
    
## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="55888-147">Vytváření typů agregace s Obecné jednotky</span><span class="sxs-lookup"><span data-stu-id="55888-147">Creating Aggregate Types with Generic Units</span></span>
<span data-ttu-id="55888-148">Následující kód ukazuje, jak vytvořit typ agregace, který se skládá z jednotlivých hodnot s plovoucí desetinnou mající jednotkách, které jsou obecné.</span><span class="sxs-lookup"><span data-stu-id="55888-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="55888-149">To umožňuje vytvořit jeden typ, který funguje s různými jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="55888-150">Obecné jednotky navíc zachovávají bezpečnost typů tím zajistí, že obecného typu, který má jednu sadu jednotky je jiného typu než stejné obecného typu pomocí jiné sady jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="55888-151">Základ pro tento postup je, že `Measure` atribut lze použít pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="55888-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]
    
## <a name="units-at-runtime"></a><span data-ttu-id="55888-152">Jednotky při běhu</span><span class="sxs-lookup"><span data-stu-id="55888-152">Units at Runtime</span></span>
<span data-ttu-id="55888-153">Měrné jednotky se používají pro kontrolu statického typu.</span><span class="sxs-lookup"><span data-stu-id="55888-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="55888-154">Když hodnot s plovoucí desetinnou kompilovány, jednotky, jsou odstraněny, tak s jednotkami jsou ztraceny za běhu.</span><span class="sxs-lookup"><span data-stu-id="55888-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="55888-155">Pokusy o implementovat funkce, které závisí na Kontrola jednotky v době běhu proto není možné.</span><span class="sxs-lookup"><span data-stu-id="55888-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="55888-156">Například implementace `ToString` funkce vytiskněte jednotky není možné.</span><span class="sxs-lookup"><span data-stu-id="55888-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>


## <a name="conversions"></a><span data-ttu-id="55888-157">Převody</span><span class="sxs-lookup"><span data-stu-id="55888-157">Conversions</span></span>
<span data-ttu-id="55888-158">Převést typ, který má jednotky (například `float<'u>`) na typ, který nemá jednotky, můžete použít funkci standardní převod.</span><span class="sxs-lookup"><span data-stu-id="55888-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="55888-159">Například můžete použít `float` převést `float` hodnotu, která nemá jednotek, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="55888-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="55888-160">Převést hodnotu unitless na hodnotu, která má jednotky, můžete hodnotu 1 nebo 1.0, která je označena vynásobit v odpovídajících jednotkách.</span><span class="sxs-lookup"><span data-stu-id="55888-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="55888-161">Pro psaní interoperabilita vrstev, existují však také některé explicitní funkce, které můžete použít k převodu unitless hodnoty na hodnoty s jednotky.</span><span class="sxs-lookup"><span data-stu-id="55888-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="55888-162">Toto jsou v [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modulu.</span><span class="sxs-lookup"><span data-stu-id="55888-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="55888-163">Například pro převod unitless `float` k `float<cm>`, použijte [floatwithmeasure –](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="55888-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]
    
## <a name="units-of-measure-in-the-f-power-pack"></a><span data-ttu-id="55888-164">Jednotky, v F # Power Pack</span><span class="sxs-lookup"><span data-stu-id="55888-164">Units of Measure in the F# Power Pack</span></span>
<span data-ttu-id="55888-165">Jednotka knihovny je k dispozici v PowerPack F #.</span><span class="sxs-lookup"><span data-stu-id="55888-165">A unit library is available in the F# PowerPack.</span></span> <span data-ttu-id="55888-166">Jednotka knihovny zahrnuje jednotek SI a fyzické konstanty.</span><span class="sxs-lookup"><span data-stu-id="55888-166">The unit library includes SI units and physical constants.</span></span>


## <a name="see-also"></a><span data-ttu-id="55888-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="55888-167">See Also</span></span>
[<span data-ttu-id="55888-168">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="55888-168">F# Language Reference</span></span>](index.md)
