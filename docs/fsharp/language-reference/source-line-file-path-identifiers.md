---
title: Identifikátory zdrojového řádku, souboru a cesty (F#)
description: 'Naučte se používat integrované F # hodnoty identifikátorů, které vám umožní přístup k číslo řádku zdroje, adresář a název souboru ve svém kódu.'
ms.date: 05/16/2016
ms.openlocfilehash: 76b705fec0d951b12655edbe69e7c9212f50779d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565214"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="6124d-103">Identifikátory zdrojového řádku, souboru a cesty</span><span class="sxs-lookup"><span data-stu-id="6124d-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="6124d-104">Identifikátory `__LINE__`, `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__` jsou předdefinované hodnoty, které vám umožní přístup k zdroj řádku číslo, adresář a název souboru ve svém kódu.</span><span class="sxs-lookup"><span data-stu-id="6124d-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="6124d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6124d-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="6124d-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6124d-106">Remarks</span></span>
<span data-ttu-id="6124d-107">Všechny tyto hodnoty má typ `string`.</span><span class="sxs-lookup"><span data-stu-id="6124d-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="6124d-108">Následující tabulka shrnuje zdrojového řádku, souboru a cesty identifikátorů, které jsou k dispozici v F #.</span><span class="sxs-lookup"><span data-stu-id="6124d-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="6124d-109">Tyto identifikátory nejsou makra preprocesoru; jsou předdefinované hodnoty, které jsou rozpoznány kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="6124d-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="6124d-110">Předdefinované identifikátor</span><span class="sxs-lookup"><span data-stu-id="6124d-110">Predefined identifier</span></span>|<span data-ttu-id="6124d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="6124d-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="6124d-112">Výsledkem je aktuální číslo řádku, s `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="6124d-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="6124d-113">Vyhodnotí jako aktuální úplnou cestu zdrojového adresáře s `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="6124d-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="6124d-114">Vyhodnotí aktuální název zdrojového souboru a jeho cesty s `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="6124d-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="6124d-115">Další informace o `#line` direktivy, viz [direktivy kompilátoru](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="6124d-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="6124d-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="6124d-116">Example</span></span>

<span data-ttu-id="6124d-117">Následující příklad kódu ukazuje použití těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="6124d-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="6124d-118">Výstup:</span><span class="sxs-lookup"><span data-stu-id="6124d-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="6124d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="6124d-119">See Also</span></span>
[<span data-ttu-id="6124d-120">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="6124d-120">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="6124d-121">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="6124d-121">F# Language Reference</span></span>](index.md)
