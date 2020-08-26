---
title: Měrné jednotky
description: 'Přečtěte si, jak plovoucí desetinná čárka a čísla se znaménkem v F # můžou mít přidružené měrné jednotky, které se obvykle používají k označení délky, objemu a hmotnosti.'
ms.date: 08/15/2020
ms.openlocfilehash: 0262f89e80697dd86161c93fe37381122972b56f
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811571"
---
# <a name="units-of-measure"></a><span data-ttu-id="4e08b-103">Měrné jednotky</span><span class="sxs-lookup"><span data-stu-id="4e08b-103">Units of Measure</span></span>

<span data-ttu-id="4e08b-104">Plovoucí desetinná čárka a čísla se znaménkem v F # můžou mít přidružené měrné jednotky, které se obvykle používají k označení délky, objemu, hmotnosti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="4e08b-104">Floating point and signed integer values in F# can have associated units of measure, which are typically used to indicate length, volume, mass, and so on.</span></span> <span data-ttu-id="4e08b-105">Pomocí množství s jednotkami povolíte kompilátoru, aby ověřil, že aritmetické relace mají správné jednotky, což pomáhá předejít chybám při programování.</span><span class="sxs-lookup"><span data-stu-id="4e08b-105">By using quantities with units, you enable the compiler to verify that arithmetic relationships have the correct units, which helps prevent programming errors.</span></span>

## <a name="syntax"></a><span data-ttu-id="4e08b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e08b-106">Syntax</span></span>

```fsharp
[<Measure>] type unit-name [ = measure ]
```

## <a name="remarks"></a><span data-ttu-id="4e08b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e08b-107">Remarks</span></span>

<span data-ttu-id="4e08b-108">Předchozí syntaxe definuje *jednotkový název* jako měrnou jednotku.</span><span class="sxs-lookup"><span data-stu-id="4e08b-108">The previous syntax defines *unit-name* as a unit of measure.</span></span> <span data-ttu-id="4e08b-109">Volitelná část se používá k definování nové míry z podmínek dříve definovaných jednotek.</span><span class="sxs-lookup"><span data-stu-id="4e08b-109">The optional part is used to define a new measure in terms of previously defined units.</span></span> <span data-ttu-id="4e08b-110">Například následující řádek definuje míru `cm` (centimetr).</span><span class="sxs-lookup"><span data-stu-id="4e08b-110">For example, the following line defines the measure `cm` (centimeter).</span></span>

```fsharp
[<Measure>] type cm
```

<span data-ttu-id="4e08b-111">Následující řádek definuje míru `ml` (milliliter) jako krychlové centimetr ( `cm^3` ).</span><span class="sxs-lookup"><span data-stu-id="4e08b-111">The following line defines the measure `ml` (milliliter) as a cubic centimeter (`cm^3`).</span></span>

```fsharp
[<Measure>] type ml = cm^3
```

<span data-ttu-id="4e08b-112">V předchozí syntaxi je *míra* vzorec, který zahrnuje jednotky.</span><span class="sxs-lookup"><span data-stu-id="4e08b-112">In the previous syntax, *measure* is a formula that involves units.</span></span> <span data-ttu-id="4e08b-113">Ve vzorcích, které zahrnují jednotky, jsou podporovány integrální pravomoci (kladné a záporné), mezery mezi jednotkami znamenají součin dvou jednotek, `*` také označuje součin jednotek a `/` označuje podíl jednotek.</span><span class="sxs-lookup"><span data-stu-id="4e08b-113">In formulas that involve units, integral powers are supported (positive and negative), spaces between units indicate a product of the two units, `*` also indicates a product of units, and `/` indicates a quotient of units.</span></span> <span data-ttu-id="4e08b-114">U reciproční jednotky můžete buď použít záporné celočíselné napájení, nebo `/` , které označuje oddělení a jmenovatel vzorec jednotky.</span><span class="sxs-lookup"><span data-stu-id="4e08b-114">For a reciprocal unit, you can either use a negative integer power or a `/` that indicates a separation between the numerator and denominator of a unit formula.</span></span> <span data-ttu-id="4e08b-115">Více jednotek ve jmenovateli musí být uzavřeny v závorkách.</span><span class="sxs-lookup"><span data-stu-id="4e08b-115">Multiple units in the denominator should be surrounded by parentheses.</span></span> <span data-ttu-id="4e08b-116">Jednotky oddělené mezerami po `/` interpretaci jsou interpretovány jako součást jmenovatele, ale jakékoli jednotky následující za `*` jsou interpretovány jako součást čitatele.</span><span class="sxs-lookup"><span data-stu-id="4e08b-116">Units separated by spaces after a `/` are interpreted as being part of the denominator, but any units following a `*` are interpreted as being part of the numerator.</span></span>

