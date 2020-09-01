---
description: Direktivy preprocesoru jazyka C#
title: Direktivy preprocesoru jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: a7ffca8b39f1bd9f05193bccbb6d90e67fa262c9
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132362"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="73621-103">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73621-103">C# preprocessor directives</span></span>
<span data-ttu-id="73621-104">Tato část obsahuje informace o následujících direktivách preprocesoru jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="73621-104">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="73621-105">#if</span><span class="sxs-lookup"><span data-stu-id="73621-105">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="73621-106">#else</span><span class="sxs-lookup"><span data-stu-id="73621-106">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="73621-107">#elif</span><span class="sxs-lookup"><span data-stu-id="73621-107">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="73621-108">#endif</span><span class="sxs-lookup"><span data-stu-id="73621-108">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="73621-109">#define</span><span class="sxs-lookup"><span data-stu-id="73621-109">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="73621-110">#undef</span><span class="sxs-lookup"><span data-stu-id="73621-110">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="73621-111">#warning</span><span class="sxs-lookup"><span data-stu-id="73621-111">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="73621-112">#error</span><span class="sxs-lookup"><span data-stu-id="73621-112">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="73621-113">#line</span><span class="sxs-lookup"><span data-stu-id="73621-113">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="73621-114">#region</span><span class="sxs-lookup"><span data-stu-id="73621-114">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="73621-115">#endregion</span><span class="sxs-lookup"><span data-stu-id="73621-115">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="73621-116">#pragma</span><span class="sxs-lookup"><span data-stu-id="73621-116">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="73621-117">upozornění #pragma</span><span class="sxs-lookup"><span data-stu-id="73621-117">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="73621-118">kontrolní součet #pragma</span><span class="sxs-lookup"><span data-stu-id="73621-118">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="73621-119">Další informace a příklady najdete v jednotlivých tématech.</span><span class="sxs-lookup"><span data-stu-id="73621-119">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="73621-120">I když kompilátor nemá samostatný preprocesor, směrnice popsané v této části jsou zpracovávány, jako kdyby existovala jedna z nich.</span><span class="sxs-lookup"><span data-stu-id="73621-120">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="73621-121">Používají se k nápovědě při podmíněné kompilaci.</span><span class="sxs-lookup"><span data-stu-id="73621-121">They are used to help in conditional compilation.</span></span> <span data-ttu-id="73621-122">Na rozdíl od direktiv jazyka C a C++ nemůžete pomocí těchto direktiv vytvořit makra.</span><span class="sxs-lookup"><span data-stu-id="73621-122">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="73621-123">Direktiva preprocesoru musí být jedinou instrukcí na řádku.</span><span class="sxs-lookup"><span data-stu-id="73621-123">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="73621-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="73621-124">See also</span></span>

- [<span data-ttu-id="73621-125">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="73621-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="73621-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="73621-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
