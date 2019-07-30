---
title: Moduly
description: Zjistěte, jak F# je modul seskupením F# kódu, jako jsou hodnoty, typy a hodnoty funkcí v F# programu.
ms.date: 04/24/2017
ms.openlocfilehash: 685ab638e7e1b6c8d47d1a316483abcc18e40199
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627423"
---
# <a name="modules"></a><span data-ttu-id="cec2a-103">Moduly</span><span class="sxs-lookup"><span data-stu-id="cec2a-103">Modules</span></span>

<span data-ttu-id="cec2a-104">V kontextu F# jazyka je *modul* seskupením F# kódu, jako jsou hodnoty, typy a hodnoty funkcí v F# programu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-104">In the context of the F# language, a *module* is a grouping of F# code, such as values, types, and function values, in an F# program.</span></span> <span data-ttu-id="cec2a-105">Seskupení kódu v modulech pomáhá udržet související kód dohromady a pomáhá vyhnout se konfliktům názvů v programu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-105">Grouping code in modules helps keep related code together and helps avoid name conflicts in your program.</span></span>

## <a name="syntax"></a><span data-ttu-id="cec2a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cec2a-106">Syntax</span></span>

```fsharp
// Top-level module declaration.
module [accessibility-modifier] [qualified-namespace.]module-name
declarations
// Local module declaration.
module [accessibility-modifier] module-name =
    declarations
```

## <a name="remarks"></a><span data-ttu-id="cec2a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cec2a-107">Remarks</span></span>

<span data-ttu-id="cec2a-108">F# Modul je seskupení konstrukcí F# kódu, jako jsou typy, hodnoty, hodnoty funkcí a kód v `do` vazbách.</span><span class="sxs-lookup"><span data-stu-id="cec2a-108">An F# module is a grouping of F# code constructs such as types, values, function values, and code in `do` bindings.</span></span> <span data-ttu-id="cec2a-109">Je implementován jako třída modulu CLR (Common Language Runtime), která má pouze statické členy.</span><span class="sxs-lookup"><span data-stu-id="cec2a-109">It is implemented as a common language runtime (CLR) class that has only static members.</span></span> <span data-ttu-id="cec2a-110">Existují dva typy deklarací modulů v závislosti na tom, zda je celý soubor součástí modulu: deklarace modulu nejvyšší úrovně a deklarace místní modul.</span><span class="sxs-lookup"><span data-stu-id="cec2a-110">There are two types of module declarations, depending on whether the whole file is included in the module: a top-level module declaration and a local module declaration.</span></span> <span data-ttu-id="cec2a-111">Deklarace modulu nejvyšší úrovně zahrnuje celý soubor v modulu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-111">A top-level module declaration includes the whole file in the module.</span></span> <span data-ttu-id="cec2a-112">Deklarace modulu nejvyšší úrovně se může objevit pouze jako první deklarace v souboru.</span><span class="sxs-lookup"><span data-stu-id="cec2a-112">A top-level module declaration can appear only as the first declaration in a file.</span></span>

<span data-ttu-id="cec2a-113">V syntaxi pro deklaraci modulu nejvyšší úrovně je volitelné *kvalifikované obory názvů* posloupnost názvů vnořených oborů názvů, které obsahují modul.</span><span class="sxs-lookup"><span data-stu-id="cec2a-113">In the syntax for the top-level module declaration, the optional *qualified-namespace* is the sequence of nested namespace names that contains the module.</span></span> <span data-ttu-id="cec2a-114">Kvalifikovaný obor názvů nemusí být dřív deklarovaný.</span><span class="sxs-lookup"><span data-stu-id="cec2a-114">The qualified namespace does not have to be previously declared.</span></span>

<span data-ttu-id="cec2a-115">V modulu nejvyšší úrovně není nutné odsazovat deklarace.</span><span class="sxs-lookup"><span data-stu-id="cec2a-115">You do not have to indent declarations in a top-level module.</span></span> <span data-ttu-id="cec2a-116">Musíte odsadit všechny deklarace v místních modulech.</span><span class="sxs-lookup"><span data-stu-id="cec2a-116">You do have to indent all declarations in local modules.</span></span> <span data-ttu-id="cec2a-117">V deklaraci místního modulu jsou součástí modulu pouze deklarace, které jsou odsazeny pod deklarací tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-117">In a local module declaration, only the declarations that are indented under that module declaration are part of the module.</span></span>

