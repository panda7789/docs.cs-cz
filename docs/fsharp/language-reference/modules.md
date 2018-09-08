---
title: Moduly (F#)
description: 'Zjistěte, jak modulu F # je seskupení kódu jazyka F #, jako jsou hodnoty, typy a hodnoty funkcí v programu F #.'
ms.date: 04/24/2017
ms.openlocfilehash: fb0aa1d508d1141933b4fbdf10633f67ed078dc7
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44178218"
---
# <a name="modules"></a><span data-ttu-id="1ec4d-103">Moduly</span><span class="sxs-lookup"><span data-stu-id="1ec4d-103">Modules</span></span>

<span data-ttu-id="1ec4d-104">V rámci jazyka F # *modulu* je seskupení kódu jazyka F #, jako jsou hodnoty, typy a hodnoty funkcí v programu F #.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="1ec4d-105">Kód v modulech seskupení udržet související kód společně a pomáhá zamezilo se konfliktům názvů ve svém programu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="1ec4d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ec4d-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="1ec4d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ec4d-107">Remarks</span></span>

<span data-ttu-id="1ec4d-108">Modulu F # je seskupení kód konstrukce F # jako je například typy, hodnoty, funkce hodnot a kódu v `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="1ec4d-109">Je implementován jako common language runtime (CLR) třídu, která obsahuje pouze statické členy.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="1ec4d-110">Existují dva typy deklarací modulu, v závislosti na tom, jestli je celý soubor součástí modulu: nejvyšší úrovně modulu prohlášení a prohlášení místní modul.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="1ec4d-111">Deklarace nejvyšší úrovně modulu zahrnuje celý soubor v modulu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="1ec4d-112">Deklarace nejvyšší úrovně modulu se může objevit pouze jako první deklarací v souboru.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="1ec4d-113">V syntaxi pro deklaraci nejvyšší úrovně modulu, volitelný *kvalifikovaný obor názvů* je posloupnost názvy vnořené obory názvů, který obsahuje modul.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="1ec4d-114">Kvalifikovaný obor názvů nemusí být deklarována.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="1ec4d-115">Není potřeba odsazení deklarace v nejvyšší úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="1ec4d-116">Budete muset odsazení všechny deklarace v lokální moduly.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="1ec4d-117">V deklaraci místní modul jenom deklarace, které jsou odsazené pod tento modul deklarace jsou součástí daného modulu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="1ec4d-118">Pokud soubor kódu nemá na začátku deklarace nejvyšší úrovně modulu nebo deklarace oboru názvů, celý obsah souboru, včetně všech místních modulů se stane součástí implicitně vytvořené nejvyšší úrovně modulu, který má stejný název jako soubor bez přípon kde je převeden na velká písmena první písmeno.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="1ec4d-119">Zvažte například následující soubor.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="1ec4d-120">Tento soubor by zkompilován, jako kdyby byly napsány tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="1ec4d-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="1ec4d-121">Pokud máte více modulů v souboru, musíte použít místní modul deklarace pro každý modul.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="1ec4d-122">Pokud je deklarovaná nadřazeného oboru názvů, tyto moduly jsou součástí nadřazeného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="1ec4d-123">Pokud není deklarován nadřazeného oboru názvů, moduly se stanou součástí modulu implicitně vytvořené nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="1ec4d-124">Následující příklad kódu ukazuje soubor kódu, který obsahuje více modulů.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="1ec4d-125">Kompilátor implicitně vytvoří modul nejvyšší úrovně s názvem `Multiplemodules`, a `MyModule1` a `MyModule2` jsou vnořené v nejvyšší úrovni modulu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="1ec4d-126">Pokud máte více souborů v projektu nebo v jedné kompilaci nebo pokud vytváříte knihovnu, musí obsahovat deklarace oboru názvů nebo modulu deklarace v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="1ec4d-127">Kompilátor F # pouze implicitně Určuje název modulu, pokud existuje pouze jeden soubor v příkazovém řádku projekt nebo kompilaci a vytváření aplikace.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="1ec4d-128">*Modifikátor dostupnosti* může být jedna z následujících akcí: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="1ec4d-129">Další informace najdete v tématu [řízení přístupu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="1ec4d-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="1ec4d-130">Výchozí hodnota je veřejná.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="1ec4d-131">Odkazování na kód v modulech</span><span class="sxs-lookup"><span data-stu-id="1ec4d-131">Referencing Code in Modules</span></span>

<span data-ttu-id="1ec4d-132">Když odkazujete z jiného modulu funkce, typy a hodnoty, musíte použít úplný název nebo otevřete modul.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="1ec4d-133">Pokud používáte úplný název, musíte zadat obory názvů, modulu a identifikátor pro ovládací prvek programu, který chcete.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="1ec4d-134">Oddělíte jednotlivých součástí kvalifikovanou cestu s tečkou (.), následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="1ec4d-135">Můžete otevřít modul nebo jeden nebo více oborů názvů pro zjednodušení kódu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="1ec4d-136">Další informace o oborech názvů otevírání a moduly, naleznete v tématu [deklarace importu: `open` – klíčové slovo](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="1ec4d-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="1ec4d-137">Následující příklad kódu ukazuje nejvyšší úrovně modulu, který obsahuje všechny kódu až po konec souboru.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="1ec4d-138">Chcete-li použít tento kód z jiného souboru ve stejném projektu, buď použijte kvalifikované názvy nebo otevření modulu před použitím funkce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="1ec4d-139">Vnořené moduly</span><span class="sxs-lookup"><span data-stu-id="1ec4d-139">Nested Modules</span></span>

<span data-ttu-id="1ec4d-140">Moduly mohou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-140">Modules can be nested.</span></span> <span data-ttu-id="1ec4d-141">Vnitřní moduly musí být odsazen až na hodnotu deklarace vnější modulů k označení, že jsou vnitřní moduly, nikoli nové moduly.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="1ec4d-142">Například porovnejte následující dva příklady.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-142">For example, compare the following two examples.</span></span> <span data-ttu-id="1ec4d-143">Modul `Z` je vnitřní modul v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="1ec4d-144">Ale modulu `Z` na stejné úrovni modulu `Y` v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="1ec4d-145">Modul `Z` je také modul na stejné úrovni v následujícím kódu, protože nebude odsazena až na hodnotu dalšími deklaracemi v modulu `Y`.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="1ec4d-146">Nakonec pokud vnější modul nemá žádná prohlášení a je okamžitě následován jiné deklarace modulu, nové deklarace modulu je považován za vnitřního modulu, ale kompilátor upozorní, pokud není druhá definice modulu odsazen dále než první.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="1ec4d-147">Chcete-li upozornění odstranit, odsazení vnitřního modulu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="1ec4d-148">Pokud chcete, aby veškerý kód v souboru v modulu single vnější a vnitřní moduly, modul vnější nevyžaduje znaménko rovná se a deklarace, včetně jakékoli vnitřní modul deklarace, které půjdou ve vnější modulu nemají odsazeny.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="1ec4d-149">Deklarace uvnitř deklarací vnitřní modul musí být odsazeny.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="1ec4d-150">Následující kód ukazuje tento případ.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-150">The following code shows this case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="1ec4d-151">Rekurzivní moduly</span><span class="sxs-lookup"><span data-stu-id="1ec4d-151">Recursive modules</span></span>

<span data-ttu-id="1ec4d-152">F # 4.1 zavádí pojem moduly, které umožňují použití všechny obsažené kód je vzájemně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="1ec4d-153">To se provádí prostřednictvím `module rec`.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-153">This is done via `module rec`.</span></span>  <span data-ttu-id="1ec4d-154">Použití `module rec` může vyřešit některé důsledně v nebude moci napsat kód vzájemně referenční typy a moduly.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="1ec4d-155">Následuje příklad:</span><span class="sxs-lookup"><span data-stu-id="1ec4d-155">The following is an example of this:</span></span>

```fsharp
module rec RecursiveModule =
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

<span data-ttu-id="1ec4d-156">Všimněte si, že výjimka `DontSqueezeTheBananaException` a třída `Banana` odkazují na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="1ec4d-157">Kromě toho modul `BananaHelpers` a třída `Banana` také odkazovat na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="1ec4d-158">To by nebylo možné vyjádřit v jazyce F #, pokud jste odebrali `rec` – klíčové slovo z `RecursiveModule` modulu.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="1ec4d-159">Tato možnost je také možné u [obory názvů](namespaces.md) s F # 4.1.</span><span class="sxs-lookup"><span data-stu-id="1ec4d-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ec4d-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1ec4d-160">See also</span></span>

- [<span data-ttu-id="1ec4d-161">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="1ec4d-161">F# Language Reference</span></span>](index.md)  
- [<span data-ttu-id="1ec4d-162">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="1ec4d-162">Namespaces</span></span>](namespaces.md)  
- [<span data-ttu-id="1ec4d-163">1009-F # RFC FS - povolit vzájemně referenční typy a moduly přes větší oborů v rámci souborů</span><span class="sxs-lookup"><span data-stu-id="1ec4d-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)  
