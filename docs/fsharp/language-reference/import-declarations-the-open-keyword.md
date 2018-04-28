---
title: 'Deklarace importu: Klíčové slovo open (F#)'
description: 'Další informace o deklarace importu F # a jak určit modul nebo obor názvů jehož elementy bez použití plně kvalifikovaný název, můžete odkazovat.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: ddbc1086e2adbe8dae408f4d39fd5af888d7fd5e
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="import-declarations-the-open-keyword"></a><span data-ttu-id="8b10a-103">Deklarace importu: `open` – klíčové slovo</span><span class="sxs-lookup"><span data-stu-id="8b10a-103">Import Declarations: The `open` Keyword</span></span>

> [!NOTE]
<span data-ttu-id="8b10a-104">Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="8b10a-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="8b10a-105">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="8b10a-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="8b10a-106">*Importovat deklarace* určuje modulu nebo obor názvů, jehož elementy bez použití plně kvalifikovaný název, můžete odkazovat.</span><span class="sxs-lookup"><span data-stu-id="8b10a-106">An *import declaration* specifies a module or namespace whose elements you can reference without using a fully qualified name.</span></span>


## <a name="syntax"></a><span data-ttu-id="8b10a-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b10a-107">Syntax</span></span>

```fsharp
open module-or-namespace-name
```

## <a name="remarks"></a><span data-ttu-id="8b10a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b10a-108">Remarks</span></span>
<span data-ttu-id="8b10a-109">Odkazování na kód pomocí plně kvalifikovaná cesta oboru názvů nebo modul pokaždé, když můžete vytvořit kód, který je pevný ke čtení, zápisu a údržbu.</span><span class="sxs-lookup"><span data-stu-id="8b10a-109">Referencing code by using the fully qualified namespace or module path every time can create code that is hard to write, read, and maintain.</span></span> <span data-ttu-id="8b10a-110">Místo toho můžete použít `open` – klíčové slovo pro často používané moduly a obory názvů, takže když odkazujete členem tohoto modulu nebo obor názvů, můžete použít zkratka pro název místo plně kvalifikovaný název.</span><span class="sxs-lookup"><span data-stu-id="8b10a-110">Instead, you can use the `open` keyword for frequently used modules and namespaces so that when you reference a member of that module or namespace, you can use the short form of the name instead of the fully qualified name.</span></span> <span data-ttu-id="8b10a-111">This – klíčové slovo je podobná `using` – klíčové slovo v jazyce C#, `using namespace` v jazyce Visual C++, a `Imports` v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="8b10a-111">This keyword is similar to the `using` keyword in C#, `using namespace` in Visual C++, and `Imports` in Visual Basic.</span></span>

<span data-ttu-id="8b10a-112">Modul, nebo zadat obor názvů musí být ve stejném projektu nebo v odkazované projektu nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="8b10a-112">The module or namespace provided must be in the same project or in a referenced project or assembly.</span></span> <span data-ttu-id="8b10a-113">Pokud není, můžete přidat odkaz na projekt, nebo použít `-reference` příkaz`-`možnost řádek (nebo jeho zkratkou `-r`).</span><span class="sxs-lookup"><span data-stu-id="8b10a-113">If it is not, you can add a reference to the project, or use the `-reference` command`-`line option (or its abbreviation, `-r`).</span></span> <span data-ttu-id="8b10a-114">Další informace najdete v tématu [– možnosti kompilátoru](compiler-options.md).</span><span class="sxs-lookup"><span data-stu-id="8b10a-114">For more information, see [Compiler Options](compiler-options.md).</span></span>

<span data-ttu-id="8b10a-115">Deklarace importu zpřístupňuje názvy v kódu, který následuje deklaraci do konce nadřazených obor názvů, modulu nebo souboru.</span><span class="sxs-lookup"><span data-stu-id="8b10a-115">The import declaration makes the names available in the code that follows the declaration, up to the end of the enclosing namespace, module, or file.</span></span>

<span data-ttu-id="8b10a-116">Pokud používáte více deklarace importu, by se zobrazit na samostatné řádky.</span><span class="sxs-lookup"><span data-stu-id="8b10a-116">When you use multiple import declarations, they should appear on separate lines.</span></span>