<span data-ttu-id="cec2a-118">Pokud soubor s kódem nezačíná deklarací modulu nejvyšší úrovně nebo deklarací oboru názvů, celý obsah souboru, včetně všech místních modulů, se stávají součástí implicitně vytvořeného modulu nejvyšší úrovně, který má stejný název jako soubor bez přípony, první písmeno se převedlo na velká písmena.</span><span class="sxs-lookup"><span data-stu-id="cec2a-118">If a code file does not begin with a top-level module declaration or a namespace declaration, the whole contents of the file, including any local modules, becomes part of an implicitly created top-level module that has the same name as the file, without the extension, with the first letter converted to uppercase.</span></span> <span data-ttu-id="cec2a-119">Zvažte například následující soubor.</span><span class="sxs-lookup"><span data-stu-id="cec2a-119">For example, consider the following file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6601.fs)]

<span data-ttu-id="cec2a-120">Tento soubor se zkompiluje, jako by byl napsán tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="cec2a-120">This file would be compiled as if it were written in this manner:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6602.fs)]

<span data-ttu-id="cec2a-121">Máte-li v souboru více modulů, je nutné pro každý modul použít deklaraci místního modulu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-121">If you have multiple modules in a file, you must use a local module declaration for each module.</span></span> <span data-ttu-id="cec2a-122">Pokud je deklarován obor názvů ohraničující, jsou tyto moduly součástí ohraničujícího oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="cec2a-122">If an enclosing namespace is declared, these modules are part of the enclosing namespace.</span></span> <span data-ttu-id="cec2a-123">Pokud obor názvů ohraničující není deklarovaný, moduly se stanou součástí implicitně vytvořeného modulu nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="cec2a-123">If an enclosing namespace is not declared, the modules become part of the implicitly created top-level module.</span></span> <span data-ttu-id="cec2a-124">Následující příklad kódu ukazuje soubor kódu, který obsahuje více modulů.</span><span class="sxs-lookup"><span data-stu-id="cec2a-124">The following code example shows a code file that contains multiple modules.</span></span> <span data-ttu-id="cec2a-125">Kompilátor implicitně vytvoří modul nejvyšší úrovně s názvem `Multiplemodules` `MyModule1` a a `MyModule2` je vnořen do tohoto modulu nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="cec2a-125">The compiler implicitly creates a top-level module named `Multiplemodules`, and `MyModule1` and `MyModule2` are nested in that top-level module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6603.fs)]

<span data-ttu-id="cec2a-126">Pokud máte více souborů v projektu nebo v jedné kompilaci, nebo pokud vytváříte knihovnu, musíte do horní části souboru zahrnout deklaraci oboru názvů nebo deklaraci modulu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-126">If you have multiple files in a project or in a single compilation, or if you are building a library, you must include a namespace declaration or module declaration at the top of the file.</span></span> <span data-ttu-id="cec2a-127">F# Kompilátor pouze v případě, že existuje pouze jeden soubor v projektu nebo příkazovém řádku kompilace a vytváří aplikaci, pouze implicitně určí název modulu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-127">The F# compiler only determines a module name implicitly when there is only one file in a project or compilation command line, and you are creating an application.</span></span>

<span data-ttu-id="cec2a-128">*Modifikátor* přístupnosti může být jedna z následujících: `public`, `private`, `internal`.</span><span class="sxs-lookup"><span data-stu-id="cec2a-128">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="cec2a-129">Další informace najdete v tématu [Access Control](access-control.md).</span><span class="sxs-lookup"><span data-stu-id="cec2a-129">For more information, see [Access Control](access-control.md).</span></span> <span data-ttu-id="cec2a-130">Výchozí hodnota je Public.</span><span class="sxs-lookup"><span data-stu-id="cec2a-130">The default is public.</span></span>

## <a name="referencing-code-in-modules"></a><span data-ttu-id="cec2a-131">Odkazování na kód v modulech</span><span class="sxs-lookup"><span data-stu-id="cec2a-131">Referencing Code in Modules</span></span>

