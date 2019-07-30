---
title: 'Deklarace importu: Klíčové slovo open'
description: Přečtěte F# si o prohlášeních pro import a o tom, jak specifikují modul nebo obor názvů, jejichž prvky můžete odkazovat bez použití plně kvalifikovaného názvu.
ms.date: 04/04/2019
ms.openlocfilehash: 816bac551692c3397290f64c6267ee22e4ce90fb
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630573"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="84c6f-103">Deklarace importu: Klíčové slovo `open`</span><span class="sxs-lookup"><span data-stu-id="84c6f-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="84c6f-104">Odkazy na reference k rozhraní API v tomto článku vás převezmou na MSDN.</span><span class="sxs-lookup"><span data-stu-id="84c6f-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="84c6f-105">Reference k rozhraní docs.microsoft.com API není dokončená.</span><span class="sxs-lookup"><span data-stu-id="84c6f-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="84c6f-106">*Deklarace importu* určuje modul nebo obor názvů, jehož prvky můžete odkazovat bez použití plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="84c6f-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="84c6f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="84c6f-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="84c6f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="84c6f-108">Remarks</span></span>

<span data-ttu-id="84c6f-109">Odkazování na kód pomocí plně kvalifikovaného oboru názvů nebo cesty modulu pokaždé může vytvořit kód, který je těžké zapsat, číst a udržovat.</span><span class="sxs-lookup"><span data-stu-id="84c6f-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="84c6f-110">Místo toho můžete použít `open` klíčové slovo pro často používané moduly a obory názvů tak, aby při odkazování na člena daného modulu nebo oboru názvů mohli použít krátký tvar názvu místo plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="84c6f-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="84c6f-111">Toto klíčové slovo je `using` podobné klíčovému slovu v `using namespace` C#, C++v vizuálu `Imports` a v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="84c6f-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="84c6f-112">Poskytnutý modul nebo obor názvů musí být ve stejném projektu nebo v odkazovaném projektu nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="84c6f-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="84c6f-113">Pokud není, můžete přidat odkaz na projekt nebo použít `-reference` parametr příkazového`-`řádku `-r`(nebo jeho zkratku).</span><span class="sxs-lookup"><span data-stu-id="84c6f-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="84c6f-114">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="84c6f-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="84c6f-115">Deklarace importu zpřístupňuje názvy v kódu, které následují po deklaraci, až do konce ohraničujícího oboru názvů, modulu nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="84c6f-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="84c6f-116">Při použití více deklarací importu by se měly zobrazit na samostatných řádcích.</span><span class="sxs-lookup"><span data-stu-id="84c6f-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="84c6f-117">Následující kód ukazuje použití `open` klíčového slova pro zjednodušení kódu.</span><span class="sxs-lookup"><span data-stu-id="84c6f-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="84c6f-118">F# Kompilátor negeneruje chybu ani varování, pokud dojde k nejednoznačnosti, když dojde k výskytu stejného názvu ve více než jednom otevřeném modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="84c6f-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="84c6f-119">Pokud dojde k nejednoznačnosti, F# dává přednost vašemu nedávno otevřenému modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="84c6f-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="84c6f-120">Například v následujícím kódu `empty` znamená `Seq.empty`, že i když `empty` je umístěn v `List` modulech a `Seq` .</span><span class="sxs-lookup"><span data-stu-id="84c6f-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="84c6f-121">Proto buďte opatrní při otevírání modulů nebo oborů názvů, jako jsou `List` nebo `Seq` obsahující členy, kteří mají stejné názvy. místo toho zvažte použití kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="84c6f-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="84c6f-122">Měli byste se vyhnout jakékoli situaci, ve které je kód závislý na pořadí importu deklarací.</span><span class="sxs-lookup"><span data-stu-id="84c6f-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="84c6f-123">Obory názvů, které jsou ve výchozím nastavení otevřeny</span><span class="sxs-lookup"><span data-stu-id="84c6f-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="84c6f-124">Některé obory názvů jsou tak často F# používány v kódu, které jsou otevírány implicitně bez nutnosti explicitní deklarace importu.</span><span class="sxs-lookup"><span data-stu-id="84c6f-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="84c6f-125">V následující tabulce jsou uvedeny obory názvů, které jsou ve výchozím nastavení otevřeny.</span><span class="sxs-lookup"><span data-stu-id="84c6f-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="84c6f-126">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="84c6f-126">Namespace</span></span>|<span data-ttu-id="84c6f-127">Popis</span><span class="sxs-lookup"><span data-stu-id="84c6f-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="84c6f-128">Obsahuje definice F# základních typů pro předdefinované typy, jako například `int` a. `float`</span><span class="sxs-lookup"><span data-stu-id="84c6f-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="84c6f-129">Obsahuje základní aritmetické operace, `+` jako `*`jsou a.</span><span class="sxs-lookup"><span data-stu-id="84c6f-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="84c6f-130">Obsahuje neměnné třídy kolekce, například `List` a `Array`.</span><span class="sxs-lookup"><span data-stu-id="84c6f-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="84c6f-131">Obsahuje typy pro řídicí konstrukce, jako je opožděné vyhodnocení a asynchronní pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="84c6f-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="84c6f-132">Obsahuje funkce pro naformátované vstupně-výstupní `printf` operace, jako je například funkce.</span><span class="sxs-lookup"><span data-stu-id="84c6f-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="84c6f-133">Atribut AutoOpen</span><span class="sxs-lookup"><span data-stu-id="84c6f-133">AutoOpen Attribute</span></span>

<span data-ttu-id="84c6f-134">Můžete použít `AutoOpen` atribut na sestavení, pokud chcete automaticky otevřít obor názvů nebo modul, když je odkazováno na sestavení.</span><span class="sxs-lookup"><span data-stu-id="84c6f-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="84c6f-135">Můžete také použít `AutoOpen` atribut na modul a automaticky tak otevřít tento modul, když je otevřený nadřazený modul nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="84c6f-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="84c6f-136">Další informace naleznete v tématu [Třída Core. AutoOpenAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="84c6f-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="84c6f-137">RequireQualifiedAccess – atribut</span><span class="sxs-lookup"><span data-stu-id="84c6f-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="84c6f-138">Některé typy modulů, záznamů nebo sjednocení mohou určovat `RequireQualifiedAccess` atribut.</span><span class="sxs-lookup"><span data-stu-id="84c6f-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="84c6f-139">Když odkazujete na prvky těchto modulů, záznamů nebo sjednocení, je nutné použít kvalifikovaný název bez ohledu na to, zda jste zahrnuli deklaraci importu.</span><span class="sxs-lookup"><span data-stu-id="84c6f-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="84c6f-140">Použijete-li tento atribut strategicky u typů, které definují běžně používané názvy, můžete se vyhnout kolizím názvů a následně zvýšit odolnost kódu vůči změnám v knihovnách.</span><span class="sxs-lookup"><span data-stu-id="84c6f-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="84c6f-141">Další informace naleznete v tématu [Třída Core. RequireQualifiedAccessAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="84c6f-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="84c6f-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="84c6f-142">See also</span></span>

- [<span data-ttu-id="84c6f-143">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="84c6f-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="84c6f-144">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="84c6f-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="84c6f-145">Moduly</span><span class="sxs-lookup"><span data-stu-id="84c6f-145">Modules</span></span>](modules.md)
