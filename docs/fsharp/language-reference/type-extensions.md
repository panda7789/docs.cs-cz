---
title: Rozšíření typů
description: 'Přečtěte si, jak rozšíření typu F # umožňují přidávat nové členy do dříve definovaného typu objektu.'
ms.date: 02/05/2020
ms.openlocfilehash: 8fdb2d5e527643b23d24a6118e8cef6b11f1a546
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559125"
---
# <a name="type-extensions"></a><span data-ttu-id="793a0-103">Rozšíření typů</span><span class="sxs-lookup"><span data-stu-id="793a0-103">Type extensions</span></span>

<span data-ttu-id="793a0-104">Přípony typů (označované také jako _rozšíření) představují_řadu funkcí, které umožňují přidat nové členy do dříve definovaného typu objektu.</span><span class="sxs-lookup"><span data-stu-id="793a0-104">Type extensions (also called _augmentations_) are a family of features that let you add new members to a previously defined object type.</span></span> <span data-ttu-id="793a0-105">K třem funkcím patří:</span><span class="sxs-lookup"><span data-stu-id="793a0-105">The three features are:</span></span>

- <span data-ttu-id="793a0-106">Rozšíření vnitřních typů</span><span class="sxs-lookup"><span data-stu-id="793a0-106">Intrinsic type extensions</span></span>
- <span data-ttu-id="793a0-107">Volitelná rozšíření typu</span><span class="sxs-lookup"><span data-stu-id="793a0-107">Optional type extensions</span></span>
- <span data-ttu-id="793a0-108">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="793a0-108">Extension methods</span></span>

<span data-ttu-id="793a0-109">Každý lze použít v různých scénářích a má různé kompromisy.</span><span class="sxs-lookup"><span data-stu-id="793a0-109">Each can be used in different scenarios and has different tradeoffs.</span></span>

## <a name="syntax"></a><span data-ttu-id="793a0-110">Syntax</span><span class="sxs-lookup"><span data-stu-id="793a0-110">Syntax</span></span>

```fsharp
// Intrinsic and optional extensions
type typename with
    member self-identifier.member-name =
        body
    ...

// Extension methods
open System.Runtime.CompilerServices

[<Extension>]
type Extensions() =
    [<Extension>]
    static member self-identifier.extension-name (ty: typename, [args]) =
        body
    ...
```

## <a name="intrinsic-type-extensions"></a><span data-ttu-id="793a0-111">Rozšíření vnitřních typů</span><span class="sxs-lookup"><span data-stu-id="793a0-111">Intrinsic type extensions</span></span>

<span data-ttu-id="793a0-112">Rozšíření vnitřního typu je rozšíření typu, které rozšiřuje uživatelsky definovaný typ.</span><span class="sxs-lookup"><span data-stu-id="793a0-112">An intrinsic type extension is a type extension that extends a user-defined type.</span></span>

<span data-ttu-id="793a0-113">Rozšíření vnitřních typů musí být definována ve stejném souboru **a** ve stejném oboru názvů nebo modulu jako typ, který rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="793a0-113">Intrinsic type extensions must be defined in the same file **and** in the same namespace or module as the type they're extending.</span></span> <span data-ttu-id="793a0-114">Všechny ostatní definice budou mít za následek [volitelná rozšíření typu](type-extensions.md#optional-type-extensions).</span><span class="sxs-lookup"><span data-stu-id="793a0-114">Any other definition will result in them being [optional type extensions](type-extensions.md#optional-type-extensions).</span></span>

<span data-ttu-id="793a0-115">Rozšíření vnitřních typů jsou někdy čisticím způsobem, jak oddělit funkce od deklarace typu.</span><span class="sxs-lookup"><span data-stu-id="793a0-115">Intrinsic type extensions are sometimes a cleaner way to separate functionality from the type declaration.</span></span> <span data-ttu-id="793a0-116">Následující příklad ukazuje, jak definovat rozšíření vnitřního typu:</span><span class="sxs-lookup"><span data-stu-id="793a0-116">The following example shows how to define an intrinsic type extension:</span></span>

```fsharp
namespace Example

type Variant =
    | Num of int
    | Str of string
  
module Variant =
    let print v =
        match v with
        | Num n -> printf "Num %d" n
        | Str s -> printf "Str %s" s

// Add a member to Variant as an extension
type Variant with
    member x.Print() = Variant.print x
```

