---
title: 'Deklarace importu: Klíčové slovo open'
description: Další informace o F# import, deklarace a jak určit modul nebo obor názvů, jehož prvky, můžete využít bez použití plně kvalifikovaného názvu.
ms.date: 04/04/2019
ms.openlocfilehash: ad64190c3243c57a185f3b864270fca80590f079
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59054998"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="e3bf8-103">Deklarace importu: `open` – Klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="e3bf8-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
> <span data-ttu-id="e3bf8-104">Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="e3bf8-105">Reference k rozhraní API webu docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="e3bf8-106">*Deklarace importu* Určuje modul nebo obor názvů, jehož prvky, můžete využít bez použití plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="e3bf8-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e3bf8-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="e3bf8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e3bf8-108">Remarks</span></span>

<span data-ttu-id="e3bf8-109">Odkazování na kódu s použitím plně kvalifikovanou cestu k oboru názvů nebo modulu pokaždé, když můžete vytvořit kód, který je těžké ke čtení, zápisu a udržovat.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="e3bf8-110">Místo toho můžete použít `open` – klíčové slovo pro často používané modulů a oborů názvů tak, aby při odkazování na člena z tohoto modulu nebo oboru názvů, krátkou formu názvu můžete používat místo plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="e3bf8-111">Toto klíčové slovo je podobný `using` – klíčové slovo v jazyce C#, `using namespace` v jazyce Visual C++ a `Imports` v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="e3bf8-112">Modul nebo obor názvů k dispozici musí být ve stejném projektu nebo v odkazovaném projektu nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="e3bf8-113">Pokud není, můžete přidat odkaz na projekt, nebo použít `-reference` příkaz`-`možnost příkazového řádku (nebo jeho zkratku `-r`).</span><span class="sxs-lookup"><span data-stu-id="e3bf8-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="e3bf8-114">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="e3bf8-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="e3bf8-115">Deklarace importu zpřístupňuje názvy v kódu, který následuje deklaraci, až do ukončení nadřazeného oboru názvů, modul nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="e3bf8-116">Pokud používáte více deklarace importu, by se zobrazit na samostatných řádcích.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="e3bf8-117">Následující kód ukazuje použití `open` – klíčové slovo pro zjednodušení kódu.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="e3bf8-118">F# Kompilátor negeneruje chybu nebo upozornění při výskytu nejednoznačnosti dojde ve více než jeden otevřít modul nebo obor názvů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="e3bf8-119">Pokud dojde k nejasnostem, F# dává přednost naposledy otevřeným modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="e3bf8-120">Například v následujícím kódu `empty` znamená, že `Seq.empty`, i když `empty` se nachází v obou `List` a `Seq` moduly.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="e3bf8-121">Proto buďte opatrní při otevření modulů nebo oborů názvů, jako `List` nebo `Seq` , které obsahují členy, které mají stejné názvy; místo toho zvažte použití kvalifikované názvy.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="e3bf8-122">Neměli byste každé situaci, ve kterém je kód závisí na pořadí deklarace importu.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="e3bf8-123">Obory názvů, které jsou spuštěné ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="e3bf8-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="e3bf8-124">Některé obory názvů často slouží v F# kód jejich otevření implicitně bez nutnosti deklarace explicitní importu.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="e3bf8-125">V následující tabulce jsou uvedeny obory názvů, které jsou spuštěné ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="e3bf8-126">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e3bf8-126">Namespace</span></span>|<span data-ttu-id="e3bf8-127">Popis</span><span class="sxs-lookup"><span data-stu-id="e3bf8-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="e3bf8-128">Obsahuje základní F# definice pro předdefinované typy obecných typů, jako `int` a `float`.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="e3bf8-129">Obsahuje základní aritmetické operace, například `+` a `*`.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="e3bf8-130">Neměnné kolekce tříd obsahuje například `List` a `Array`.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="e3bf8-131">Obsahuje typy pro ovládací prvek konstrukce, jako je například opožděné vyhodnocení a asynchronní pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="e3bf8-132">Obsahuje funkce pro formátovaný vstupně-výstupních operací, jako `printf` funkce.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="e3bf8-133">AutoOpen – atribut</span><span class="sxs-lookup"><span data-stu-id="e3bf8-133">AutoOpen Attribute</span></span>

<span data-ttu-id="e3bf8-134">Můžete použít `AutoOpen` atributu k sestavení, pokud chcete automaticky otevře oboru názvů nebo modulu při odkazování sestavení.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="e3bf8-135">Můžete také použít `AutoOpen` atribut modulu, který automaticky otevře že modulu při otevření nadřazené modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="e3bf8-136">Další informace najdete v tématu [Core.autoopenattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="e3bf8-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="e3bf8-137">RequireQualifiedAccess – atribut</span><span class="sxs-lookup"><span data-stu-id="e3bf8-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="e3bf8-138">Některé moduly, záznamy nebo typy sjednocení může zadat `RequireQualifiedAccess` atribut.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="e3bf8-139">Při odkazování na prvky tyto moduly, záznamy nebo sjednocení, musíte použít kvalifikovaného názvu bez ohledu na to, jestli zahrnují deklarace importu.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="e3bf8-140">Pokud použijete tento atribut strategicky na typy, které definují běžně používají názvy, pomáhají vyhnete kolize názvů a tím kód odolnější vůči změnám v knihovnách.</span><span class="sxs-lookup"><span data-stu-id="e3bf8-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="e3bf8-141">Další informace najdete v tématu [Core.requirequalifiedaccessattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="e3bf8-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="e3bf8-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3bf8-142">See also</span></span>

- [<span data-ttu-id="e3bf8-143">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="e3bf8-143">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e3bf8-144">Jmenné prostory</span><span class="sxs-lookup"><span data-stu-id="e3bf8-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="e3bf8-145">Moduly</span><span class="sxs-lookup"><span data-stu-id="e3bf8-145">Modules</span></span>](modules.md)