<span data-ttu-id="4e08b-117">Můžete použít 1 ve výrazech jednotek, buď samostatně k označení množství bez dimenze, nebo spolu s jinými jednotkami, jako je například v čitateli.</span><span class="sxs-lookup"><span data-stu-id="4e08b-117">You can use 1 in unit expressions, either alone to indicate a dimensionless quantity, or together with other units, such as in the numerator.</span></span> <span data-ttu-id="4e08b-118">Například jednotky pro sazbu by byly zapsány jako `1/s` , kde `s` označuje sekundy.</span><span class="sxs-lookup"><span data-stu-id="4e08b-118">For example, the units for a rate would be written as `1/s`, where `s` indicates seconds.</span></span> <span data-ttu-id="4e08b-119">Ve vzorcích jednotek se nepoužívají kulaté závorky.</span><span class="sxs-lookup"><span data-stu-id="4e08b-119">Parentheses are not used in unit formulas.</span></span> <span data-ttu-id="4e08b-120">Ve vzorcích jednotek neurčíte číselné konstanty převodu. Můžete však definovat konstanty převodu s jednotkami samostatně a použít je v výpočtech kontrolovaných jednotkou.</span><span class="sxs-lookup"><span data-stu-id="4e08b-120">You do not specify numeric conversion constants in the unit formulas; however, you can define conversion constants with units separately and use them in unit-checked computations.</span></span>

<span data-ttu-id="4e08b-121">Vzorce jednotek, které znamenají stejnou věc, mohou být napsány různými podobnými způsoby.</span><span class="sxs-lookup"><span data-stu-id="4e08b-121">Unit formulas that mean the same thing can be written in various equivalent ways.</span></span> <span data-ttu-id="4e08b-122">Kompilátor proto převede vzorce jednotek do konzistentního formátu, který převede záporné pravomoci na reciprocals, seskupí jednotky do jednoho čitatele a jmenovatele a alphabetizes jednotky v čitateli a jmenovateli.</span><span class="sxs-lookup"><span data-stu-id="4e08b-122">Therefore, the compiler converts unit formulas into a consistent form, which converts negative powers to reciprocals, groups units into a single numerator and a denominator, and alphabetizes the units in the numerator and denominator.</span></span>

<span data-ttu-id="4e08b-123">Například vzorce jednotek `kg m s^-2` a `m /s s * kg` jsou převedeny na `kg m/s^2` .</span><span class="sxs-lookup"><span data-stu-id="4e08b-123">For example, the unit formulas `kg m s^-2` and `m /s s * kg` are both converted to `kg m/s^2`.</span></span>

<span data-ttu-id="4e08b-124">Měrné jednotky se používají ve výrazech s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="4e08b-124">You use units of measure in floating point expressions.</span></span> <span data-ttu-id="4e08b-125">Použití čísel s plovoucí desetinnou čárkou spolu s přidruženými jednotkami míry přidává další úroveň zabezpečení typu a pomáhá vyhnout se chybám neshody jednotek, ke kterým může dojít ve vzorcích při použití slabého typu čísla s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="4e08b-125">Using floating point numbers together with associated units of measure adds another level of type safety and helps avoid the unit mismatch errors that can occur in formulas when you use weakly typed floating point numbers.</span></span> <span data-ttu-id="4e08b-126">Pokud napíšete výraz s plovoucí desetinnou čárkou, který používá jednotky, jednotky ve výrazu se musí shodovat.</span><span class="sxs-lookup"><span data-stu-id="4e08b-126">If you write a floating point expression that uses units, the units in the expression must match.</span></span>

<span data-ttu-id="4e08b-127">Literály můžete opatřit poznámkami pomocí vzorce jednotky v lomených závorkách, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="4e08b-127">You can annotate literals with a unit formula in angle brackets, as shown in the following examples.</span></span>

```fsharp
1.0<cm>
55.0<miles/hour>
```

