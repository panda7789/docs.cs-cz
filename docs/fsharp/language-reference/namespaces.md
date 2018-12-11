---
title: Obory názvů (F#)
description: Zjistěte, jak F# obor názvů umožňuje organizovat kód tím, že povolíte připojení názvu k seskupení prvků programu do oblasti související funkce.
ms.date: 12/08/2018
ms.openlocfilehash: ad5cca8947d09d8480bfa418b003c84546edc29b
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169019"
---
# <a name="namespaces"></a><span data-ttu-id="72b3a-103">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="72b3a-103">Namespaces</span></span>

<span data-ttu-id="72b3a-104">Obor názvů umožňuje uspořádat kódu do související funkční oblasti tím, že povolíte připojení názvu k seskupení F# prvky programu.</span><span class="sxs-lookup"><span data-stu-id="72b3a-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of F# program elements.</span></span> <span data-ttu-id="72b3a-105">Obory názvů jsou obvykle nejvyšší úrovně prvky F# soubory.</span><span class="sxs-lookup"><span data-stu-id="72b3a-105">Namespaces are typically top-level elements in F# files.</span></span>

## <a name="syntax"></a><span data-ttu-id="72b3a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72b3a-106">Syntax</span></span>

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="72b3a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72b3a-107">Remarks</span></span>

<span data-ttu-id="72b3a-108">Pokud chcete vložit kód v oboru názvů, je třeba deklarovat první deklarací v souboru obor názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="72b3a-109">Obsah pak celý soubor se stanou součástí obor názvů, pokud neexistuje žádné další deklarace oborů názvů dále v souboru.</span><span class="sxs-lookup"><span data-stu-id="72b3a-109">The contents of the entire file then become part of the namespace, provided no other namespaces declaration exists further in the file.</span></span> <span data-ttu-id="72b3a-110">Pokud je to tento případ, veškerý kód do další deklarace oboru názvů se považuje se během prvního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-110">If that is the case, then all code up until the next namespace declaration is considered to be within the first namespace.</span></span>

<span data-ttu-id="72b3a-111">Obory názvů nemůže přímo obsahovat hodnoty a funkce.</span><span class="sxs-lookup"><span data-stu-id="72b3a-111">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="72b3a-112">Namísto toho hodnoty a funkce musí být součástí moduly a moduly jsou zahrnuty v oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-112">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="72b3a-113">Obory názvů může obsahovat typy, moduly.</span><span class="sxs-lookup"><span data-stu-id="72b3a-113">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="72b3a-114">Komentáře XML mohou být deklarovány nad oboru názvů, ale jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="72b3a-114">XML doc comments can be declared above a namespace, but they're ignored.</span></span> <span data-ttu-id="72b3a-115">Direktivy kompilátoru lze také deklarovat nad oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-115">Compiler directives can also be declared above a namespace.</span></span>

<span data-ttu-id="72b3a-116">Obory názvů lze explicitně deklarovat pomocí klíčového slova oboru názvů nebo implicitně při deklaraci modulu.</span><span class="sxs-lookup"><span data-stu-id="72b3a-116">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="72b3a-117">Obor názvů explicitně deklarovat, použijte klíčové slovo oboru názvů, za nímž následuje název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-117">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="72b3a-118">Následující příklad ukazuje soubor kódu, který deklaruje oboru názvů `Widgets` s typem a modul zahrnuté v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-118">The following example shows a code file that declares a namespace `Widgets` with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="72b3a-119">Pokud celý obsah souboru do jednoho modulu, můžete také deklarovat obory názvů implicitně pomocí `module` – klíčové slovo a poskytnutí nového názvu oboru názvů v modulu plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="72b3a-119">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="72b3a-120">Následující příklad ukazuje soubor kódu, který deklaruje oboru názvů `Widgets` a modul `WidgetsModule`, který obsahuje funkci.</span><span class="sxs-lookup"><span data-stu-id="72b3a-120">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="72b3a-121">Následující kód je ekvivalentní předchozí kód, ale modul je místní modul deklarace.</span><span class="sxs-lookup"><span data-stu-id="72b3a-121">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="72b3a-122">V takovém případě obor názvů musí být na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="72b3a-122">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="72b3a-123">Pokud je to více než jeden modul je nutné ve stejném souboru v jedné nebo více oborů názvů, je nutné použít místní modul deklarace.</span><span class="sxs-lookup"><span data-stu-id="72b3a-123">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="72b3a-124">Když používáte místní modul deklarace, nelze použít kvalifikovaný obor názvů v deklaracích module.</span><span class="sxs-lookup"><span data-stu-id="72b3a-124">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="72b3a-125">Následující kód ukazuje soubor, který má deklarace oboru názvů a dvě deklarace místní modul.</span><span class="sxs-lookup"><span data-stu-id="72b3a-125">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="72b3a-126">V tomto případě jsou obsaženy moduly přímo v oboru názvů; neexistuje žádný implicitně vytvořený modul, který má stejný název jako soubor.</span><span class="sxs-lookup"><span data-stu-id="72b3a-126">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="72b3a-127">Jakýkoli jiný kód v souboru, například `do` vazby, je v oboru názvů, ale ne v vnitřní moduly, takže je potřeba kvalifikovat člen modulu `widgetFunction` pomocí názvu modulu.</span><span class="sxs-lookup"><span data-stu-id="72b3a-127">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="72b3a-128">Výstup tohoto příkladu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="72b3a-128">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="72b3a-129">Další informace najdete v tématu [moduly](modules.md).</span><span class="sxs-lookup"><span data-stu-id="72b3a-129">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="72b3a-130">Vnořené obory názvů</span><span class="sxs-lookup"><span data-stu-id="72b3a-130">Nested Namespaces</span></span>

<span data-ttu-id="72b3a-131">Když vytvoříte vnořené oboru názvů, musíte ho plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="72b3a-131">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="72b3a-132">V opačném případě můžete vytvořit nový obor názvů nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="72b3a-132">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="72b3a-133">Odsazení je ignorován v deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-133">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="72b3a-134">Následující příklad ukazuje, jak deklarovat vnořené oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-134">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="72b3a-135">Obory názvů souborů a sestavení</span><span class="sxs-lookup"><span data-stu-id="72b3a-135">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="72b3a-136">Obory názvů může zahrnovat více souborů v jednom projektu nebo kompilace.</span><span class="sxs-lookup"><span data-stu-id="72b3a-136">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="72b3a-137">Termín *obor názvů fragment* popisuje část oboru názvů, který je zahrnutý v jednom souboru.</span><span class="sxs-lookup"><span data-stu-id="72b3a-137">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="72b3a-138">Obory názvů může zasahovat do více sestavení.</span><span class="sxs-lookup"><span data-stu-id="72b3a-138">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="72b3a-139">Například `System` obor názvů zahrnuje celý .NET Framework, která zahrnuje mnoho sestavení a obsahuje mnoho vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-139">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="72b3a-140">Globální Namespace</span><span class="sxs-lookup"><span data-stu-id="72b3a-140">Global Namespace</span></span>

<span data-ttu-id="72b3a-141">Použít oboru předdefinovanou `global` chcete změnit názvy na nejvyšší úrovni oboru názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="72b3a-141">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="72b3a-142">Můžete použít také globální k odkazu na nejvyšší úrovni obor názvů .NET, například, chcete-li vyřešit název je v konfliktu s další obory názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-142">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="72b3a-143">Rekurzivní obory názvů</span><span class="sxs-lookup"><span data-stu-id="72b3a-143">Recursive namespaces</span></span>

<span data-ttu-id="72b3a-144">Obory názvů lze také deklarovat jako rekurzivní povolit pro všechny obsažené kód je vzájemně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="72b3a-144">Namespaces can also be declared as recursive to allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="72b3a-145">To se provádí prostřednictvím `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="72b3a-145">This is done via `namespace rec`.</span></span> <span data-ttu-id="72b3a-146">Použití `namespace rec` může vyřešit některé důsledně v nebude moci napsat kód vzájemně referenční typy a moduly.</span><span class="sxs-lookup"><span data-stu-id="72b3a-146">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span> <span data-ttu-id="72b3a-147">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="72b3a-147">The following is an example of this:</span></span>

```fsharp
namespace rec MutualReferences

type Orientation = Up | Down
type PeelState = Peeled | Unpeeled

// This exception depends on the type below.
exception DontSqueezeTheBananaException of Banana

type BananaPeel() = class end

type Banana(orientation : Orientation) =
    member val IsPeeled = false with get, set
    member val Orientation = orientation with get, set
    member val Sides: PeelState list = [ Unpeeled; Unpeeled; Unpeeled; Unpeeled] with get, set

    member self.Peel() = BananaHelpers.peel self // Note the dependency on the BananaHelpers module.
    member self.SqueezeJuiceOut() = raise (DontSqueezeTheBananaException self) // This member depends on the exception above.

module BananaHelpers =
    let peel (b: Banana) =
        let flip (banana: Banana) =
            match banana.Orientation with
            | Up -> 
                banana.Orientation <- Down
                banana
            | Down -> banana

        let peelSides (banana: Banana) =
            banana.Sides
            |> List.map (function
                         | Unpeeled -> Peeled
                         | Peeled -> Peeled)

        match b.Orientation with
        | Up ->   b |> flip |> peelSides
        | Down -> b |> peelSides
```

<span data-ttu-id="72b3a-148">Všimněte si, že výjimka `DontSqueezeTheBananaException` a třída `Banana` odkazují na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="72b3a-148">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="72b3a-149">Kromě toho modul `BananaHelpers` a třída `Banana` také odkazovat na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="72b3a-149">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span> <span data-ttu-id="72b3a-150">To by nebylo možné vyjádřit v F# Pokud jste odebrali `rec` – klíčové slovo z `MutualReferences` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="72b3a-150">This wouldn't be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="72b3a-151">Tato funkce je také k dispozici pro nejvyšší úrovně [moduly](modules.md).</span><span class="sxs-lookup"><span data-stu-id="72b3a-151">This feature is also available for top-level [Modules](modules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="72b3a-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72b3a-152">See also</span></span>

- [<span data-ttu-id="72b3a-153">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="72b3a-153">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="72b3a-154">Moduly</span><span class="sxs-lookup"><span data-stu-id="72b3a-154">Modules</span></span>](modules.md)
- [<span data-ttu-id="72b3a-155">F#RFC FS-1009 - povolit vzájemně referenční typy a moduly přes větší oborů v rámci souborů</span><span class="sxs-lookup"><span data-stu-id="72b3a-155">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