<span data-ttu-id="8b10a-117">Následující kód ukazuje použití `open` – klíčové slovo zjednodušit kód.</span><span class="sxs-lookup"><span data-stu-id="8b10a-117">The following code shows the use of the `open` keyword to simplify code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6801.fs)]

<span data-ttu-id="8b10a-118">Kompilátor jazyka F # není emitování chybě nebo upozornění při nejednoznačnosti dojít, když se stejným názvem v více než jeden otevřete modul nebo oboru názvů dojde.</span><span class="sxs-lookup"><span data-stu-id="8b10a-118">The F# compiler does not emit an error or warning when ambiguities occur when the same name occurs in more than one open module or namespace.</span></span> <span data-ttu-id="8b10a-119">Pokud dojde k nejednoznačnosti, F # dává přednost posledních otevřených modul, nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8b10a-119">When ambiguities occur, F# gives preference to the more recently opened module or namespace.</span></span> <span data-ttu-id="8b10a-120">Například v následujícím kódu `empty` znamená `Seq.empty`, i když `empty` se nachází v obou `List` a `Seq` moduly.</span><span class="sxs-lookup"><span data-stu-id="8b10a-120">For example, in the following code, `empty` means `Seq.empty`, even though `empty` is located in both the `List` and `Seq` modules.</span></span>

```fsharp
open List
open Seq
printfn "%A" empty
```

<span data-ttu-id="8b10a-121">Proto buďte opatrní při otevření moduly nebo obory názvů, jako `List` nebo `Seq` obsahující členy, kteří mají stejné názvy; místo toho zvažte použití kvalifikované názvy.</span><span class="sxs-lookup"><span data-stu-id="8b10a-121">Therefore, be careful when you open modules or namespaces such as `List` or `Seq` that contain members that have identical names; instead, consider using the qualified names.</span></span> <span data-ttu-id="8b10a-122">Neměli byste každé situaci, ve kterém je závislý na pořadí deklarace importu kód.</span><span class="sxs-lookup"><span data-stu-id="8b10a-122">You should avoid any situation in which the code is dependent upon the order of the import declarations.</span></span>


## <a name="namespaces-that-are-open-by-default"></a><span data-ttu-id="8b10a-123">Obory názvů, které jsou otevřené ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="8b10a-123">Namespaces That Are Open by Default</span></span>
<span data-ttu-id="8b10a-124">Některé obory názvů, často se používá v F # – kód, aby se implicitně otevřena bez nutnosti deklarace explicitní import.</span><span class="sxs-lookup"><span data-stu-id="8b10a-124">Some namespaces are so frequently used in F# code that they are opened implicitly without the need of an explicit import declaration.</span></span> <span data-ttu-id="8b10a-125">V následující tabulce jsou obory názvů, které jsou otevřené ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="8b10a-125">The following table shows the namespaces that are open by default.</span></span>

|<span data-ttu-id="8b10a-126">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8b10a-126">Namespace</span></span>|<span data-ttu-id="8b10a-127">Popis</span><span class="sxs-lookup"><span data-stu-id="8b10a-127">Description</span></span>|
|---------|-----------|
|`Microsoft.FSharp.Core`|<span data-ttu-id="8b10a-128">Obsahuje základní definice typů F # pro vestavěné typy, jako `int` a `float`.</span><span class="sxs-lookup"><span data-stu-id="8b10a-128">Contains basic F# type definitions for built-in types such as `int` and `float`.</span></span>|
|`Microsoft.FSharp.Core.Operators`|<span data-ttu-id="8b10a-129">Obsahuje základní aritmetické operace, jako `+` a `*`.</span><span class="sxs-lookup"><span data-stu-id="8b10a-129">Contains basic arithmetic operations such as `+` and `*`.</span></span>|
|`Microsoft.FSharp.Collections`|<span data-ttu-id="8b10a-130">Obsahuje třídy neměnné kolekce, jako `List` a `Array`.</span><span class="sxs-lookup"><span data-stu-id="8b10a-130">Contains immutable collection classes such as `List` and `Array`.</span></span>|
|`Microsoft.FSharp.Control`|<span data-ttu-id="8b10a-131">Obsahuje typy pro ovládací prvek konstrukce, jako je například opožděné vyhodnocení a asynchronní pracovní postupy.</span><span class="sxs-lookup"><span data-stu-id="8b10a-131">Contains types for control constructs such as lazy evaluation and asynchronous workflows.</span></span>|
|`Microsoft.FSharp.Text`|<span data-ttu-id="8b10a-132">Obsahuje funkce pro formátovaný vstupně-výstupní operace, jako jsou například `printf` funkce.</span><span class="sxs-lookup"><span data-stu-id="8b10a-132">Contains functions for formatted IO, such as the `printf` function.</span></span>|

