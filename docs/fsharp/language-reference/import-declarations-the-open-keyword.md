---
title: 'Deklarace importu: Klíčové slovo open'
description: 'Přečtěte si o deklaracích importu F # a o tom, jak specifikují modul nebo obor názvů, jejichž prvky můžete odkazovat bez použití plně kvalifikovaného názvu.'
ms.date: 04/04/2019
ms.openlocfilehash: 2b88427ca92212fb4a7598447dd1a5e12061093a
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855085"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="f5308-103">Deklarace importu: `open` klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="f5308-103">Import declarations: The `open` keyword</span></span>

<span data-ttu-id="f5308-104">*Deklarace importu* určuje modul nebo obor názvů, jehož prvky můžete odkazovat bez použití plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="f5308-104">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="f5308-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5308-105">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="f5308-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5308-106">Remarks</span></span>

> [!NOTE]
> <span data-ttu-id="f5308-107">Reference k rozhraní docs.microsoft.com API pro F # není dokončená.</span><span class="sxs-lookup"><span data-stu-id="f5308-107">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="f5308-108">Pokud narazíte na nefunkční odkazy, místo toho použijte [dokumentaci základní knihovny F #](https://fsharp.github.io/fsharp-core-docs/) .</span><span class="sxs-lookup"><span data-stu-id="f5308-108">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

<span data-ttu-id="f5308-109">Odkazování na kód pomocí plně kvalifikovaného oboru názvů nebo cesty modulu pokaždé může vytvořit kód, který je těžké zapsat, číst a udržovat.</span><span class="sxs-lookup"><span data-stu-id="f5308-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="f5308-110">Místo toho můžete použít `open` klíčové slovo pro často používané moduly a obory názvů tak, aby při odkazování na člena daného modulu nebo oboru názvů mohli použít krátký tvar názvu místo plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="f5308-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="f5308-111">Toto klíčové slovo je podobné `using` klíčovému slovu v jazyce C#, `using namespace` v Visual C++ a `Imports` v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f5308-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="f5308-112">Poskytnutý modul nebo obor názvů musí být ve stejném projektu nebo v odkazovaném projektu nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="f5308-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="f5308-113">Pokud není, můžete přidat odkaz na projekt nebo použít `-reference` parametr příkazového řádku (nebo jeho zkratku `-r` ).</span><span class="sxs-lookup"><span data-stu-id="f5308-113">If it is not, you can add a reference to the project, or use the `-reference` command-line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="f5308-114">Další informace naleznete v tématu [Možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="f5308-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="f5308-115">Deklarace importu zpřístupňuje názvy v kódu, které následují po deklaraci, až do konce ohraničujícího oboru názvů, modulu nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="f5308-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="f5308-116">Při použití více deklarací importu by se měly zobrazit na samostatných řádcích.</span><span class="sxs-lookup"><span data-stu-id="f5308-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="f5308-117">Následující kód ukazuje použití `open` klíčového slova pro zjednodušení kódu.</span><span class="sxs-lookup"><span data-stu-id="f5308-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="f5308-118">Kompilátor F # negeneruje chybu ani varování, pokud dojde k nejednoznačnosti, když dojde k výskytu stejného názvu ve více než jednom otevřeném modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f5308-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="f5308-119">Když dojde k nejednoznačnosti, poskytuje jazyk F # preferovaný modul nebo obor názvů, který se nedávno otevřel.</span><span class="sxs-lookup"><span data-stu-id="f5308-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="f5308-120">Například v následujícím kódu `empty` znamená `Seq.empty` , že i když `empty` je umístěn v `List` `Seq` modulech a.</span><span class="sxs-lookup"><span data-stu-id="f5308-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="f5308-121">Proto buďte opatrní při otevírání modulů nebo oborů názvů, jako jsou `List` nebo `Seq` obsahující členy, kteří mají stejné názvy. místo toho zvažte použití kvalifikovaných názvů.</span><span class="sxs-lookup"><span data-stu-id="f5308-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="f5308-122">Měli byste se vyhnout jakékoli situaci, ve které je kód závislý na pořadí importu deklarací.</span><span class="sxs-lookup"><span data-stu-id="f5308-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="f5308-123">Obory názvů, které jsou ve výchozím nastavení otevřeny</span><span class="sxs-lookup"><span data-stu-id="f5308-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="f5308-124">Některé obory názvů jsou tak často používány v kódu F #, které jsou otevírány implicitně bez nutnosti explicitní deklarace importu.</span><span class="sxs-lookup"><span data-stu-id="f5308-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="f5308-125">V následující tabulce jsou uvedeny obory názvů, které jsou ve výchozím nastavení otevřeny.</span><span class="sxs-lookup"><span data-stu-id="f5308-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="f5308-126">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f5308-126">Namespace</span></span>|<span data-ttu-id="f5308-127">Popis</span><span class="sxs-lookup"><span data-stu-id="f5308-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="f5308-128">Obsahuje základní definice typu F # pro předdefinované typy, jako například `int` a `float` .</span><span class="sxs-lookup"><span data-stu-id="f5308-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="f5308-129">Obsahuje základní aritmetické operace, jako jsou `+` a `*` .</span><span class="sxs-lookup"><span data-stu-id="f5308-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="f5308-130">Obsahuje neměnné třídy kolekce, například `List` a `Array` .</span><span class="sxs-lookup"><span data-stu-id="f5308-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="f5308-131">Obsahuje typy pro řídicí konstrukce, jako je opožděné vyhodnocení a asynchronní pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="f5308-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="f5308-132">Obsahuje funkce pro naformátované vstupně-výstupní operace, jako je například `printf` funkce.</span><span class="sxs-lookup"><span data-stu-id="f5308-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="f5308-133">Atribut AutoOpen</span><span class="sxs-lookup"><span data-stu-id="f5308-133">AutoOpen Attribute</span></span>

<span data-ttu-id="f5308-134">Můžete použít `AutoOpen` atribut na sestavení, pokud chcete automaticky otevřít obor názvů nebo modul, když je odkazováno na sestavení.</span><span class="sxs-lookup"><span data-stu-id="f5308-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="f5308-135">Můžete také použít `AutoOpen` atribut na modul a automaticky tak otevřít tento modul, když je otevřený nadřazený modul nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f5308-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="f5308-136">Další informace naleznete v tématu [Třída Core. AutoOpenAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="f5308-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="f5308-137">RequireQualifiedAccess – atribut</span><span class="sxs-lookup"><span data-stu-id="f5308-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="f5308-138">Některé typy modulů, záznamů nebo sjednocení mohou určovat `RequireQualifiedAccess` atribut.</span><span class="sxs-lookup"><span data-stu-id="f5308-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="f5308-139">Když odkazujete na prvky těchto modulů, záznamů nebo sjednocení, je nutné použít kvalifikovaný název bez ohledu na to, zda jste zahrnuli deklaraci importu.</span><span class="sxs-lookup"><span data-stu-id="f5308-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="f5308-140">Použijete-li tento atribut strategicky u typů, které definují běžně používané názvy, můžete se vyhnout kolizím názvů a následně zvýšit odolnost kódu vůči změnám v knihovnách.</span><span class="sxs-lookup"><span data-stu-id="f5308-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="f5308-141">Další informace naleznete v tématu [Třída Core. RequireQualifiedAccessAttribute](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="f5308-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="f5308-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5308-142">See also</span></span>

- [<span data-ttu-id="f5308-143">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="f5308-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="f5308-144">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="f5308-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="f5308-145">Moduly</span><span class="sxs-lookup"><span data-stu-id="f5308-145">Modules</span></span>](modules.md)