<span data-ttu-id="793a0-117">Použití rozšíření typu umožňuje oddělit jednotlivé z následujících možností:</span><span class="sxs-lookup"><span data-stu-id="793a0-117">Using a type extension allows you to separate each of the following:</span></span>

- <span data-ttu-id="793a0-118">Deklarace `Variant` typu</span><span class="sxs-lookup"><span data-stu-id="793a0-118">The declaration of a `Variant` type</span></span>
- <span data-ttu-id="793a0-119">Funkce pro tisk `Variant` třídy v závislosti na jejím "tvaru"</span><span class="sxs-lookup"><span data-stu-id="793a0-119">Functionality to print the `Variant` class depending on its "shape"</span></span>
- <span data-ttu-id="793a0-120">Způsob přístupu k funkcím tisku pomocí notace typu Object-Style `.`</span><span class="sxs-lookup"><span data-stu-id="793a0-120">A way to access the printing functionality with object-style `.`-notation</span></span>

<span data-ttu-id="793a0-121">Jedná se o alternativu k definování všeho jako člena v `Variant` .</span><span class="sxs-lookup"><span data-stu-id="793a0-121">This is an alternative to defining everything as a member on `Variant`.</span></span> <span data-ttu-id="793a0-122">I když se nejedná o nepodstatný lepší přístup, může to být v některých situacích čisticí reprezentace funkcí.</span><span class="sxs-lookup"><span data-stu-id="793a0-122">Although it is not an inherently better approach, it can be a cleaner representation of functionality in some situations.</span></span>

<span data-ttu-id="793a0-123">Rozšíření vnitřních typů jsou kompilována jako členové typu, které rozšiřují, a jsou uvedeny u typu, když je typ zkontrolován pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="793a0-123">Intrinsic type extensions are compiled as members of the type they augment, and appear on the type when the type is examined by reflection.</span></span>

## <a name="optional-type-extensions"></a><span data-ttu-id="793a0-124">Volitelná rozšíření typu</span><span class="sxs-lookup"><span data-stu-id="793a0-124">Optional type extensions</span></span>

<span data-ttu-id="793a0-125">Volitelné rozšíření typu je rozšíření, které se zobrazí mimo původní modul, obor názvů nebo sestavení typu, který se rozšiřuje.</span><span class="sxs-lookup"><span data-stu-id="793a0-125">An optional type extension is an extension that appears outside the original module, namespace, or assembly of the type being extended.</span></span>

<span data-ttu-id="793a0-126">Volitelná rozšíření typu jsou užitečná pro rozšíření typu, který jste nedefinovali sami.</span><span class="sxs-lookup"><span data-stu-id="793a0-126">Optional type extensions are useful for extending a type that you have not defined yourself.</span></span> <span data-ttu-id="793a0-127">Příklad:</span><span class="sxs-lookup"><span data-stu-id="793a0-127">For example:</span></span>

```fsharp
module Extensions

type IEnumerable<'T> with
    /// Repeat each element of the sequence n times
    member xs.RepeatElements(n: int) =
        seq {
            for x in xs do
                for _ in 1 .. n -> x
        }
```

<span data-ttu-id="793a0-128">Nyní máte přístup `RepeatElements` , jako by byl členem, <xref:System.Collections.Generic.IEnumerable%601> dokud `Extensions` je modul otevřen v oboru, ve kterém pracujete.</span><span class="sxs-lookup"><span data-stu-id="793a0-128">You can now access `RepeatElements` as if it's a member of <xref:System.Collections.Generic.IEnumerable%601> as long as the `Extensions` module is opened in the scope that you are working in.</span></span>

<span data-ttu-id="793a0-129">Volitelná rozšíření se v rozšířeném typu nezobrazují, pokud jsou zkontrolovány pomocí reflexe.</span><span class="sxs-lookup"><span data-stu-id="793a0-129">Optional extensions do not appear on the extended type when examined by reflection.</span></span> <span data-ttu-id="793a0-130">Volitelná rozšíření musí být v modulech a jsou pouze v oboru, pokud je modul, který obsahuje rozšíření, otevřen nebo jinak v oboru.</span><span class="sxs-lookup"><span data-stu-id="793a0-130">Optional extensions must be in modules, and they're only in scope when the module that contains the extension is open or is otherwise in scope.</span></span>

