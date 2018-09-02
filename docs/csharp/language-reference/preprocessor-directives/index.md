---
title: C# direktivy preprocesoru
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 1c0a97cabce347be0bc9367f3d090a1fc699db19
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421998"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="9be05-102">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="9be05-102">C# preprocessor directives</span></span>
<span data-ttu-id="9be05-103">Tato část obsahuje informace o následujících C# direktivy preprocesoru:</span><span class="sxs-lookup"><span data-stu-id="9be05-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="9be05-104">#if</span><span class="sxs-lookup"><span data-stu-id="9be05-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="9be05-105">#else</span><span class="sxs-lookup"><span data-stu-id="9be05-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="9be05-106">#elif</span><span class="sxs-lookup"><span data-stu-id="9be05-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="9be05-107">#endif</span><span class="sxs-lookup"><span data-stu-id="9be05-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="9be05-108">#define</span><span class="sxs-lookup"><span data-stu-id="9be05-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="9be05-109">#undef</span><span class="sxs-lookup"><span data-stu-id="9be05-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="9be05-110">#warning</span><span class="sxs-lookup"><span data-stu-id="9be05-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="9be05-111">#error</span><span class="sxs-lookup"><span data-stu-id="9be05-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="9be05-112">#line</span><span class="sxs-lookup"><span data-stu-id="9be05-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="9be05-113">#region</span><span class="sxs-lookup"><span data-stu-id="9be05-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="9be05-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="9be05-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="9be05-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="9be05-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="9be05-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="9be05-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="9be05-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="9be05-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="9be05-118">Viz témata pro další informace a příklady.</span><span class="sxs-lookup"><span data-stu-id="9be05-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="9be05-119">Ačkoli kompilátor nemá samostatné preprocesoru, direktivy popsané v této části jsou zpracovávány jako by došlo k jedné.</span><span class="sxs-lookup"><span data-stu-id="9be05-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="9be05-120">Slouží k pomáhají v podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="9be05-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="9be05-121">Na rozdíl od jazyka C a C++ direktivy nelze použít tyto direktivy makra.</span><span class="sxs-lookup"><span data-stu-id="9be05-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="9be05-122">Direktivy preprocesoru musí být pouze instrukce na řádek.</span><span class="sxs-lookup"><span data-stu-id="9be05-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="9be05-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9be05-123">See also</span></span>

- [<span data-ttu-id="9be05-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9be05-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9be05-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9be05-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
