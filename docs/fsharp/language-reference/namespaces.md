---
title: Jmenné prostory
description: Naučte se F# , jak obor názvů umožňuje organizovat kód do oblastí souvisejících funkcí tím, že umožňuje připojit název k seskupení prvků programu.
ms.date: 12/08/2018
ms.openlocfilehash: d295f25cae81bc28b4fcb522bdcacde862f9517a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627374"
---
# <a name="namespaces"></a><span data-ttu-id="f2275-103">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="f2275-103">Namespaces</span></span>

<span data-ttu-id="f2275-104">Obor názvů umožňuje organizovat kód do oblastí souvisejících funkcí tím, že umožňuje připojit název k seskupení prvků F# programu.</span><span class="sxs-lookup"><span data-stu-id="f2275-104">A namespace lets you organize code into areas of related functionality by enabling you to attach a name to a grouping of F# program elements.</span></span> <span data-ttu-id="f2275-105">Obory názvů jsou obvykle prvky nejvyšší úrovně F# v souborech.</span><span class="sxs-lookup"><span data-stu-id="f2275-105">Namespaces are typically top-level elements in F# files.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2275-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2275-106">Syntax</span></span>

```fsharp
namespace [rec] [parent-namespaces.]identifier
```

## <a name="remarks"></a><span data-ttu-id="f2275-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f2275-107">Remarks</span></span>

<span data-ttu-id="f2275-108">Pokud chcete vložit kód do oboru názvů, první deklarace v souboru musí deklarovat obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-108">If you want to put code in a namespace, the first declaration in the file must declare the namespace.</span></span> <span data-ttu-id="f2275-109">Obsah celého souboru se pak stane součástí oboru názvů, za předpokladu, že v souboru ještě neexistují žádné další deklarace oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-109">The contents of the entire file then become part of the namespace, provided no other namespaces declaration exists further in the file.</span></span> <span data-ttu-id="f2275-110">Pokud se jedná o tento případ, pak veškerý kód, dokud není další deklarace oboru názvů považována za v rámci prvního oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-110">If that is the case, then all code up until the next namespace declaration is considered to be within the first namespace.</span></span>

<span data-ttu-id="f2275-111">Obory názvů nemohou přímo obsahovat hodnoty a funkce.</span><span class="sxs-lookup"><span data-stu-id="f2275-111">Namespaces cannot directly contain values and functions.</span></span> <span data-ttu-id="f2275-112">Místo toho musí být hodnoty a funkce zahrnuté v modulech a moduly jsou zahrnuté v oborech názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-112">Instead, values and functions must be included in modules, and modules are included in namespaces.</span></span> <span data-ttu-id="f2275-113">Obory názvů mohou obsahovat typy, moduly.</span><span class="sxs-lookup"><span data-stu-id="f2275-113">Namespaces can contain types, modules.</span></span>

<span data-ttu-id="f2275-114">Komentáře XML mohou být deklarovány nad oborem názvů, ale jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="f2275-114">XML doc comments can be declared above a namespace, but they're ignored.</span></span> <span data-ttu-id="f2275-115">Direktivy kompilátoru mohou být také deklarovány nad oborem názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-115">Compiler directives can also be declared above a namespace.</span></span>

<span data-ttu-id="f2275-116">Obory názvů lze deklarovat explicitně s klíčovým slovem Namespace nebo implicitně při deklaraci modulu.</span><span class="sxs-lookup"><span data-stu-id="f2275-116">Namespaces can be declared explicitly with the namespace keyword, or implicitly when declaring a module.</span></span> <span data-ttu-id="f2275-117">K deklaraci oboru názvů explicitně použijte klíčové slovo Namespace následovaný názvem oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-117">To declare a namespace explicitly, use the namespace keyword followed by the namespace name.</span></span> <span data-ttu-id="f2275-118">Následující příklad ukazuje soubor kódu, který deklaruje obor názvů `Widgets` s typem a modul obsažený v tomto oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-118">The following example shows a code file that declares a namespace `Widgets` with a type and a module included in that namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6406.fs)]

