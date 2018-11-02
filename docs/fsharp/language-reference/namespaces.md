---
title: Obory názvů (F#)
description: 'Zjistěte, jak obor názvů F # umožňuje organizovat kód tím, že povolíte připojení názvu k seskupení prvků programu do oblasti související funkce.'
ms.date: 04/24/2017
ms.openlocfilehash: 769a1241f76ac32d3a6a80bd637078493119bb3c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44178249"
---
# <a name="namespaces"></a><span data-ttu-id="8762e-103">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="8762e-103">Namespaces</span></span>

<span data-ttu-id="8762e-104">Obor názvů umožňuje uspořádat kódu do související funkční oblasti tím, že jste se připojit k seskupení prvků programu název.</span><span class="sxs-lookup"><span data-stu-id="8762e-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of program elements.</span></span>

## <a name="syntax"></a><span data-ttu-id="8762e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8762e-105">Syntax</span></span>

```fsharp
namespace [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="8762e-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8762e-106">Remarks</span></span>

<span data-ttu-id="8762e-107">Pokud chcete vložit kód v oboru názvů, je třeba deklarovat první deklarací v souboru obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-107">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="8762e-108">Obsah celého souboru pak mohou stát součástí oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-108">The contents of the entire file then become part of the namespace.</span></span>

<span data-ttu-id="8762e-109">Obory názvů nemůže přímo obsahovat hodnoty a funkce.</span><span class="sxs-lookup"><span data-stu-id="8762e-109">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="8762e-110">Namísto toho hodnoty a funkce musí být součástí moduly a moduly jsou zahrnuty v oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-110">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="8762e-111">Obory názvů může obsahovat typy, moduly.</span><span class="sxs-lookup"><span data-stu-id="8762e-111">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="8762e-112">Obory názvů lze explicitně deklarovat pomocí klíčového slova oboru názvů nebo implicitně při deklaraci modulu.</span><span class="sxs-lookup"><span data-stu-id="8762e-112">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="8762e-113">Obor názvů explicitně deklarovat, použijte klíčové slovo oboru názvů, za nímž následuje název oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-113">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="8762e-114">Následující příklad ukazuje soubor kódu, který deklaruje pomůcky oboru názvů s typem a modul zahrnuté v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-114">The following example shows a code file that declares a namespace Widgets with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="8762e-115">Pokud celý obsah souboru do jednoho modulu, můžete také deklarovat obory názvů implicitně pomocí `module` – klíčové slovo a poskytnutí nového názvu oboru názvů v modulu plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="8762e-115">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="8762e-116">Následující příklad ukazuje soubor kódu, který deklaruje oboru názvů `Widgets` a modul `WidgetsModule`, který obsahuje funkci.</span><span class="sxs-lookup"><span data-stu-id="8762e-116">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="8762e-117">Následující kód je ekvivalentní předchozí kód, ale modul je místní modul deklarace.</span><span class="sxs-lookup"><span data-stu-id="8762e-117">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="8762e-118">V takovém případě obor názvů musí být na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="8762e-118">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="8762e-119">Pokud je to více než jeden modul je nutné ve stejném souboru v jedné nebo více oborů názvů, je nutné použít místní modul deklarace.</span><span class="sxs-lookup"><span data-stu-id="8762e-119">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="8762e-120">Když používáte místní modul deklarace, nelze použít kvalifikovaný obor názvů v deklaracích module.</span><span class="sxs-lookup"><span data-stu-id="8762e-120">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="8762e-121">Následující kód ukazuje soubor, který má deklarace oboru názvů a dvě deklarace místní modul.</span><span class="sxs-lookup"><span data-stu-id="8762e-121">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="8762e-122">V tomto případě jsou obsaženy moduly přímo v oboru názvů; neexistuje žádný implicitně vytvořený modul, který má stejný název jako soubor.</span><span class="sxs-lookup"><span data-stu-id="8762e-122">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="8762e-123">Jakýkoli jiný kód v souboru, například `do` vazby, je v oboru názvů, ale ne v vnitřní moduly, takže je potřeba kvalifikovat člen modulu `widgetFunction` pomocí názvu modulu.</span><span class="sxs-lookup"><span data-stu-id="8762e-123">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="8762e-124">Výstup tohoto příkladu vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="8762e-124">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="8762e-125">Další informace najdete v tématu [moduly](modules.md).</span><span class="sxs-lookup"><span data-stu-id="8762e-125">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="8762e-126">Vnořené obory názvů</span><span class="sxs-lookup"><span data-stu-id="8762e-126">Nested Namespaces</span></span>

<span data-ttu-id="8762e-127">Když vytvoříte vnořené oboru názvů, musíte ho plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="8762e-127">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="8762e-128">V opačném případě můžete vytvořit nový obor názvů nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="8762e-128">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="8762e-129">Odsazení je ignorován v deklarace oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-129">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="8762e-130">Následující příklad ukazuje, jak deklarovat vnořené oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-130">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="8762e-131">Obory názvů souborů a sestavení</span><span class="sxs-lookup"><span data-stu-id="8762e-131">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="8762e-132">Obory názvů může zahrnovat více souborů v jednom projektu nebo kompilace.</span><span class="sxs-lookup"><span data-stu-id="8762e-132">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="8762e-133">Termín *obor názvů fragment* popisuje část oboru názvů, který je zahrnutý v jednom souboru.</span><span class="sxs-lookup"><span data-stu-id="8762e-133">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="8762e-134">Obory názvů může zasahovat do více sestavení.</span><span class="sxs-lookup"><span data-stu-id="8762e-134">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="8762e-135">Například `System` obor názvů zahrnuje celý .NET Framework, která zahrnuje mnoho sestavení a obsahuje mnoho vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-135">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="8762e-136">Globální Namespace</span><span class="sxs-lookup"><span data-stu-id="8762e-136">Global Namespace</span></span>

<span data-ttu-id="8762e-137">Použít oboru předdefinovanou `global` chcete změnit názvy na nejvyšší úrovni oboru názvů .NET.</span><span class="sxs-lookup"><span data-stu-id="8762e-137">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="8762e-138">Můžete použít také globální k odkazu na nejvyšší úrovni obor názvů .NET, například, chcete-li vyřešit název je v konfliktu s další obory názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-138">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="8762e-139">Rekurzivní obory názvů</span><span class="sxs-lookup"><span data-stu-id="8762e-139">Recursive namespaces</span></span>

<span data-ttu-id="8762e-140">F # 4.1 zavádí pojem obory názvů, které umožňují všechny obsažené kód je vzájemně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="8762e-140">F# 4.1 introduces the notion of namespaces which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="8762e-141">To se provádí prostřednictvím `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="8762e-141">This is done via `namespace rec`.</span></span>  <span data-ttu-id="8762e-142">Použití `namespace rec` může vyřešit některé důsledně v nebude moci napsat kód vzájemně referenční typy a moduly.</span><span class="sxs-lookup"><span data-stu-id="8762e-142">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="8762e-143">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="8762e-143">The following is an example of this:</span></span>

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

<span data-ttu-id="8762e-144">Všimněte si, že výjimka `DontSqueezeTheBananaException` a třída `Banana` odkazují na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="8762e-144">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="8762e-145">Kromě toho modul `BananaHelpers` a třída `Banana` také odkazovat na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="8762e-145">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="8762e-146">To by nebylo možné vyjádřit v jazyce F #, pokud jste odebrali `rec` – klíčové slovo z `MutualReferences` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8762e-146">This would not be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="8762e-147">Tato funkce je také k dispozici pro nejvyšší úrovně [moduly](modules.md) v F # 4.1 nebo vyšší.</span><span class="sxs-lookup"><span data-stu-id="8762e-147">This feature is also available for top-level [Modules](modules.md) in F# 4.1 or higher.</span></span>

## <a name="see-also"></a><span data-ttu-id="8762e-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8762e-148">See also</span></span>

- [<span data-ttu-id="8762e-149">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="8762e-149">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8762e-150">Moduly</span><span class="sxs-lookup"><span data-stu-id="8762e-150">Modules</span></span>](modules.md)
- [<span data-ttu-id="8762e-151">1009-F # RFC FS - povolit vzájemně referenční typy a moduly přes větší oborů v rámci souborů</span><span class="sxs-lookup"><span data-stu-id="8762e-151">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
