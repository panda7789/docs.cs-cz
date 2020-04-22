---
title: 'Deklarace importu: Klíčové slovo open'
description: Další informace o Deklaracích importu Jazyka F# a o tom, jak určují modul nebo obor názvů, na jejichž prvky můžete odkazovat bez použití plně kvalifikovaného názvu.
ms.date: 04/04/2019
ms.openlocfilehash: 0baef27c7dc3181b9da0defb1c793fec04269c09
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021541"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="0eb33-103">Dovozní prohlášení: `open` Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="0eb33-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="0eb33-104">Odkazy na odkazy na odkazy na odkazy na rozhraní API v tomto článku přejdete na msdn.</span><span class="sxs-lookup"><span data-stu-id="0eb33-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="0eb33-105">Odkaz na rozhraní API docs.microsoft.com není dokončen.</span><span class="sxs-lookup"><span data-stu-id="0eb33-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="0eb33-106">*Deklarace importu* určuje modul nebo obor názvů, na jejichž prvky můžete odkazovat bez použití plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="0eb33-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="0eb33-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0eb33-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="0eb33-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0eb33-108">Remarks</span></span>

<span data-ttu-id="0eb33-109">Odkazování na kód pomocí plně kvalifikovaný obor názvů nebo cesta modulu pokaždé, když můžete vytvořit kód, který je obtížné psát, číst a udržovat.</span><span class="sxs-lookup"><span data-stu-id="0eb33-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="0eb33-110">Místo toho můžete `open` použít klíčové slovo pro často používané moduly a obory názvů tak, aby při odkazování na člena tohoto modulu nebo oboru názvů, můžete použít krátký formulář názvu namísto plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="0eb33-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="0eb33-111">Toto klíčové slovo `using` je podobné `using namespace` klíčovému slovu v `Imports` jazyce C#, v jazyce Visual C++ a v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0eb33-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="0eb33-112">Zadaný modul nebo obor názvů musí být ve stejném projektu nebo v odkazovaném projektu nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="0eb33-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="0eb33-113">Pokud tomu tak není, můžete přidat odkaz na `-reference` projekt nebo použít možnost příkazového řádku (nebo jeho zkratku). `-r`</span><span class="sxs-lookup"><span data-stu-id="0eb33-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="0eb33-114">Další informace naleznete v [tématu Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="0eb33-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="0eb33-115">Deklarace importu zpřístupní názvy v kódu, který následuje za deklarací, až do konce ohraničujícího oboru názvů, modulu nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="0eb33-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="0eb33-116">Použijete-li více dovozních deklarací, měly by se zobrazit na samostatných řádcích.</span><span class="sxs-lookup"><span data-stu-id="0eb33-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="0eb33-117">Následující kód ukazuje použití `open` klíčového slova pro zjednodušení kódu.</span><span class="sxs-lookup"><span data-stu-id="0eb33-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="0eb33-118">Kompilátor F# nevyzařuje chybu nebo upozornění, když dojde k nejasnostem, když dojde ke stejnému názvu ve více než jednom otevřeném modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0eb33-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="0eb33-119">Pokud dojde k nejasnostem, F# dává přednost nedávno otevřený modul nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="0eb33-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="0eb33-120">Například v následujícím kódu `empty` `Seq.empty`znamená , `empty` i když `List` je `Seq` umístěn v obou a moduly.</span><span class="sxs-lookup"><span data-stu-id="0eb33-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="0eb33-121">Proto buďte opatrní při otevření modulů nebo `List` `Seq` oborů názvů, jako jsou nebo které obsahují členy, které mají stejné názvy; místo toho zvažte použití kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="0eb33-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="0eb33-122">Měli byste se vyhnout jakékoli situaci, ve které je kód závislý na pořadí dovozních prohlášení.</span><span class="sxs-lookup"><span data-stu-id="0eb33-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="0eb33-123">Obory názvů, které jsou ve výchozím nastavení otevřené</span><span class="sxs-lookup"><span data-stu-id="0eb33-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="0eb33-124">Některé obory názvů jsou tak často používány v kódu F#, že jsou otevřeny implicitně bez nutnosti explicitní prohlášení o importu.</span><span class="sxs-lookup"><span data-stu-id="0eb33-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="0eb33-125">V následující tabulce jsou uvedeny obory názvů, které jsou ve výchozím nastavení otevřené.</span><span class="sxs-lookup"><span data-stu-id="0eb33-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="0eb33-126">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="0eb33-126">Namespace</span></span>|<span data-ttu-id="0eb33-127">Popis</span><span class="sxs-lookup"><span data-stu-id="0eb33-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="0eb33-128">Obsahuje základní definice typu F# pro předdefinované typy, jako `int` jsou například a `float`.</span><span class="sxs-lookup"><span data-stu-id="0eb33-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="0eb33-129">Obsahuje základní aritmetické `+` operace, jako jsou a `*`.</span><span class="sxs-lookup"><span data-stu-id="0eb33-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="0eb33-130">Obsahuje neměnné třídy `List` `Array`kolekce, jako jsou a .</span><span class="sxs-lookup"><span data-stu-id="0eb33-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="0eb33-131">Obsahuje typy pro řídicí konstrukce, jako je například opožděné vyhodnocení a asynchronní pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="0eb33-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="0eb33-132">Obsahuje funkce pro formátované vi, jako je například `printf` funkce.</span><span class="sxs-lookup"><span data-stu-id="0eb33-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="0eb33-133">Atribut automatického otevření</span><span class="sxs-lookup"><span data-stu-id="0eb33-133">AutoOpen Attribute</span></span>

<span data-ttu-id="0eb33-134">`AutoOpen` Atribut můžete použít na sestavení, pokud chcete automaticky otevřít obor názvů nebo modul, když se na sestavení odkazuje.</span><span class="sxs-lookup"><span data-stu-id="0eb33-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="0eb33-135">Atribut můžete také `AutoOpen` použít pro modul, který tento modul automaticky otevře při otevření nadřazeného modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0eb33-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="0eb33-136">Další informace naleznete v tématu [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="0eb33-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="0eb33-137">Atribut RequireQualifiedAccess</span><span class="sxs-lookup"><span data-stu-id="0eb33-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="0eb33-138">Některé moduly, záznamy nebo typy `RequireQualifiedAccess` sjednocení mohou určit atribut.</span><span class="sxs-lookup"><span data-stu-id="0eb33-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="0eb33-139">Při odkazování na prvky těchto modulů, záznamů nebo sjednocení je nutné použít kvalifikovaný název bez ohledu na to, zda zahrnete prohlášení o importu.</span><span class="sxs-lookup"><span data-stu-id="0eb33-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="0eb33-140">Pokud použijete tento atribut strategicky na typy, které definují běžně používané názvy, můžete zabránit kolizím názvů a tím učinit kód odolnější vůči změnám v knihovnách.</span><span class="sxs-lookup"><span data-stu-id="0eb33-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="0eb33-141">Další informace naleznete v tématu [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="0eb33-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="0eb33-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="0eb33-142">See also</span></span>

- [<span data-ttu-id="0eb33-143">Referenční příručka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="0eb33-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="0eb33-144">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="0eb33-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="0eb33-145">Moduly</span><span class="sxs-lookup"><span data-stu-id="0eb33-145">Modules</span></span>](modules.md)
