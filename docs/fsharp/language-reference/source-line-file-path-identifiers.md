---
title: Identifikátory zdrojového řádku, souboru a cesty
description: Naučte se používat předdefinované hodnoty F# identifikátorů, které vám umožní přístup ke zdrojovému číslu, adresáři a názvu souboru ve vašem kódu.
ms.date: 05/16/2016
ms.openlocfilehash: 5ff36210edc75370f8baf9ee7be057f3ac0c3979
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627112"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="01237-103">Identifikátory zdrojového řádku, souboru a cesty</span><span class="sxs-lookup"><span data-stu-id="01237-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="01237-104">Identifikátory `__LINE__` `__SOURCE_DIRECTORY__` a jsoupředdefinovanéhodnoty,kterévámumožnípřístupkezdrojovémučísluřádku,adresářianázvusouboruvevašemkódu.`__SOURCE_FILE__`</span><span class="sxs-lookup"><span data-stu-id="01237-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="01237-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01237-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="01237-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01237-106">Remarks</span></span>

<span data-ttu-id="01237-107">Každá z těchto hodnot je typu `string`.</span><span class="sxs-lookup"><span data-stu-id="01237-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="01237-108">Následující tabulka shrnuje identifikátory zdrojového řádku, souboru a cesty, které jsou k dispozici v F#.</span><span class="sxs-lookup"><span data-stu-id="01237-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="01237-109">Tyto identifikátory neobsahují makra preprocesoru; jsou to předdefinované hodnoty, které kompilátor rozpozná.</span><span class="sxs-lookup"><span data-stu-id="01237-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="01237-110">Předdefinovaný identifikátor</span><span class="sxs-lookup"><span data-stu-id="01237-110">Predefined identifier</span></span>|<span data-ttu-id="01237-111">Popis</span><span class="sxs-lookup"><span data-stu-id="01237-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="01237-112">Vyhodnotí na aktuální číslo řádku a zváží `#line` direktivy.</span><span class="sxs-lookup"><span data-stu-id="01237-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="01237-113">Vyhodnotí na aktuální úplnou cestu ke zdrojovému adresáři, který `#line` zvažuje direktivy.</span><span class="sxs-lookup"><span data-stu-id="01237-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="01237-114">Vyhodnotí na aktuální název zdrojového souboru bez cesty, kde se `#line` dotýkají direktiv.</span><span class="sxs-lookup"><span data-stu-id="01237-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="01237-115">Další informace o `#line` direktivě naleznete v tématu [direktivy kompilátoru](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="01237-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="01237-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="01237-116">Example</span></span>

<span data-ttu-id="01237-117">Následující příklad kódu ukazuje použití těchto hodnot.</span><span class="sxs-lookup"><span data-stu-id="01237-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="01237-118">Výstup:</span><span class="sxs-lookup"><span data-stu-id="01237-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="01237-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01237-119">See also</span></span>

- [<span data-ttu-id="01237-120">Direktivy kompilátoru</span><span class="sxs-lookup"><span data-stu-id="01237-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="01237-121">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="01237-121">F# Language Reference</span></span>](index.md)
