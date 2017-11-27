---
title: Moduly (F#)
description: "Zjistěte, jak modul F # je seskupení F # kódu, například hodnoty, typy a hodnoty funkce v programu F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 46de2d18-da51-40fa-a262-92edecada79d
ms.openlocfilehash: 89401c1f889be6c5585a302e3a7ac62478573b95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="modules"></a><span data-ttu-id="6a7ce-104">Moduly</span><span class="sxs-lookup"><span data-stu-id="6a7ce-104">Modules</span></span>

<span data-ttu-id="6a7ce-105">V kontextu jazyk F # *modulu* je seskupení F # kódu, například hodnoty, typy a hodnoty funkce v programu F #.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-105">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="6a7ce-106">Kód v modulech seskupení vám pomůže uchovávat související kód společně a pomáhá zabránit název je v konfliktu v programu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-106">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="6a7ce-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6a7ce-107">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="6a7ce-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6a7ce-108">Remarks</span></span>
<span data-ttu-id="6a7ce-109">Modul F # je seskupení F # kód konstruktory, jako jsou typy, hodnoty, funkce hodnoty a kódu v `do` vazby.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-109">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="6a7ce-110">Rozhraní je implementováno jako běžné třídy language runtime (CLR), která má jenom statické členy.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-110">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="6a7ce-111">Existují dva typy deklarací modulu, v závislosti na tom, jestli je celý soubor součástí modulu: nejvyšší úrovně modul deklarace a deklaraci místního modulu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-111">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="6a7ce-112">Deklaraci nejvyšší úrovně modulu zahrnuje celý soubor v modulu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-112">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="6a7ce-113">Deklaraci nejvyšší úrovně modul může se objevit pouze jako první deklaraci do souboru.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-113">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="6a7ce-114">V syntaxi pro deklaraci nejvyšší úrovně modulu nepovinný *kvalifikovaný obor názvů* sekvence názvy vnořené oborů názvů, který obsahuje modul.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-114">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="6a7ce-115">Kvalifikovaný obor názvů nemusí být předtím nebyl deklarovaný.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-115">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="6a7ce-116">Nemáte odsazovat deklarace v modulu nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-116">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="6a7ce-117">Budete muset odsazovat všechny deklarace v lokální moduly.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-117">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="6a7ce-118">V deklaraci místního modulu jenom deklarace, které odsazeny pod tento modul deklarace jsou součástí daného modulu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-118">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="6a7ce-119">Pokud soubor kód nezačíná nejvyšší úrovně modulu deklaraci nebo deklarace oboru názvů, celý obsah souboru, včetně všech modulů místní stane součástí modul implicitně vytvořených nejvyšší úrovně, který má stejný název jako soubor bez přípony, první písmeno převeden na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-119">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="6a7ce-120">Zvažte například následující soubor.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-120">For example, consider the following file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="6a7ce-121">Tento soubor by být zkompilovány, jako kdyby byly napsány tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="6a7ce-121">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="6a7ce-122">Pokud máte více modulů v souboru, musíte použít deklaraci místního modulu pro každý modul.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-122">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="6a7ce-123">Pokud je deklarovaná nadřazených obor názvů, tyto moduly jsou součástí nadřazených oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-123">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="6a7ce-124">Pokud není deklarovaný nadřazených obor názvů, moduly se stanou součástí modul implicitně vytvořených nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-124">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="6a7ce-125">Následující příklad kódu ukazuje soubor kód, který obsahuje více modulů.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-125">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="6a7ce-126">Kompilátor implicitně vytvoří nejvyšší úrovně modul s názvem `Multiplemodules`, a `MyModule1` a `MyModule2` jsou vnořené v tomto modulu nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-126">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="6a7ce-127">Pokud máte více souborů v projektu nebo v jedné kompilaci nebo pokud vytváříte knihovny, je nutné zahrnout deklaraci oboru názvů nebo modul deklarace v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-127">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="6a7ce-128">Kompilátor jazyka F # pouze implicitně Určuje název modulu v případě, že existuje pouze jeden soubor na příkazovém řádku projektu nebo kompilace a vytvoříte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-128">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="6a7ce-129">*Modifikátor dostupnosti* může být jedna z následujících: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-129">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="6a7ce-130">Další informace najdete v tématu [řízení přístupu](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="6a7ce-130">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="6a7ce-131">Výchozí hodnota je veřejná.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-131">The default is public.</span></span>


## <a name="referencing-code-in-modules"></a><span data-ttu-id="6a7ce-132">Odkazování na kód v modulech</span><span class="sxs-lookup"><span data-stu-id="6a7ce-132">Referencing Code in Modules</span></span>
<span data-ttu-id="6a7ce-133">Když odkazujete funkcí, typy a hodnoty z jiný modul, musíte použít kvalifikovaný název nebo otevřete modul.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-133">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="6a7ce-134">Pokud používáte úplný název, je nutné zadat obory názvů, modulu a identifikátor elementu program, který má být.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-134">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="6a7ce-135">Oddělíte jednotlivých součástí kvalifikovanou cestu s tečkou (.), následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-135">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="6a7ce-136">Můžete otevřít modul nebo jeden nebo více oborů názvů, můžete zjednodušit kód.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-136">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="6a7ce-137">Další informace o otevírání obory názvů a moduly, naleznete v části [deklarace importu: `open` – klíčové slovo](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="6a7ce-137">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="6a7ce-138">Následující příklad kódu ukazuje nejvyšší úrovně modul, který obsahuje všechny kód do konce souboru.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-138">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="6a7ce-139">Pokud chcete použít tento kód z jiného souboru ve stejném projektu, můžete buď použít kvalifikované názvy nebo otevřete modul před použitím funkcí, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-139">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="6a7ce-140">Vnořené moduly</span><span class="sxs-lookup"><span data-stu-id="6a7ce-140">Nested Modules</span></span>
<span data-ttu-id="6a7ce-141">Moduly mohou být použity.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-141">Modules can be nested.</span></span> <span data-ttu-id="6a7ce-142">Vnitřní moduly musí být odsazeny Pokud je to vnější modul deklarace k označení, že se jedná o vnitřní moduly, není nové moduly.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-142">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="6a7ce-143">Například porovnejte následující dva příklady.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-143">For example, compare the following two examples.</span></span> <span data-ttu-id="6a7ce-144">Modul `Z` je modul vnitřní v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-144">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="6a7ce-145">Ale modul `Z` na stejné úrovni modulu `Y` v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-145">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="6a7ce-146">Modul `Z` je také modul na stejné úrovni jako v následujícím kódu, protože není s odsazením, pokud je to jiné deklarace v modulu `Y`.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-146">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="6a7ce-147">Navíc pokud vnější modul nemá žádné deklarace a okamžitě následuje se jiný modul deklarace, novou deklaraci modulu předpokládá se, že modul vnitřní, ale kompilátor upozornění, pokud není dále než odsazeny definici druhý modulu první.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-147">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="6a7ce-148">Pokud chcete odstranit toto upozornění, odsazovat vnitřní modulu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-148">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="6a7ce-149">Pokud chcete, aby všechny kód v souboru ve vnější jeden modul a chcete vnitřní moduly, modul vnější nevyžaduje znaménkem rovnosti a deklarace, včetně všech vnitřní modul deklarace, které přejde v modulu vnější nemají odsazení.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-149">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="6a7ce-150">Deklarace uvnitř deklarace vnitřní modulu by měly být zobrazují odsazené.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-150">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="6a7ce-151">Následující kód ukazuje tento případ.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-151">The following code shows this case.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="module-rec-allowing-mutual-recursive-code-at-the-module-level"></a><span data-ttu-id="6a7ce-152">Modul `rec`: povolení vzájemné rekurzivní kódu na úrovni modulu</span><span class="sxs-lookup"><span data-stu-id="6a7ce-152">Module `rec`: allowing mutual recursive code at the module level</span></span>

<span data-ttu-id="6a7ce-153">F # 4.1 zavádí představu o moduly, které umožňují všechny obsažené kódu být vzájemně rekurzivní.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-153">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="6a7ce-154">To se provádí prostřednictvím `module rec`.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-154">This is done via `module rec`.</span></span>  <span data-ttu-id="6a7ce-155">Použití `module rec` můžete zmírnit některé důsledně v nebude moci napsat vzájemně referenční kód mezi typy a modulů.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-155">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="6a7ce-156">Následuje příklad tohoto:</span><span class="sxs-lookup"><span data-stu-id="6a7ce-156">The following is an example of this:</span></span>

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

    module private BananaHelpers =
        let peel (b : Banana) =
            let flip banana =
                match banana.Orientation with
                | Up -> 
                    banana.Orientation <- Down
                    banana
                | Down -> banana

            let peelSides banana =
                for side in banana.Sides do
                    if side = Unpeeled then
                        side <- Peeled

            match b.Orientation with
            | Up ->   b |> flip |> peelSides
            | Down -> b |> peelSides
```

<span data-ttu-id="6a7ce-157">Všimněte si, že výjimka `DontSqueezeTheBananaException` a třídu `Banana` odkazují na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-157">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="6a7ce-158">Kromě toho modul `BananaHelpers` a třídu `Banana` se také podívat na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-158">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="6a7ce-159">To nebude možné v jazyce F # express, pokud jste odebrali `rec` – klíčové slovo z `RecursiveModule` modulu.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-159">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="6a7ce-160">Tato funkce je také možné v [obory názvů](namespaces.md) s F # 4.1.</span><span class="sxs-lookup"><span data-stu-id="6a7ce-160">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a7ce-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="6a7ce-161">See Also</span></span>

<span data-ttu-id="6a7ce-162">[Referenční dokumentace jazyka F #](index.md)
[obory názvů](namespaces.md)
[F # RFC 1009 FS - povolit vzájemně referenční typy a moduly přes větší oborů v rámci soubory](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)</span><span class="sxs-lookup"><span data-stu-id="6a7ce-162">[F# Language Reference](index.md)
[Namespaces](namespaces.md)
[F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)</span></span>