<span data-ttu-id="cec2a-132">Když odkazujete na funkce, typy a hodnoty z jiného modulu, musíte buď použít kvalifikovaný název, nebo otevřít modul.</span><span class="sxs-lookup"><span data-stu-id="cec2a-132">When you reference functions, types, and values from another module, you must either use a qualified name or open the module.</span></span> <span data-ttu-id="cec2a-133">Použijete-li kvalifikovaný název, je nutné zadat obory názvů, modul a identifikátor požadovaného prvku programu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-133">If you use a qualified name, you must specify the namespaces, the module, and the identifier for the program element you want.</span></span> <span data-ttu-id="cec2a-134">Jednotlivé části kvalifikované cesty oddělte tečkou (.), a to následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="cec2a-134">You separate each part of the qualified path with a dot (.), as follows.</span></span>

`Namespace1.Namespace2.ModuleName.Identifier`

<span data-ttu-id="cec2a-135">Můžete otevřít modul nebo jeden nebo více oborů názvů a zjednodušit tak kód.</span><span class="sxs-lookup"><span data-stu-id="cec2a-135">You can open the module or one or more of the namespaces to simplify the code.</span></span> <span data-ttu-id="cec2a-136">Další informace o otevření oborů názvů a modulů najdete v [tématu Import deklarací: `open` Klíčové slovo](import-declarations-the-open-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="cec2a-136">For more information about opening namespaces and modules, see [Import Declarations: The `open` Keyword](import-declarations-the-open-keyword.md).</span></span>

<span data-ttu-id="cec2a-137">Následující příklad kódu ukazuje modul nejvyšší úrovně, který obsahuje veškerý kód na konec souboru.</span><span class="sxs-lookup"><span data-stu-id="cec2a-137">The following code example shows a top-level module that contains all the code up to the end of the file.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6604.fs)]

<span data-ttu-id="cec2a-138">Chcete-li použít tento kód z jiného souboru ve stejném projektu, použijte buď kvalifikované názvy, nebo otevřete modul před použitím funkcí, jak je znázorněno v následujících příkladech.</span><span class="sxs-lookup"><span data-stu-id="cec2a-138">To use this code from another file in the same project, you either use qualified names or you open the module before you use the functions, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6605.fs)]

## <a name="nested-modules"></a><span data-ttu-id="cec2a-139">Vnořené moduly</span><span class="sxs-lookup"><span data-stu-id="cec2a-139">Nested Modules</span></span>

<span data-ttu-id="cec2a-140">Moduly můžou být vnořené.</span><span class="sxs-lookup"><span data-stu-id="cec2a-140">Modules can be nested.</span></span> <span data-ttu-id="cec2a-141">Vnitřní moduly musí být odsazené jako vnější deklarace modulu, aby označovaly, že se jedná o vnitřní moduly, nikoli nové moduly.</span><span class="sxs-lookup"><span data-stu-id="cec2a-141">Inner modules must be indented as far as outer module declarations to indicate that they are inner modules, not new modules.</span></span> <span data-ttu-id="cec2a-142">Například Porovnejte následující dva příklady.</span><span class="sxs-lookup"><span data-stu-id="cec2a-142">For example, compare the following two examples.</span></span> <span data-ttu-id="cec2a-143">Modul `Z` je vnitřní modul v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-143">Module `Z` is an inner module in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6607.fs)]

