---
title: "Identifikátory zdrojového řádku, souboru a cesty (F#)"
description: "Naučte se používat integrované F # hodnoty identifikátorů, které vám umožní přístup k číslo řádku zdroje, adresář a název souboru ve svém kódu."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4cfe7439-275c-4d08-980b-784e240bbf29
ms.openlocfilehash: 44cc0914226c120f2b877ce3decd25caa6817eec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="5955c-104">Identifikátory zdrojového řádku, souboru a cesty</span><span class="sxs-lookup"><span data-stu-id="5955c-104">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="5955c-105">Identifikátory `__LINE__`, `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__` jsou předdefinované hodnoty, které vám umožní přístup k zdroj řádku číslo, adresář a název souboru ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="5955c-105">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="5955c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5955c-106">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="5955c-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5955c-107">Remarks</span></span>
<span data-ttu-id="5955c-108">Všechny tyto hodnoty má typ `string`.</span><span class="sxs-lookup"><span data-stu-id="5955c-108">Each of these values has type `string`.</span></span>

<span data-ttu-id="5955c-109">Následující tabulka shrnuje zdrojového řádku, souboru a cesty identifikátorů, které jsou k dispozici v F #.</span><span class="sxs-lookup"><span data-stu-id="5955c-109">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="5955c-110">Tyto identifikátory nejsou makra preprocesoru; jsou předdefinované hodnoty, které jsou rozpoznány kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="5955c-110">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="5955c-111">Předdefinované identifikátor</span><span class="sxs-lookup"><span data-stu-id="5955c-111">Predefined identifier</span></span>|<span data-ttu-id="5955c-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5955c-112">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="5955c-113">Výsledkem je aktuální číslo řádku, s `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="5955c-113">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="5955c-114">Vyhodnotí jako aktuální úplnou cestu zdrojového adresáře s `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="5955c-114">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="5955c-115">Vyhodnotí aktuální název zdrojového souboru a jeho cesty s `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="5955c-115">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="5955c-116">Další informace o `#line` direktivy, viz [direktivy kompilátoru](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="5955c-116">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="5955c-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="5955c-117">Example</span></span>

<span data-ttu-id="5955c-118">Následující příklad kódu ukazuje použití těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="5955c-118">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="5955c-119">Výstup:</span><span class="sxs-lookup"><span data-stu-id="5955c-119">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="5955c-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="5955c-120">See Also</span></span>
[<span data-ttu-id="5955c-121">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="5955c-121">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="5955c-122">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="5955c-122">F# Language Reference</span></span>](index.md)