<span data-ttu-id="793a0-131">Volitelné členy rozšíření jsou zkompilovány do statických členů, pro které je instance objektu implicitně předána jako první parametr.</span><span class="sxs-lookup"><span data-stu-id="793a0-131">Optional extension members are compiled to static members for which the object instance is passed implicitly as the first parameter.</span></span> <span data-ttu-id="793a0-132">Fungují však jako v případě, že se jedná o členy instance nebo statické členy podle toho, jak jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="793a0-132">However, they act as if they're instance members or static members according to how they're declared.</span></span>

<span data-ttu-id="793a0-133">Volitelné členy rozšíření nejsou také viditelné pro zákazníky v jazyce C# nebo Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="793a0-133">Optional extension members are also not visible to C# or Visual Basic consumers.</span></span> <span data-ttu-id="793a0-134">Můžou být spotřebované jenom v jiném kódu F #.</span><span class="sxs-lookup"><span data-stu-id="793a0-134">They can only be consumed in other F# code.</span></span>

## <a name="generic-limitation-of-intrinsic-and-optional-type-extensions"></a><span data-ttu-id="793a0-135">Obecné omezení vnitřních a volitelných rozšíření typu</span><span class="sxs-lookup"><span data-stu-id="793a0-135">Generic limitation of intrinsic and optional type extensions</span></span>

<span data-ttu-id="793a0-136">Je možné deklarovat rozšíření typu u obecného typu, kde je proměnná typu omezená.</span><span class="sxs-lookup"><span data-stu-id="793a0-136">It's possible to declare a type extension on a generic type where the type variable is constrained.</span></span> <span data-ttu-id="793a0-137">Požadavek znamená, že omezení deklarace rozšíření odpovídá omezení deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="793a0-137">The requirement is that the constraint of the extension declaration matches the constraint of the declared type.</span></span>

<span data-ttu-id="793a0-138">Nicméně i v případě, že se omezení shodují mezi deklarovaným typem a rozšířením typu, je možné, že je omezení odvozeno v těle rozšířeného člena, který ukládá jiný požadavek na parametr typu než deklarovaný typ.</span><span class="sxs-lookup"><span data-stu-id="793a0-138">However, even when constraints are matched between a declared type and a type extension, it's possible for a constraint to be inferred by the body of an extended member that imposes a different requirement on the type parameter than the declared type.</span></span> <span data-ttu-id="793a0-139">Příklad:</span><span class="sxs-lookup"><span data-stu-id="793a0-139">For example:</span></span>

```fsharp
open System.Collections.Generic

// NOT POSSIBLE AND FAILS TO COMPILE!
//
// The member 'Sum' has a different requirement on 'T than the type IEnumerable<'T>
type IEnumerable<'T> with
    member this.Sum() = Seq.sum this
```

<span data-ttu-id="793a0-140">Neexistuje žádný způsob, jak tento kód získat pro práci s volitelným rozšířením typu:</span><span class="sxs-lookup"><span data-stu-id="793a0-140">There is no way to get this code to work with an optional type extension:</span></span>

- <span data-ttu-id="793a0-141">Jak je, `Sum` má člen jiné omezení na `'T` ( `static member get_Zero` a), `static member (+)` než určuje přípona typu.</span><span class="sxs-lookup"><span data-stu-id="793a0-141">As is, the `Sum` member has a different constraint on `'T` (`static member get_Zero` and `static member (+)`) than what the type extension defines.</span></span>
- <span data-ttu-id="793a0-142">Změna rozšíření typu na má stejné omezení, jako by `Sum` se už neshodovalo s definovaným omezením `IEnumerable<'T>` .</span><span class="sxs-lookup"><span data-stu-id="793a0-142">Modifying the type extension to have the same constraint as `Sum` will no longer match the defined constraint on `IEnumerable<'T>`.</span></span>
- <span data-ttu-id="793a0-143">Když se změní `member this.Sum` na `member inline this.Sum` , dojde k chybě, že se neshodují omezení typu.</span><span class="sxs-lookup"><span data-stu-id="793a0-143">Changing `member this.Sum` to `member inline this.Sum` will give an error that type constraints are mismatched.</span></span>

