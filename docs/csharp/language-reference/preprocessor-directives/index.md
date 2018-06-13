---
title: C# direktivy preprocesoru
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: 63a7bdb6d36794e0380ca84443926338fe926e4d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33279916"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="40431-102">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="40431-102">C# preprocessor directives</span></span>
<span data-ttu-id="40431-103">Tato část obsahuje informace o následujících C# direktivy preprocesoru:</span><span class="sxs-lookup"><span data-stu-id="40431-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="40431-104">#if</span><span class="sxs-lookup"><span data-stu-id="40431-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="40431-105">#else</span><span class="sxs-lookup"><span data-stu-id="40431-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="40431-106">#elif</span><span class="sxs-lookup"><span data-stu-id="40431-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="40431-107">#endif</span><span class="sxs-lookup"><span data-stu-id="40431-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="40431-108">#define</span><span class="sxs-lookup"><span data-stu-id="40431-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="40431-109">#undef</span><span class="sxs-lookup"><span data-stu-id="40431-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="40431-110">#warning</span><span class="sxs-lookup"><span data-stu-id="40431-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="40431-111">#error</span><span class="sxs-lookup"><span data-stu-id="40431-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="40431-112">#line</span><span class="sxs-lookup"><span data-stu-id="40431-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="40431-113">#region</span><span class="sxs-lookup"><span data-stu-id="40431-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="40431-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="40431-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="40431-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="40431-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="40431-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="40431-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="40431-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="40431-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="40431-118">V tématech jednotlivých Další informace a příklady.</span><span class="sxs-lookup"><span data-stu-id="40431-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="40431-119">I když kompilátor nemá samostatné preprocesor, direktivy popsaných v této části jsou zpracovávány jako kdyby nebyla jeden.</span><span class="sxs-lookup"><span data-stu-id="40431-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="40431-120">Používají se k vám pomůžou Podmíněná kompilace.</span><span class="sxs-lookup"><span data-stu-id="40431-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="40431-121">Na rozdíl od direktivy jazyka C a C++ nemůžete použít tyto direktivy makra.</span><span class="sxs-lookup"><span data-stu-id="40431-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="40431-122">Direktivy preprocesoru musí být pouze pokyn na řádek.</span><span class="sxs-lookup"><span data-stu-id="40431-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="40431-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="40431-123">See also</span></span>
 [<span data-ttu-id="40431-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="40431-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="40431-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="40431-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
