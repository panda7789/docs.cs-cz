---
title: Identifikátory zdrojového řádku, souboru a cesty
description: Zjistěte, jak použít integrovaný F# hodnoty identifikátorů, které vám umožní přístup ke zdroji řádek číslo, adresář a název souboru ve vašem kódu.
ms.date: 05/16/2016
ms.openlocfilehash: 4b145fe1fe20e3d7f868558e33bab26204fb0125
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656008"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="1104b-103">Identifikátory zdrojového řádku, souboru a cesty</span><span class="sxs-lookup"><span data-stu-id="1104b-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="1104b-104">Identifikátory `__LINE__`, `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__` jsou předdefinované hodnoty, které vám umožní přístup ke zdrojové řádek číslo, adresář a název souboru ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="1104b-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="1104b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1104b-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="1104b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1104b-106">Remarks</span></span>

<span data-ttu-id="1104b-107">Každá z těchto hodnot obsahuje typ `string`.</span><span class="sxs-lookup"><span data-stu-id="1104b-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="1104b-108">Následující tabulka shrnuje zdrojového řádku, souboru a cestu identifikátory, které jsou k dispozici v F#.</span><span class="sxs-lookup"><span data-stu-id="1104b-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="1104b-109">Tyto identifikátory nejsou makra preprocesoru; jsou předdefinované hodnoty, které jsou rozpoznávány kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="1104b-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="1104b-110">Předdefinovaný identifikátor</span><span class="sxs-lookup"><span data-stu-id="1104b-110">Predefined identifier</span></span>|<span data-ttu-id="1104b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1104b-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="1104b-112">Aktuální číslo řádku, je vyhodnocen jako zvážení `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="1104b-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="1104b-113">Vyhodnotí jako aktuální úplná cesta zdrojového adresáře, vzhledem k tomu `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="1104b-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="1104b-114">Vyhodnotí na aktuální název zdrojového souboru a jeho cestu vzhledem k tomu `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="1104b-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|

<span data-ttu-id="1104b-115">Další informace o `#line` direktiv, viz [direktivy kompilátoru](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="1104b-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="1104b-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="1104b-116">Example</span></span>

<span data-ttu-id="1104b-117">Následující příklad kódu ukazuje použití těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="1104b-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="1104b-118">Výstup:</span><span class="sxs-lookup"><span data-stu-id="1104b-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="1104b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1104b-119">See also</span></span>

- [<span data-ttu-id="1104b-120">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="1104b-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="1104b-121">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="1104b-121">F# Language Reference</span></span>](index.md)