<span data-ttu-id="793a0-144">Co je žádoucí, jsou statické metody, které jsou "float in Space" a mohou být prezentovány, jako kdyby rozšíří typ.</span><span class="sxs-lookup"><span data-stu-id="793a0-144">What is desired are static methods that "float in space" and can be presented as if they're extending a type.</span></span> <span data-ttu-id="793a0-145">Tady jsou metody rozšíření, které jsou nezbytné.</span><span class="sxs-lookup"><span data-stu-id="793a0-145">This is where extension methods become necessary.</span></span>

## <a name="extension-methods"></a><span data-ttu-id="793a0-146">Metody rozšíření</span><span class="sxs-lookup"><span data-stu-id="793a0-146">Extension methods</span></span>

<span data-ttu-id="793a0-147">Nakonec metody rozšíření (někdy označované jako "členy rozšíření stylu C#") lze deklarovat v jazyce F # jako statickou členskou metodu pro třídu.</span><span class="sxs-lookup"><span data-stu-id="793a0-147">Finally, extension methods (sometimes called "C# style extension members") can be declared in F# as a static member method on a class.</span></span>

<span data-ttu-id="793a0-148">Rozšiřující metody jsou užitečné, pokud chcete definovat rozšíření u obecného typu, který omezí proměnnou typu.</span><span class="sxs-lookup"><span data-stu-id="793a0-148">Extension methods are useful for when you wish to define extensions on a generic type that will constrain the type variable.</span></span> <span data-ttu-id="793a0-149">Příklad:</span><span class="sxs-lookup"><span data-stu-id="793a0-149">For example:</span></span>

```fsharp
namespace Extensions

open System.Collections.Generic
open System.Runtime.CompilerServices

[<Extension>]
type IEnumerableExtensions =
    [<Extension>]
    static member inline Sum(xs: IEnumerable<'T>) = Seq.sum xs
```

<span data-ttu-id="793a0-150">Při použití tohoto kódu se tento kód zobrazí, jako by byl `Sum` definován v <xref:System.Collections.Generic.IEnumerable%601> , pokud byl `Extensions` otevřen nebo je v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="793a0-150">When used, this code will make it appear as if `Sum` is defined on <xref:System.Collections.Generic.IEnumerable%601>, so long as `Extensions` has been opened or is in scope.</span></span>

<span data-ttu-id="793a0-151">Aby bylo rozšíření k dispozici pro VB.NET kód, `ExtensionAttribute` je na úrovni sestavení vyžadován extra.</span><span class="sxs-lookup"><span data-stu-id="793a0-151">For the extension to be available to VB.NET code, an extra `ExtensionAttribute` is required at the assembly level:</span></span>

```fsharp
module AssemblyInfo
open System.Runtime.CompilerServices
[<assembly:Extension>]
do ()
```

## <a name="other-remarks"></a><span data-ttu-id="793a0-152">Další poznámky</span><span class="sxs-lookup"><span data-stu-id="793a0-152">Other remarks</span></span>

<span data-ttu-id="793a0-153">Přípony typů mají také následující atributy:</span><span class="sxs-lookup"><span data-stu-id="793a0-153">Type extensions also have the following attributes:</span></span>