## <a name="autoopen-attribute"></a><span data-ttu-id="8b10a-133">AutoOpen – atribut</span><span class="sxs-lookup"><span data-stu-id="8b10a-133">AutoOpen Attribute</span></span>
<span data-ttu-id="8b10a-134">Můžete použít `AutoOpen` atribut k sestavení, pokud chcete automaticky otevřít obor názvů nebo modul při odkazování na sestavení.</span><span class="sxs-lookup"><span data-stu-id="8b10a-134">You can apply the `AutoOpen` attribute to an assembly if you want to automatically open a namespace or module when the assembly is referenced.</span></span> <span data-ttu-id="8b10a-135">Můžete taky použít `AutoOpen` atribut modul Tenhle modul otvírat automaticky při otevření nadřazeného modulu nebo obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8b10a-135">You can also apply the `AutoOpen` attribute to a module to automatically open that module when the parent module or namespace is opened.</span></span> <span data-ttu-id="8b10a-136">Další informace najdete v tématu [Core.autoopenattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="8b10a-136">For more information, see [Core.AutoOpenAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.autoopenattribute-class-%5bfsharp%5d).</span></span>


## <a name="requirequalifiedaccess-attribute"></a><span data-ttu-id="8b10a-137">RequireQualifiedAccess – atribut</span><span class="sxs-lookup"><span data-stu-id="8b10a-137">RequireQualifiedAccess Attribute</span></span>
<span data-ttu-id="8b10a-138">Některé moduly, záznamy nebo typy union může určovat `RequireQualifiedAccess` atribut.</span><span class="sxs-lookup"><span data-stu-id="8b10a-138">Some modules, records, or union types may specify the `RequireQualifiedAccess` attribute.</span></span> <span data-ttu-id="8b10a-139">Když odkazujete elementy těchto modulů, záznamy nebo sjednocení, musíte použít kvalifikovaný název bez ohledu na to, zda obsahují deklarace importu.</span><span class="sxs-lookup"><span data-stu-id="8b10a-139">When you reference elements of those modules, records, or unions, you must use a qualified name regardless of whether you include an import declaration.</span></span> <span data-ttu-id="8b10a-140">Pokud používáte tento atribut strategicky na typy, které definují běžně používat názvy, pomoci vyhnout kolize názvů a tím provést kód pružnější změny v knihovnách.</span><span class="sxs-lookup"><span data-stu-id="8b10a-140">If you use this attribute strategically on types that define commonly used names, you help avoid name collisions and thereby make code more resilient to changes in libraries.</span></span> <span data-ttu-id="8b10a-141">Další informace najdete v tématu [Core.requirequalifiedaccessattribute – třída](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span><span class="sxs-lookup"><span data-stu-id="8b10a-141">For more information, see [Core.RequireQualifiedAccessAttribute Class](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.requirequalifiedaccessattribute-class-%5Bfsharp%5D).</span></span>


## <a name="see-also"></a><span data-ttu-id="8b10a-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="8b10a-142">See Also</span></span>
[<span data-ttu-id="8b10a-143"># Referenční dokumentace jazyka</span><span class="sxs-lookup"><span data-stu-id="8b10a-143"># Language Reference</span></span>](index.md)

[<span data-ttu-id="8b10a-144">Obory názvů</span><span class="sxs-lookup"><span data-stu-id="8b10a-144">Namespaces</span></span>](namespaces.md)

[<span data-ttu-id="8b10a-145">Moduly</span><span class="sxs-lookup"><span data-stu-id="8b10a-145">Modules</span></span>](modules.md)

