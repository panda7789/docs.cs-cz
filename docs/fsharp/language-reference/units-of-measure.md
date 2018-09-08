---
title: Měrné jednotky (F#)
description: 'Zjistěte, jak plovoucí desetinnou čárkou a celé číslo se znaménkem hodnoty v jazyce F # můžete mít přidružené jednotky měření, které se obvykle používají k označení délku, svazek a velkokapacitních.'
ms.date: 05/16/2016
ms.openlocfilehash: ad2193e25f3c0cee6e73cd529ab43d1e4b6b549b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44131257"
---
# <a name="units-of-measure"></a><span data-ttu-id="92fab-103">Měrné jednotky</span><span class="sxs-lookup"><span data-stu-id="92fab-103">Units of Measure</span></span>

<span data-ttu-id="92fab-104">Plovoucí desetinná čárka a číslo se znaménkem hodnoty v jazyce F # můžete mít přidružené jednotky měření, které se obvykle používají k označení délku, svazek, hmotnost, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="92fab-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="92fab-105">Pomocí množství s jednotkami povolíte kompilátor ověřte, že aritmetické vztahy mají správnou jednotek, která pomáhá zabránit programovací chyby.</span><span class="sxs-lookup"><span data-stu-id="92fab-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="92fab-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92fab-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="92fab-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92fab-107">Remarks</span></span>

<span data-ttu-id="92fab-108">Předchozí syntaxe definuje *název jednotky* jako měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="92fab-109">Volitelná součást se používá k definování novou míru dříve definované jednotkách.</span><span class="sxs-lookup"><span data-stu-id="92fab-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="92fab-110">Například následující řádek určuje míru `cm` (centimetr).</span><span class="sxs-lookup"><span data-stu-id="92fab-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="92fab-111">Následující řádek určuje míru `ml` (milliliter) jako kubické centimetru (`cm^3`).</span><span class="sxs-lookup"><span data-stu-id="92fab-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="92fab-112">V předchozí syntaxi *míru* je vzorec, který zahrnuje jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="92fab-113">Ve vzorcích, které se týkají jednotky, integrální mocniny podporují (kladné a záporné) mezery mezi jednotkami určete, součin dvou jednotky `*` také určuje produkt jednotek a `/` označuje podíl jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="92fab-114">Pro vzájemné jednotek, můžete použít buď power záporné celé číslo nebo `/` určující oddělení mezi čitatelem a jmenovatelem částí vzorce.</span><span class="sxs-lookup"><span data-stu-id="92fab-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="92fab-115">Několik jednotek v jmenovatel by měl být uzavřen v závorkách.</span><span class="sxs-lookup"><span data-stu-id="92fab-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="92fab-116">Jednotky oddělené mezerami po `/` jsou interpretovány jako součást jmenovatel, ale všechny jednotky po `*` jsou interpretovány jako součást čítač.</span><span class="sxs-lookup"><span data-stu-id="92fab-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="92fab-117">1 můžete použít ve výrazech jednotek, buď samostatně k označení bezrozměrná množství nebo společně s další jednotky, jako je například čítač.</span><span class="sxs-lookup"><span data-stu-id="92fab-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="92fab-118">Například jednotky pro mírou by byla zapsána jako `1/s`, kde `s` označuje sekund.</span><span class="sxs-lookup"><span data-stu-id="92fab-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="92fab-119">Ve vzorcích jednotek nejsou použity závorky.</span><span class="sxs-lookup"><span data-stu-id="92fab-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="92fab-120">Ve vzorcích jednotek; není zadán číselný převod konstanty ale můžete definovat převod konstanty s jednotkami samostatně a jejich použití v částí kontroluje výpočty.</span><span class="sxs-lookup"><span data-stu-id="92fab-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="92fab-121">Jednotka vzorce, které mají stejný význam je možné psát v různých ekvivalentní způsoby.</span><span class="sxs-lookup"><span data-stu-id="92fab-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="92fab-122">Proto kompilátor převede částí vzorce konzistentní formulář, který převede negativní mocniny recipročních, skupiny jednotky do jednoho čitatelem a jmenovatelem a seřadí podle abecedy jednotek v čitatelem a jmenovatelem.</span><span class="sxs-lookup"><span data-stu-id="92fab-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="92fab-123">Například jednotky vzorce `kg m s^-2` a `m /s s * kg` jsou převedeny na `kg m/s^2`.</span><span class="sxs-lookup"><span data-stu-id="92fab-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="92fab-124">Ve výrazech s plovoucí desetinnou čárkou bod použijete měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="92fab-125">Pomocí čísel s plovoucí desetinnou spolu s přidružené jednotky měření přidává další úroveň bezpečnost typů a pomáhá zabránit jednotky chybám, které se mohou vyskytnout ve vzorcích, když použijete slabě typované čísel s plovoucí desetinnou.</span><span class="sxs-lookup"><span data-stu-id="92fab-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="92fab-126">Pokud píšete plovoucí bodu výraz, který používá jednotky, musí odpovídat jednotky ve výrazu.</span><span class="sxs-lookup"><span data-stu-id="92fab-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="92fab-127">Literály s částí vzorce v lomených závorkách, může opatřit poznámkami, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="92fab-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="92fab-128">Není vložíme mezeru mezi číslo a ostré závorky; však může zahrnovat přípona literálu jako `f`, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="92fab-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="92fab-129">Taková anotace změní typ literálu z jeho primitivního typu (například `float`) rozměrový typ jako `float<cm>` nebo v tomto případě `float<miles/hour>`.</span><span class="sxs-lookup"><span data-stu-id="92fab-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="92fab-130">Jednotka anotace `<1>` označuje bezrozměrná množství a její typ je ekvivalentní primitivní typ bez parametru jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="92fab-131">Typ měrné jednotky se plovoucí desetinnou čárkou nebo společně s další jednotky anotaci, uvedené v závorkách celočíselný typ se znaménkem.</span><span class="sxs-lookup"><span data-stu-id="92fab-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="92fab-132">Proto při psaní typ převodu z `g` (g) k `kg` (kg), které popisují typy následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="92fab-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="92fab-133">Měrné jednotky se používají pro jednotku kompilace kontrolu, ale nejsou zachované v prostředí za běhu.</span><span class="sxs-lookup"><span data-stu-id="92fab-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="92fab-134">Proto neovlivňují výkon.</span><span class="sxs-lookup"><span data-stu-id="92fab-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="92fab-135">Měrné jednotky lze použít u libovolného typu, ne jenom plovoucí typy bodů; pouze typy plovoucího bodu, ale podepsané celočíselných typů a desítkové typy podporu dimenzovanými počty.</span><span class="sxs-lookup"><span data-stu-id="92fab-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="92fab-136">Proto pouze má smysl použít měrné jednotky na primitivní typy a agregátů, které obsahují tyto primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="92fab-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="92fab-137">Následující příklad ukazuje použití měrné jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="92fab-138">Následující příklad kódu ukazuje, jak převést bezrozměrná číslo s plovoucí desetinnou čárkou na dimenzované hodnotu s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="92fab-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="92fab-139">Můžete pouze vynásobit 1.0, použití dimenze pro rozhraní příkazového řádku 1.0.</span><span class="sxs-lookup"><span data-stu-id="92fab-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="92fab-140">Můžete to abstraktní do funkce, jako je `degreesFahrenheit`.</span><span class="sxs-lookup"><span data-stu-id="92fab-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="92fab-141">Navíc při předání dimenzované hodnoty do funkce, které očekávají. bezrozměrná čísel s plovoucí desetinnou musíte zrušit jednotky nebo přetypován na `float` pomocí `float` operátor.</span><span class="sxs-lookup"><span data-stu-id="92fab-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="92fab-142">V tomto příkladu budete dělit `1.0<degC>` pro argumenty, které mají `printf` protože `printf` očekává, že. bezrozměrná množství.</span><span class="sxs-lookup"><span data-stu-id="92fab-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="92fab-143">Následující příklad relace ukazuje vytvořené jako výstupy z a vstupy pro tento kód.</span><span class="sxs-lookup"><span data-stu-id="92fab-143">The following example session shows the outputs from and inputs to this code.</span></span>

```
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="92fab-144">Použití obecného jednotek</span><span class="sxs-lookup"><span data-stu-id="92fab-144">Using Generic Units</span></span>

<span data-ttu-id="92fab-145">Můžete napsat obecné funkce, které pracují s daty, která má související jednotka měření.</span><span class="sxs-lookup"><span data-stu-id="92fab-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="92fab-146">To provedete tak, že zadáte typ spolu s Obecné jednotky jako parametr typu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="92fab-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="92fab-147">Vytvoření agregované typy pomocí obecného jednotky</span><span class="sxs-lookup"><span data-stu-id="92fab-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="92fab-148">Následující kód ukazuje, jak vytvořit agregační typ, který se skládá z jednotlivých hodnot s plovoucí desetinnou, které mají jednotek, které jsou obecné.</span><span class="sxs-lookup"><span data-stu-id="92fab-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="92fab-149">To umožňuje jeden typ má být vytvořen, který spolupracuje s řadou jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="92fab-150">Obecné jednotky také zachovat bezpečnost typů tím, že zajišťuje, že je obecný typ, který má jednu sadu jednotky jiného typu než stejný obecný typ s jinou sadu jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="92fab-151">Základ této techniky je, že `Measure` atribut lze použít pro parametr typu.</span><span class="sxs-lookup"><span data-stu-id="92fab-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="92fab-152">Jednotky za běhu</span><span class="sxs-lookup"><span data-stu-id="92fab-152">Units at Runtime</span></span>

<span data-ttu-id="92fab-153">Měrné jednotky se používají pro kontrolu statického typu.</span><span class="sxs-lookup"><span data-stu-id="92fab-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="92fab-154">Po zkompilování hodnoty s plovoucí desetinnou měrné jednotky jsou odstraněny, tak, aby v době běhu byly ztraceny jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="92fab-155">Jakékoli pokusy o implementaci funkcí, které závisí na kontrolu za běhu jednotky proto není možné.</span><span class="sxs-lookup"><span data-stu-id="92fab-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="92fab-156">Příklad implementace `ToString` funkce, který vytiskne jednotky není možné.</span><span class="sxs-lookup"><span data-stu-id="92fab-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="92fab-157">Převody</span><span class="sxs-lookup"><span data-stu-id="92fab-157">Conversions</span></span>

<span data-ttu-id="92fab-158">Převést typ, který má jednotky (například `float<'u>`) na typ, který nemá jednotek, můžete použít funkci standardní převod.</span><span class="sxs-lookup"><span data-stu-id="92fab-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="92fab-159">Například můžete použít `float` pro převod na `float` hodnotu, která nemá žádné jednotky, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="92fab-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="92fab-160">Pro převedení unitless hodnoty na hodnotu, která má jednotky, můžete hodnotu 1 nebo 1.0, která je označena vynásobit se vhodné jednotky.</span><span class="sxs-lookup"><span data-stu-id="92fab-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="92fab-161">Pro psaní vrstvy vzájemná funkční spolupráce, existují však také některé explicitní funkce, které můžete použít k převodu unitless hodnot na hodnoty s jednotkami.</span><span class="sxs-lookup"><span data-stu-id="92fab-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="92fab-162">Toto jsou v [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) modulu.</span><span class="sxs-lookup"><span data-stu-id="92fab-162">These are in the [Microsoft.FSharp.Core.LanguagePrimitives](https://msdn.microsoft.com/library/69d08ac5-5d51-4c20-bf1e-850fd312ece3) module.</span></span> <span data-ttu-id="92fab-163">Například chcete převést unitless `float` k `float<cm>`, použijte [floatwithmeasure –](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="92fab-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://msdn.microsoft.com/library/69520bc7-d67b-46b8-9004-7cac9646b8d9), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="92fab-164">Měrné jednotky v knihovně F # Core</span><span class="sxs-lookup"><span data-stu-id="92fab-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="92fab-165">Je k dispozici v knihovně jednotky `FSharp.Data.UnitSystems.SI` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="92fab-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="92fab-166">V obou jejich symbol formulář obsahuje jednotek SI (podobně jako `m` pro měření) v `UnitSymbols` podřízeném oboru názvů a jejich úplný název (jako `meter` pro měření) v `UnitNames` podřízeném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="92fab-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="92fab-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92fab-167">See also</span></span>

- [<span data-ttu-id="92fab-168">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="92fab-168">F# Language Reference</span></span>](index.md)