- <span data-ttu-id="793a0-154">Libovolný typ, který lze použít, lze rozšířit.</span><span class="sxs-lookup"><span data-stu-id="793a0-154">Any type that can be accessed can be extended.</span></span>
- <span data-ttu-id="793a0-155">Vnitřní a volitelné rozšíření typu mohou definovat _libovolný_ typ člena, nikoli pouze metody.</span><span class="sxs-lookup"><span data-stu-id="793a0-155">Intrinsic and optional type extensions can define _any_ member type, not just methods.</span></span> <span data-ttu-id="793a0-156">Vlastnosti rozšíření jsou také možné, například.</span><span class="sxs-lookup"><span data-stu-id="793a0-156">So extension properties are also possible, for example.</span></span>
- <span data-ttu-id="793a0-157">`self-identifier`Token v [syntaxi](type-extensions.md#syntax) představuje instanci volaného typu, stejně jako běžné členy.</span><span class="sxs-lookup"><span data-stu-id="793a0-157">The `self-identifier` token in the [syntax](type-extensions.md#syntax) represents the instance of the type being invoked, just like ordinary members.</span></span>
- <span data-ttu-id="793a0-158">Rozšířené členy mohou být statické nebo členy instance.</span><span class="sxs-lookup"><span data-stu-id="793a0-158">Extended members can be static or instance members.</span></span>
- <span data-ttu-id="793a0-159">Proměnné typu v rozšíření typu se musí shodovat s omezeními deklarovaného typu.</span><span class="sxs-lookup"><span data-stu-id="793a0-159">Type variables on a type extension must match the constraints of the declared type.</span></span>

<span data-ttu-id="793a0-160">Pro přípony typů existují taky tato omezení:</span><span class="sxs-lookup"><span data-stu-id="793a0-160">The following limitations also exist for type extensions:</span></span>

- <span data-ttu-id="793a0-161">Rozšíření typu nepodporují virtuální ani abstraktní metody.</span><span class="sxs-lookup"><span data-stu-id="793a0-161">Type extensions do not support virtual or abstract methods.</span></span>
- <span data-ttu-id="793a0-162">Rozšíření typu nepodporují metody přepisu jako rozšíření.</span><span class="sxs-lookup"><span data-stu-id="793a0-162">Type extensions do not support override methods as augmentations.</span></span>
- <span data-ttu-id="793a0-163">Rozšíření typu nepodporují [staticky vyřešené parametry typu](./generics/statically-resolved-type-parameters.md).</span><span class="sxs-lookup"><span data-stu-id="793a0-163">Type extensions do not support [Statically Resolved Type Parameters](./generics/statically-resolved-type-parameters.md).</span></span>
- <span data-ttu-id="793a0-164">Volitelná rozšíření typu nepodporují konstruktory jako rozšíření.</span><span class="sxs-lookup"><span data-stu-id="793a0-164">Optional Type extensions do not support constructors as augmentations.</span></span>
- <span data-ttu-id="793a0-165">Pro [zkratky typu](type-abbreviations.md)nelze definovat rozšíření typu.</span><span class="sxs-lookup"><span data-stu-id="793a0-165">Type extensions cannot be defined on [type abbreviations](type-abbreviations.md).</span></span>
- <span data-ttu-id="793a0-166">Přípony typů nejsou platné pro `byref<'T>` (i když mohou být deklarovány).</span><span class="sxs-lookup"><span data-stu-id="793a0-166">Type extensions are not valid for `byref<'T>` (though they can be declared).</span></span>
- <span data-ttu-id="793a0-167">Přípony typů nejsou platné pro atributy (i když mohou být deklarovány).</span><span class="sxs-lookup"><span data-stu-id="793a0-167">Type extensions are not valid for attributes (though they can be declared).</span></span>
- <span data-ttu-id="793a0-168">Můžete definovat rozšíření, která přetěžují jiné metody se stejným názvem, ale Kompilátor F # dává přednost metodám bez rozšíření, pokud dojde k nejednoznačnému volání.</span><span class="sxs-lookup"><span data-stu-id="793a0-168">You can define extensions that overload other methods of the same name, but the F# compiler gives preference to non-extension methods if there is an ambiguous call.</span></span>

<span data-ttu-id="793a0-169">Nakonec, pokud existuje více rozšíření vnitřního typu pro jeden typ, všechny členy musí být jedinečné.</span><span class="sxs-lookup"><span data-stu-id="793a0-169">Finally, if multiple intrinsic type extensions exist for one type, all members must be unique.</span></span> <span data-ttu-id="793a0-170">Pro volitelná rozšíření typu můžou mít členové v různých typech rozšíření stejného typu stejné názvy.</span><span class="sxs-lookup"><span data-stu-id="793a0-170">For optional type extensions, members in different type extensions to the same type can have the same names.</span></span> <span data-ttu-id="793a0-171">K chybám nejednoznačnosti dochází pouze v případě, že klientský kód otevírá dva různé obory, které definují stejné názvy členů.</span><span class="sxs-lookup"><span data-stu-id="793a0-171">Ambiguity errors occur only if client code opens two different scopes that define the same member names.</span></span>

## <a name="see-also"></a><span data-ttu-id="793a0-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="793a0-172">See also</span></span>

- [<span data-ttu-id="793a0-173">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="793a0-173">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="793a0-174">Členové</span><span class="sxs-lookup"><span data-stu-id="793a0-174">Members</span></span>](./members/index.md)
