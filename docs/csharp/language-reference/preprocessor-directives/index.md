---
title: C# direktivy preprocesoru
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6378c8df794a4ee75e7b5ca283b18b228ba46383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="4d9fd-102">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="4d9fd-102">C# preprocessor directives</span></span>
<span data-ttu-id="4d9fd-103">Tato část obsahuje informace o následujících C# direktivy preprocesoru:</span><span class="sxs-lookup"><span data-stu-id="4d9fd-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="4d9fd-104">#if</span><span class="sxs-lookup"><span data-stu-id="4d9fd-104">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
- [<span data-ttu-id="4d9fd-105">#else</span><span class="sxs-lookup"><span data-stu-id="4d9fd-105">#else</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md)
- [<span data-ttu-id="4d9fd-106">#elif</span><span class="sxs-lookup"><span data-stu-id="4d9fd-106">#elif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md)
- [<span data-ttu-id="4d9fd-107">#endif</span><span class="sxs-lookup"><span data-stu-id="4d9fd-107">#endif</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)
- [<span data-ttu-id="4d9fd-108">#define</span><span class="sxs-lookup"><span data-stu-id="4d9fd-108">#define</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md)
- [<span data-ttu-id="4d9fd-109">#undef</span><span class="sxs-lookup"><span data-stu-id="4d9fd-109">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)
- [<span data-ttu-id="4d9fd-110">#warning</span><span class="sxs-lookup"><span data-stu-id="4d9fd-110">#warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md)
- [<span data-ttu-id="4d9fd-111">#error</span><span class="sxs-lookup"><span data-stu-id="4d9fd-111">#error</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md)
- [<span data-ttu-id="4d9fd-112">#line</span><span class="sxs-lookup"><span data-stu-id="4d9fd-112">#line</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-line.md)
- [<span data-ttu-id="4d9fd-113">#region</span><span class="sxs-lookup"><span data-stu-id="4d9fd-113">#region</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-region.md)
- [<span data-ttu-id="4d9fd-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="4d9fd-114">#endregion</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md)
- [<span data-ttu-id="4d9fd-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="4d9fd-115">#pragma</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma.md)
- [<span data-ttu-id="4d9fd-116">#pragma – upozornění</span><span class="sxs-lookup"><span data-stu-id="4d9fd-116">#pragma warning</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md)
- [<span data-ttu-id="4d9fd-117">#pragma – kontrolní součet</span><span class="sxs-lookup"><span data-stu-id="4d9fd-117">#pragma checksum</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-checksum.md)

<span data-ttu-id="4d9fd-118">V tématech jednotlivých Další informace a příklady.</span><span class="sxs-lookup"><span data-stu-id="4d9fd-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="4d9fd-119">I když kompilátor nemá samostatné preprocesor, direktivy popsaných v této části jsou zpracovávány jako kdyby nebyla jeden.</span><span class="sxs-lookup"><span data-stu-id="4d9fd-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="4d9fd-120">Používají se k vám pomůžou Podmíněná kompilace.</span><span class="sxs-lookup"><span data-stu-id="4d9fd-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="4d9fd-121">Na rozdíl od direktivy jazyka C a C++ nemůžete použít tyto direktivy makra.</span><span class="sxs-lookup"><span data-stu-id="4d9fd-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="4d9fd-122">Direktivy preprocesoru musí být pouze pokyn na řádek.</span><span class="sxs-lookup"><span data-stu-id="4d9fd-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d9fd-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d9fd-123">See also</span></span>
 [<span data-ttu-id="4d9fd-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4d9fd-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4d9fd-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="4d9fd-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