<span data-ttu-id="f2275-119">Pokud je celý obsah souboru v jednom modulu, můžete také deklarovat obory názvů implicitně pomocí `module` klíčového slova a zadáním nového názvu oboru názvů v plně kvalifikovaném názvu modulu.</span><span class="sxs-lookup"><span data-stu-id="f2275-119">If the entire contents of the file are in one module, you can also declare namespaces implicitly by using the `module` keyword and providing the new namespace name in the fully qualified module name.</span></span> <span data-ttu-id="f2275-120">Následující příklad ukazuje soubor kódu, který deklaruje obor názvů `Widgets` a modul `WidgetsModule`, který obsahuje funkci.</span><span class="sxs-lookup"><span data-stu-id="f2275-120">The following example shows a code file that declares a namespace `Widgets` and a module `WidgetsModule`, which contains a function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6401.fs)]

<span data-ttu-id="f2275-121">Následující kód je ekvivalentní předchozímu kódu, ale modul je místní deklarace modulu.</span><span class="sxs-lookup"><span data-stu-id="f2275-121">The following code is equivalent to the preceding code, but the module is a local module declaration.</span></span> <span data-ttu-id="f2275-122">V takovém případě se obor názvů musí zobrazit na samostatném řádku.</span><span class="sxs-lookup"><span data-stu-id="f2275-122">In that case, the namespace must appear on its own line.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/namespaces/snippet6402.fs)]

<span data-ttu-id="f2275-123">Pokud je ve stejném souboru v jednom nebo více oborech názvů více než jeden modul, je nutné použít deklarace místních modulů.</span><span class="sxs-lookup"><span data-stu-id="f2275-123">If more than one module is required in the same file in one or more namespaces, you must use local module declarations.</span></span> <span data-ttu-id="f2275-124">Pokud používáte deklarace místních modulů, nemůžete použít kvalifikovaný obor názvů v deklaracích modulů.</span><span class="sxs-lookup"><span data-stu-id="f2275-124">When you use local module declarations, you cannot use the qualified namespace in the module declarations.</span></span> <span data-ttu-id="f2275-125">Následující kód ukazuje soubor, který má deklaraci oboru názvů a dvě deklarace místních modulů.</span><span class="sxs-lookup"><span data-stu-id="f2275-125">The following code shows a file that has a namespace declaration and two local module declarations.</span></span> <span data-ttu-id="f2275-126">V tomto případě jsou moduly obsaženy přímo v oboru názvů; neexistuje žádný implicitně vytvořený modul, který má stejný název jako soubor.</span><span class="sxs-lookup"><span data-stu-id="f2275-126">In this case, the modules are contained directly in the namespace; there is no implicitly created module that has the same name as the file.</span></span> <span data-ttu-id="f2275-127">Jakýkoli jiný kód v souboru, jako `do` je například vazba, je v oboru názvů, ale ne ve vnitřních modulech, takže je nutné kvalifikovat člen `widgetFunction` modulu pomocí názvu modulu.</span><span class="sxs-lookup"><span data-stu-id="f2275-127">Any other code in the file, such as a `do` binding, is in the namespace but not in the inner modules, so you need to qualify the module member `widgetFunction` by using the module name.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6403.fs)]

<span data-ttu-id="f2275-128">Výstup tohoto příkladu je následující.</span><span class="sxs-lookup"><span data-stu-id="f2275-128">The output of this example is as follows.</span></span>

```fsharp
Module1 10 20
Module2 5 6
```

<span data-ttu-id="f2275-129">Další informace najdete v tématu [moduly](modules.md).</span><span class="sxs-lookup"><span data-stu-id="f2275-129">For more information, see [Modules](modules.md).</span></span>

## <a name="nested-namespaces"></a><span data-ttu-id="f2275-130">Vnořené obory názvů</span><span class="sxs-lookup"><span data-stu-id="f2275-130">Nested Namespaces</span></span>

<span data-ttu-id="f2275-131">Když vytvoříte vnořený obor názvů, musíte ho plně kvalifikovat.</span><span class="sxs-lookup"><span data-stu-id="f2275-131">When you create a nested namespace, you must fully qualify it.</span></span> <span data-ttu-id="f2275-132">V opačném případě vytvoříte nový obor názvů nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="f2275-132">Otherwise, you create a new top-level namespace.</span></span> <span data-ttu-id="f2275-133">Odsazení se v deklaracích oboru názvů ignoruje.</span><span class="sxs-lookup"><span data-stu-id="f2275-133">Indentation is ignored in namespace declarations.</span></span>

<span data-ttu-id="f2275-134">Následující příklad ukazuje, jak deklarovat vnořený obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-134">The following example shows how to declare a nested namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6404.fs)]