<span data-ttu-id="4e08b-128">Mezi číslem a lomenou závorkou nelze vložit mezeru. Můžete však zahrnout příponu literálu `f` , například, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4e08b-128">You do not put a space between the number and the angle bracket; however, you can include a literal suffix such as `f`, as in the following example.</span></span>

```fsharp
// The f indicates single-precision floating point.
55.0f<miles/hour>
```

<span data-ttu-id="4e08b-129">Tato poznámka mění typ literálu z jeho primitivního typu (například `float` ) na typ dimenze, například `float<cm>` nebo, v tomto případě `float<miles/hour>` .</span><span class="sxs-lookup"><span data-stu-id="4e08b-129">Such an annotation changes the type of the literal from its primitive type (such as `float`) to a dimensioned type, such as `float<cm>` or, in this case, `float<miles/hour>`.</span></span> <span data-ttu-id="4e08b-130">Jednotka anotace `<1>` indikuje množství bez dimenzí a její typ je ekvivalentní primitivnímu typu bez parametr jednotky.</span><span class="sxs-lookup"><span data-stu-id="4e08b-130">A unit annotation of `<1>` indicates a dimensionless quantity, and its type is equivalent to the primitive type without a unit parameter.</span></span>

<span data-ttu-id="4e08b-131">Typ měrné jednotky je plovoucí desetinná čárka nebo podepsaný integrální typ společně s poznámkou jednotky navíc, která je uvedena v závorkách.</span><span class="sxs-lookup"><span data-stu-id="4e08b-131">The type of a unit of measure is a floating point or signed integral type together with an extra unit annotation, indicated in brackets.</span></span> <span data-ttu-id="4e08b-132">Proto při psaní typu převodu z `g` (gramů) na `kg` (kilogramy), popíšete typy následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="4e08b-132">Thus, when you write the type of a conversion from `g` (grams) to `kg` (kilograms), you describe the types as follows.</span></span>

```fsharp
let convertg2kg (x : float<g>) = x / 1000.0<g/kg>
```

<span data-ttu-id="4e08b-133">Měrné jednotky se používají pro kontrolu jednotky při kompilaci, ale v běhovém prostředí nejsou trvalé.</span><span class="sxs-lookup"><span data-stu-id="4e08b-133">Units of measure are used for compile-time unit checking but are not persisted in the run-time environment.</span></span> <span data-ttu-id="4e08b-134">Proto nemají vliv na výkon.</span><span class="sxs-lookup"><span data-stu-id="4e08b-134">Therefore, they do not affect performance.</span></span>

<span data-ttu-id="4e08b-135">Měrné jednotky lze použít na jakýkoli typ, nikoli pouze na typy s plovoucí desetinnou čárkou. pouze typy s plovoucí desetinnou čárkou, podepsané celočíselné typy a typy Decimal podporují dimenze množství.</span><span class="sxs-lookup"><span data-stu-id="4e08b-135">Units of measure can be applied to any type, not just floating point types; however, only floating point types, signed integral types, and decimal types support dimensioned quantities.</span></span> <span data-ttu-id="4e08b-136">Proto má smysl použít měrné jednotky u primitivních typů a agregací, které obsahují tyto primitivní typy.</span><span class="sxs-lookup"><span data-stu-id="4e08b-136">Therefore, it only makes sense to use units of measure on the primitive types and on aggregates that contain these primitive types.</span></span>

<span data-ttu-id="4e08b-137">Následující příklad znázorňuje použití měrných jednotek.</span><span class="sxs-lookup"><span data-stu-id="4e08b-137">The following example illustrates the use of units of measure.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6901.fs)]

<span data-ttu-id="4e08b-138">Následující příklad kódu ukazuje, jak převést hodnoty s plovoucí desetinnou čárkou na dimenze s hodnotou s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="4e08b-138">The following code example illustrates how to convert from a dimensionless floating point number to a dimensioned floating point value.</span></span> <span data-ttu-id="4e08b-139">Jenom vynásobte 1,0, aplikujete rozměry na 1,0.</span><span class="sxs-lookup"><span data-stu-id="4e08b-139">You just multiply by 1.0, applying the dimensions to the 1.0.</span></span> <span data-ttu-id="4e08b-140">Tuto možnost můžete zaabstraktit do funkce jako `degreesFahrenheit` .</span><span class="sxs-lookup"><span data-stu-id="4e08b-140">You can abstract this into a function like `degreesFahrenheit`.</span></span>

