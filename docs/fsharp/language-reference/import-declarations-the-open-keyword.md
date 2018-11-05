---
title: 'Deklarace importu: Klíčové slovo open (F#)'
description: Další informace o deklarace importu F# a jak určit modulu nebo oboru názvů jejíž prvky, můžete využít bez použití plně kvalifikovaného názvu.
ms.date: 05/16/2016
ms.openlocfilehash: 8cae4b4f5418689bfb0933b7db4ec23a313d5ed8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "46586620"
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="e0c17-103">Deklarace importu: `open` – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="e0c17-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
<span data-ttu-id="e0c17-104">Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="e0c17-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="e0c17-105">Reference k rozhraní API webu docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="e0c17-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="e0c17-106">*Deklarace importu* Určuje modul nebo obor názvů, jehož prvky, můžete využít bez použití plně kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="e0c17-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>

## <a name="syntax"></a><span data-ttu-id="e0c17-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0c17-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="e0c17-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0c17-108">Remarks</span></span>

<span data-ttu-id="e0c17-109">Odkazování na kódu s použitím plně kvalifikovanou cestu k oboru názvů nebo modulu pokaždé, když můžete vytvořit kód, který je těžké ke čtení, zápisu a udržovat.</span><span class="sxs-lookup"><span data-stu-id="e0c17-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="e0c17-110">Místo toho můžete použít `open` – klíčové slovo pro často používané modulů a oborů názvů tak, aby při odkazování na člena z tohoto modulu nebo oboru názvů, krátkou formu názvu můžete používat místo plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="e0c17-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="e0c17-111">Toto klíčové slovo je podobný `using` – klíčové slovo v jazyce C#, `using namespace` v jazyce Visual C++ a `Imports` v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e0c17-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="e0c17-112">Modul nebo obor názvů k dispozici musí být ve stejném projektu nebo v odkazovaném projektu nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0c17-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="e0c17-113">Pokud není, můžete přidat odkaz na projekt, nebo použít `-reference` příkaz`-`možnost příkazového řádku (nebo jeho zkratku `-r`).</span><span class="sxs-lookup"><span data-stu-id="e0c17-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="e0c17-114">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="e0c17-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="e0c17-115">Deklarace importu zpřístupňuje názvy v kódu, který následuje deklaraci, až do ukončení nadřazeného oboru názvů, modul nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="e0c17-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="e0c17-116">Pokud používáte více deklarace importu, by se zobrazit na samostatných řádcích.</span><span class="sxs-lookup"><span data-stu-id="e0c17-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="e0c17-117">Následující kód ukazuje použití `open` – klíčové slovo pro zjednodušení kódu.</span><span class="sxs-lookup"><span data-stu-id="e0c17-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="e0c17-118">Kompilátor F# negeneruje chybu nebo upozornění, když dojde k nejasnostem, dojde ve více než jeden otevřít modul nebo obor názvů se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="e0c17-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="e0c17-119">Pokud dojde k nejasnostem, F# dává přednost naposledy otevřeným modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e0c17-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="e0c17-120">Například v následujícím kódu `empty` znamená, že `Seq.empty`, i když `empty` se nachází v obou `List` a `Seq` moduly.</span><span class="sxs-lookup"><span data-stu-id="e0c17-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="e0c17-121">Proto buďte opatrní při otevření modulů nebo oborů názvů, jako `List` nebo `Seq` , které obsahují členy, které mají stejné názvy; místo toho zvažte použití kvalifikované názvy.</span><span class="sxs-lookup"><span data-stu-id="e0c17-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="e0c17-122">Neměli byste každé situaci, ve kterém je kód závisí na pořadí deklarace importu.</span><span class="sxs-lookup"><span data-stu-id="e0c17-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>

## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="e0c17-123">Obory názvů, které jsou spuštěné ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="e0c17-123">Namespaces That Are Open by Default</span></span>

<span data-ttu-id="e0c17-124">Některé obory názvů často slouží v kódu F#, implicitně jsou otevřené bez nutnosti deklarace explicitní importu.</span><span class="sxs-lookup"><span data-stu-id="e0c17-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="e0c17-125">V následující tabulce jsou uvedeny obory názvů, které jsou spuštěné ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e0c17-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="e0c17-126">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e0c17-126">Namespace</span></span>|<span data-ttu-id="e0c17-127">Popis</span><span class="sxs-lookup"><span data-stu-id="e0c17-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="e0c17-128">Obsahuje základní definice typů F# pro předdefinované typy jako `int` a `float`.</span><span class="sxs-lookup"><span data-stu-id="e0c17-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="e0c17-129">Obsahuje základní aritmetické operace, například `+` a `*`.</span><span class="sxs-lookup"><span data-stu-id="e0c17-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="e0c17-130">Neměnné kolekce tříd obsahuje například `List` a `Array`.</span><span class="sxs-lookup"><span data-stu-id="e0c17-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="e0c17-131">Obsahuje typy pro ovládací prvek konstrukce, jako je například opožděné vyhodnocení a asynchronní pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="e0c17-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="e0c17-132">Obsahuje funkce pro formátovaný vstupně-výstupních operací, jako `printf` funkce.</span><span class="sxs-lookup"><span data-stu-id="e0c17-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="e0c17-133">AutoOpen – atribut</span><span class="sxs-lookup"><span data-stu-id="e0c17-133">AutoOpen Attribute</span></span>

<span data-ttu-id="e0c17-134">Můžete použít `AutoOpen` atributu k sestavení, pokud chcete automaticky otevře oboru názvů nebo modulu při odkazování sestavení.</span><span class="sxs-lookup"><span data-stu-id="e0c17-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="e0c17-135">Můžete také použít `AutoOpen` atribut modulu, který automaticky otevře že modulu při otevření nadřazené modulu nebo oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e0c17-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="e0c17-136">Další informace najdete v tématu [Core.autoopenattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="e0c17-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>

## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="e0c17-137">RequireQualifiedAccess – atribut</span><span class="sxs-lookup"><span data-stu-id="e0c17-137">RequireQualifiedAccess Attribute</span></span>

<span data-ttu-id="e0c17-138">Některé moduly, záznamy nebo typy sjednocení může zadat `RequireQualifiedAccess` atribut.</span><span class="sxs-lookup"><span data-stu-id="e0c17-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="e0c17-139">Při odkazování na prvky tyto moduly, záznamy nebo sjednocení, musíte použít kvalifikovaného názvu bez ohledu na to, jestli zahrnují deklarace importu.</span><span class="sxs-lookup"><span data-stu-id="e0c17-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="e0c17-140">Pokud použijete tento atribut strategicky na typy, které definují běžně používají názvy, pomáhají vyhnete kolize názvů a tím kód odolnější vůči změnám v knihovnách.</span><span class="sxs-lookup"><span data-stu-id="e0c17-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="e0c17-141">Další informace najdete v tématu [Core.requirequalifiedaccessattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="e0c17-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0c17-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0c17-142">See also</span></span>

- [<span data-ttu-id="e0c17-143"># Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="e0c17-143"># Language Reference</span></span>](index.md)
- [<span data-ttu-id="e0c17-144">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="e0c17-144">Namespaces</span></span>](namespaces.md)
- [<span data-ttu-id="e0c17-145">Moduly</span><span class="sxs-lookup"><span data-stu-id="e0c17-145">Modules</span></span>](modules.md)