## <a name="namespaces-in-files-and-assemblies"></a><span data-ttu-id="f2275-135">Obory názvů v souborech a sestaveních</span><span class="sxs-lookup"><span data-stu-id="f2275-135">Namespaces in Files and Assemblies</span></span>

<span data-ttu-id="f2275-136">Obory názvů mohou zahrnovat více souborů v jednom projektu nebo kompilaci.</span><span class="sxs-lookup"><span data-stu-id="f2275-136">Namespaces can span multiple files in a single project or compilation.</span></span> <span data-ttu-id="f2275-137">Pojem *fragment oboru názvů* popisuje část oboru názvů, která je obsažena v jednom souboru.</span><span class="sxs-lookup"><span data-stu-id="f2275-137">The term *namespace fragment* describes the part of a namespace that is included in one file.</span></span> <span data-ttu-id="f2275-138">Obory názvů mohou také zahrnovat více sestavení.</span><span class="sxs-lookup"><span data-stu-id="f2275-138">Namespaces can also span multiple assemblies.</span></span> <span data-ttu-id="f2275-139">Například `System` obor názvů zahrnuje celou .NET Framework, která zahrnuje mnoho sestavení a obsahuje mnoho vnořených oborů názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-139">For example, the `System` namespace includes the whole .NET Framework, which spans many assemblies and contains many nested namespaces.</span></span>

## <a name="global-namespace"></a><span data-ttu-id="f2275-140">Globální obor názvů</span><span class="sxs-lookup"><span data-stu-id="f2275-140">Global Namespace</span></span>

<span data-ttu-id="f2275-141">Předdefinovaný obor názvů `global` slouží k umístění názvů do oboru názvů na nejvyšší úrovni .NET.</span><span class="sxs-lookup"><span data-stu-id="f2275-141">You use the predefined namespace `global` to put names in the .NET top-level namespace.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6407.fs)]

<span data-ttu-id="f2275-142">Globální můžete použít také k odkazování na obor názvů .NET nejvyšší úrovně, například pro vyřešení konfliktu názvů s jinými obory názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-142">You can also use global to reference the top-level .NET namespace, for example, to resolve name conflicts with other namespaces.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6408.fs)]

## <a name="recursive-namespaces"></a><span data-ttu-id="f2275-143">Rekurzivní obory názvů</span><span class="sxs-lookup"><span data-stu-id="f2275-143">Recursive namespaces</span></span>

<span data-ttu-id="f2275-144">Obory názvů lze také deklarovat jako rekurzivní, aby bylo možné veškerý obsažený kód vzájemně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="f2275-144">Namespaces can also be declared as recursive to allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="f2275-145">To se provádí prostřednictvím `namespace rec`.</span><span class="sxs-lookup"><span data-stu-id="f2275-145">This is done via `namespace rec`.</span></span> <span data-ttu-id="f2275-146">Použití aplikace `namespace rec` může zmírnit některé bolesti v neschopnost psát vzájemně referenční kód mezi typy a moduly.</span><span class="sxs-lookup"><span data-stu-id="f2275-146">Use of `namespace rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span> <span data-ttu-id="f2275-147">Zde je příklad:</span><span class="sxs-lookup"><span data-stu-id="f2275-147">The following is an example of this:</span></span>

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

<span data-ttu-id="f2275-148">Všimněte si, že `DontSqueezeTheBananaException` výjimka a třída `Banana` odkazují na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="f2275-148">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="f2275-149">Kromě toho modul `BananaHelpers` a třída `Banana` také odkazují na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="f2275-149">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span> <span data-ttu-id="f2275-150">To by nebylo možné vyjádřit v F# případě, že jste odebrali `rec` klíčové slovo z `MutualReferences` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f2275-150">This wouldn't be possible to express in F# if you removed the `rec` keyword from the `MutualReferences` namespace.</span></span>

<span data-ttu-id="f2275-151">Tato funkce je k dispozici také pro [moduly](modules.md)nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="f2275-151">This feature is also available for top-level [Modules](modules.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f2275-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2275-152">See also</span></span>

- [<span data-ttu-id="f2275-153">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="f2275-153">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f2275-154">Moduly</span><span class="sxs-lookup"><span data-stu-id="f2275-154">Modules</span></span>](modules.md)
- [<span data-ttu-id="f2275-155">F#RFC FS-1009 – povoluje vzájemně se referenční typy a moduly nad větším rozsahem v rámci souborů.</span><span class="sxs-lookup"><span data-stu-id="f2275-155">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