<span data-ttu-id="4e08b-141">Také při předání hodnot dimenzí funkcím, které očekávají bez dimenzí čísla s plovoucí desetinnou čárkou, je nutné zrušit jednotky nebo přetypovat na `float` pomocí `float` operátoru.</span><span class="sxs-lookup"><span data-stu-id="4e08b-141">Also, when you pass dimensioned values to functions that expect dimensionless floating point numbers, you must cancel out the units or cast to `float` by using the `float` operator.</span></span> <span data-ttu-id="4e08b-142">V tomto příkladu je rozdělen `1.0<degC>` argument pro argumenty, které mají za následek, že `printf` `printf` neočekáváte množství bez dimenzí.</span><span class="sxs-lookup"><span data-stu-id="4e08b-142">In this example, you divide by `1.0<degC>` for the arguments to `printf` because `printf` expects dimensionless quantities.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6902.fs)]

<span data-ttu-id="4e08b-143">Následující příklad relace zobrazuje výstupy a vstupy tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="4e08b-143">The following example session shows the outputs from and inputs to this code.</span></span>

```console
Enter a temperature in degrees Fahrenheit.
90
That temperature in degrees Celsius is    32.22.
```

## <a name="using-generic-units"></a><span data-ttu-id="4e08b-144">Použití obecných jednotek</span><span class="sxs-lookup"><span data-stu-id="4e08b-144">Using Generic Units</span></span>

<span data-ttu-id="4e08b-145">Můžete napsat obecné funkce, které pracují s daty, která mají přidruženou jednotku měření.</span><span class="sxs-lookup"><span data-stu-id="4e08b-145">You can write generic functions that operate on data that has an associated unit of measure.</span></span> <span data-ttu-id="4e08b-146">To provedete tak, že zadáte typ společně s obecnou jednotkou jako parametr typu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4e08b-146">You do this by specifying a type together with a generic unit as a type parameter, as shown in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6903.fs)]

## <a name="creating-aggregate-types-with-generic-units"></a><span data-ttu-id="4e08b-147">Vytváření agregovaných typů s obecnými jednotkami</span><span class="sxs-lookup"><span data-stu-id="4e08b-147">Creating Aggregate Types with Generic Units</span></span>

<span data-ttu-id="4e08b-148">Následující kód ukazuje, jak vytvořit agregovaný typ, který se skládá z jednotlivých hodnot s plovoucí desetinnou čárkou, které mají Obecné jednotky.</span><span class="sxs-lookup"><span data-stu-id="4e08b-148">The following code shows how to create an aggregate type that consists of individual floating point values that have units that are generic.</span></span> <span data-ttu-id="4e08b-149">To umožňuje vytvořit jeden typ, který pracuje s nejrůznějšími jednotkami.</span><span class="sxs-lookup"><span data-stu-id="4e08b-149">This enables a single type to be created that works with a variety of units.</span></span> <span data-ttu-id="4e08b-150">Obecné jednotky zachovávají bezpečnost typů také tím, že zajistí, že obecný typ, který má jednu sadu jednotek, je jiný typ než stejný obecný typ s jinou sadou jednotek.</span><span class="sxs-lookup"><span data-stu-id="4e08b-150">Also, generic units preserve type safety by ensuring that a generic type that has one set of units is a different type than the same generic type with a different set of units.</span></span> <span data-ttu-id="4e08b-151">Základem této techniky je, že `Measure` atribut lze použít na parametr typu.</span><span class="sxs-lookup"><span data-stu-id="4e08b-151">The basis of this technique is that the `Measure` attribute can be applied to the type parameter.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6904.fs)]

## <a name="units-at-runtime"></a><span data-ttu-id="4e08b-152">Jednotky za běhu</span><span class="sxs-lookup"><span data-stu-id="4e08b-152">Units at Runtime</span></span>