<span data-ttu-id="cec2a-144">Ale modul `Z` je na stejné úrovni jako `Y` modul v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-144">But module `Z` is a sibling to module `Y` in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6608.fs)]
<span data-ttu-id="cec2a-145">Modul `Z` je také modul na stejné úrovni v následujícím kódu, protože není odsazený jako jiné deklarace v modulu `Y`.</span><span class="sxs-lookup"><span data-stu-id="cec2a-145">Module `Z` is also a sibling module in the following code, because it is not indented as far as other declarations in module `Y`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6609.fs)]
<span data-ttu-id="cec2a-146">Nakonec, pokud vnější modul nemá žádné deklarace a za ním následuje další deklarace modulu, předpokládá se, že nová deklarace modulu je vnitřní modul, ale kompilátor vás upozorní, pokud není druhá definice modulu odsazena dále než první.</span><span class="sxs-lookup"><span data-stu-id="cec2a-146">Finally, if the outer module has no declarations and is followed immediately by another module declaration, the new module declaration is assumed to be an inner module, but the compiler will warn you if the second module definition is not indented farther than the first.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6610.fs)]
<span data-ttu-id="cec2a-147">Chcete-li odstranit upozornění, odsadit vnitřní modul.</span><span class="sxs-lookup"><span data-stu-id="cec2a-147">To eliminate the warning, indent the inner module.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6611.fs)]
<span data-ttu-id="cec2a-148">Pokud chcete, aby byl veškerý kód v souboru v jednom vnějším modulu a aby byly interní moduly, vnější modul nevyžaduje znaménko rovná se a deklarace, včetně všech vnitřních modulů deklarací, které se budou předávat do vnějšího modulu, nemusí být odsazeny.</span><span class="sxs-lookup"><span data-stu-id="cec2a-148">If you want all the code in a file to be in a single outer module and you want inner modules, the outer module does not require the equal sign, and the declarations, including any inner module declarations, that will go in the outer module do not have to be indented.</span></span> <span data-ttu-id="cec2a-149">Deklarace v deklaracích vnitřních modulů musí být odsazené.</span><span class="sxs-lookup"><span data-stu-id="cec2a-149">Declarations inside the inner module declarations do have to be indented.</span></span> <span data-ttu-id="cec2a-150">Následující kód ukazuje tento případ.</span><span class="sxs-lookup"><span data-stu-id="cec2a-150">The following code shows this case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/modules/snippet6612.fs)]

## <a name="recursive-modules"></a><span data-ttu-id="cec2a-151">Rekurzivní moduly</span><span class="sxs-lookup"><span data-stu-id="cec2a-151">Recursive modules</span></span>

<span data-ttu-id="cec2a-152">F#4,1 zavádí fiktivní moduly, které umožňují vzájemně rekurzivní kódování veškerého obsaženého kódu.</span><span class="sxs-lookup"><span data-stu-id="cec2a-152">F# 4.1 introduces the notion of modules which allow for all contained code to be mutually recursive.</span></span>  <span data-ttu-id="cec2a-153">To se provádí prostřednictvím `module rec`.</span><span class="sxs-lookup"><span data-stu-id="cec2a-153">This is done via `module rec`.</span></span>  <span data-ttu-id="cec2a-154">Použití aplikace `module rec` může zmírnit některé bolesti v neschopnost psát vzájemně referenční kód mezi typy a moduly.</span><span class="sxs-lookup"><span data-stu-id="cec2a-154">Use of `module rec` can alleviate some pains in not being able to write mutually referential code between types and modules.</span></span>  <span data-ttu-id="cec2a-155">Zde je příklad:</span><span class="sxs-lookup"><span data-stu-id="cec2a-155">The following is an example of this:</span></span>

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

<span data-ttu-id="cec2a-156">Všimněte si, že `DontSqueezeTheBananaException` výjimka a třída `Banana` odkazují na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="cec2a-156">Note that the exception `DontSqueezeTheBananaException` and the class `Banana` both refer to each other.</span></span>  <span data-ttu-id="cec2a-157">Kromě toho modul `BananaHelpers` a třída `Banana` také odkazují na sebe navzájem.</span><span class="sxs-lookup"><span data-stu-id="cec2a-157">Additionally, the module `BananaHelpers` and the class `Banana` also refer to each other.</span></span>  <span data-ttu-id="cec2a-158">To by nebylo možné vyjádřit v F# případě, že jste z `rec` `RecursiveModule` modulu odebrali klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="cec2a-158">This would not be possible to express in F# if you removed the `rec` keyword from the `RecursiveModule` module.</span></span>

<span data-ttu-id="cec2a-159">Tato funkce je také možné použít v [oborech názvů](namespaces.md) s F# 4,1.</span><span class="sxs-lookup"><span data-stu-id="cec2a-159">This capability is also possible in [Namespaces](namespaces.md) with F# 4.1.</span></span>

## <a name="see-also"></a><span data-ttu-id="cec2a-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cec2a-160">See also</span></span>

- [<span data-ttu-id="cec2a-161">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="cec2a-161">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="cec2a-162">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="cec2a-162">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="cec2a-163">F#RFC FS-1009 – povoluje vzájemně se referenční typy a moduly nad větším rozsahem v rámci souborů.</span><span class="sxs-lookup"><span data-stu-id="cec2a-163">F# RFC FS-1009 - Allow mutually referential types and modules over larger scopes within files</span></span>](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.1/FS-1009-mutually-referential-types-and-modules-single-scope.md)
