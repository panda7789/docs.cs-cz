---
title: Identifikátory zdrojového řádku, souboru a cesty (F#)
description: 'Další informace o použití integrovaných F # hodnoty identifikátorů, které vám umožní přístup k číslo zdrojového řádku, adresář a název souboru ve vašem kódu.'
ms.date: 05/16/2016
ms.openlocfilehash: 14f710d1412c3420ec627dc30216ba2e89f16bcd
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43865124"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="23453-103">Identifikátory zdrojového řádku, souboru a cesty</span><span class="sxs-lookup"><span data-stu-id="23453-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="23453-104">Identifikátory `__LINE__`, `__SOURCE_DIRECTORY__` a `__SOURCE_FILE__` jsou předdefinované hodnoty, které vám umožní přístup ke zdrojové řádek číslo, adresář a název souboru ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="23453-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="23453-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23453-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="23453-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23453-106">Remarks</span></span>

<span data-ttu-id="23453-107">Každá z těchto hodnot obsahuje typ `string`.</span><span class="sxs-lookup"><span data-stu-id="23453-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="23453-108">Následující tabulka shrnuje zdrojového řádku, souboru a cesty identifikátorů, které jsou k dispozici v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="23453-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="23453-109">Tyto identifikátory nejsou makra preprocesoru; jsou předdefinované hodnoty, které jsou rozpoznávány kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="23453-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="23453-110">Předdefinovaný identifikátor</span><span class="sxs-lookup"><span data-stu-id="23453-110">Predefined identifier</span></span>|<span data-ttu-id="23453-111">Popis</span><span class="sxs-lookup"><span data-stu-id="23453-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="23453-112">Aktuální číslo řádku, je vyhodnocen jako zvážení `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="23453-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="23453-113">Vyhodnotí jako aktuální úplná cesta zdrojového adresáře, vzhledem k tomu `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="23453-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="23453-114">Vyhodnotí na aktuální název zdrojového souboru a jeho cestu vzhledem k tomu `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="23453-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="23453-115">Další informace o `#line` direktiv, viz [direktivy kompilátoru](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="23453-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="23453-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="23453-116">Example</span></span>

<span data-ttu-id="23453-117">Následující příklad kódu ukazuje použití těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="23453-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="23453-118">Výstup:</span><span class="sxs-lookup"><span data-stu-id="23453-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="23453-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23453-119">See also</span></span>

- [<span data-ttu-id="23453-120">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="23453-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="23453-121">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="23453-121">F# Language Reference</span></span>](index.md)