<span data-ttu-id="4e08b-153">Měrné jednotky se používají pro kontrolu statického typu.</span><span class="sxs-lookup"><span data-stu-id="4e08b-153">Units of measure are used for static type checking.</span></span> <span data-ttu-id="4e08b-154">Pokud jsou kompilovány hodnoty s plovoucí desetinnou čárkou, jsou jednotky míry eliminovány, takže jednotky budou za běhu ztraceny.</span><span class="sxs-lookup"><span data-stu-id="4e08b-154">When floating point values are compiled, the units of measure are eliminated, so the units are lost at run time.</span></span> <span data-ttu-id="4e08b-155">Proto není možné provádět jakékoli pokus o implementaci funkcí, které závisí na kontrole jednotek za běhu.</span><span class="sxs-lookup"><span data-stu-id="4e08b-155">Therefore, any attempt to implement functionality that depends on checking the units at run time is not possible.</span></span> <span data-ttu-id="4e08b-156">Například implementace `ToString` funkce pro tisk jednotek není možná.</span><span class="sxs-lookup"><span data-stu-id="4e08b-156">For example, implementing a `ToString` function to print out the units is not possible.</span></span>

## <a name="conversions"></a><span data-ttu-id="4e08b-157">Převody</span><span class="sxs-lookup"><span data-stu-id="4e08b-157">Conversions</span></span>

<span data-ttu-id="4e08b-158">Chcete-li převést typ, který obsahuje jednotky (například `float<'u>` ) na typ, který nemá jednotky, můžete použít funkci standardního převodu.</span><span class="sxs-lookup"><span data-stu-id="4e08b-158">To convert a type that has units (for example, `float<'u>`) to a type that does not have units, you can use the standard conversion function.</span></span> <span data-ttu-id="4e08b-159">Například můžete použít `float` k převodu na `float` hodnotu, která nemá jednotky, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e08b-159">For example, you can use `float` to convert to a `float` value that does not have units, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6905.fs)]

<span data-ttu-id="4e08b-160">Chcete-li převést jednotkovou hodnotu na hodnotu, která má jednotky, můžete vynásobit hodnotu 1 nebo 1,0, která je opatřena příslušnými jednotkami.</span><span class="sxs-lookup"><span data-stu-id="4e08b-160">To convert a unitless value to a value that has units, you can multiply by a 1 or 1.0 value that is annotated with the appropriate units.</span></span> <span data-ttu-id="4e08b-161">Pro psaní vrstev interoperability ale existují i některé explicitní funkce, které můžete použít k převodu hodnot bez jednotek na hodnoty s jednotkami.</span><span class="sxs-lookup"><span data-stu-id="4e08b-161">However, for writing interoperability layers, there are also some explicit functions that you can use to convert unitless values to values with units.</span></span> <span data-ttu-id="4e08b-162">Ty jsou v modulu [FSharp. Core. LanguagePrimitives](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) .</span><span class="sxs-lookup"><span data-stu-id="4e08b-162">These are in the [FSharp.Core.LanguagePrimitives](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html) module.</span></span> <span data-ttu-id="4e08b-163">Například pro převod z jednotky `float` bez jednotek na `float<cm>` , použijte [floatwithmeasure –](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure), jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="4e08b-163">For example, to convert from a unitless `float` to a `float<cm>`, use [FloatWithMeasure](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-languageprimitives.html#FloatWithMeasure), as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6906.fs)]

## <a name="units-of-measure-in-the-f-core-library"></a><span data-ttu-id="4e08b-164">Měrné jednotky v základní knihovně jazyka F #</span><span class="sxs-lookup"><span data-stu-id="4e08b-164">Units of Measure in the F# Core library</span></span>

<span data-ttu-id="4e08b-165">V oboru názvů je k dispozici knihovna jednotek `FSharp.Data.UnitSystems.SI` .</span><span class="sxs-lookup"><span data-stu-id="4e08b-165">A unit library is available in the `FSharp.Data.UnitSystems.SI` namespace.</span></span> <span data-ttu-id="4e08b-166">Obsahuje jednotky v obou svých symbolových formách (jako `m` měřič) v `UnitSymbols` suboboru názvů a jejich úplný název (jako `meter` měřič) v `UnitNames` oboru názvů sub.</span><span class="sxs-lookup"><span data-stu-id="4e08b-166">It includes SI units in both their symbol form (like `m` for meter) in the `UnitSymbols` sub-namespace, and their full name (like `meter` for meter) in the `UnitNames` sub-namespace.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e08b-167">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e08b-167">See also</span></span>

- [<span data-ttu-id="4e08b-168">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="4e08b-168">F# Language Reference</span></span>](index.md)
