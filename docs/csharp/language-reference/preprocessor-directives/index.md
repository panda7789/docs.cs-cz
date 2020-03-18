---
title: Direktivy preprocesoru jazyka C#
ms.date: 07/20/2015
f1_keywords:
- cs.preprocessor
helpviewer_keywords:
- preprocessor directives [C#]
- keywords [C#], preprocessor directives
ms.assetid: f2406090-b244-4f7e-ab72-3698fefed724
ms.openlocfilehash: f63ba3e0bd89a88ad04b14c2f359a8cde65e8f12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "69608595"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="0d2bc-102">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d2bc-102">C# preprocessor directives</span></span>
<span data-ttu-id="0d2bc-103">Tato část obsahuje informace o následujících direktivách preprocesoru jazyka C#:</span><span class="sxs-lookup"><span data-stu-id="0d2bc-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="0d2bc-104">#if</span><span class="sxs-lookup"><span data-stu-id="0d2bc-104">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="0d2bc-105">#else</span><span class="sxs-lookup"><span data-stu-id="0d2bc-105">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="0d2bc-106">#elif</span><span class="sxs-lookup"><span data-stu-id="0d2bc-106">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="0d2bc-107">#endif</span><span class="sxs-lookup"><span data-stu-id="0d2bc-107">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="0d2bc-108">#define</span><span class="sxs-lookup"><span data-stu-id="0d2bc-108">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="0d2bc-109">#undef</span><span class="sxs-lookup"><span data-stu-id="0d2bc-109">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="0d2bc-110">#warning</span><span class="sxs-lookup"><span data-stu-id="0d2bc-110">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="0d2bc-111">#error</span><span class="sxs-lookup"><span data-stu-id="0d2bc-111">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="0d2bc-112">#line</span><span class="sxs-lookup"><span data-stu-id="0d2bc-112">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="0d2bc-113">#region</span><span class="sxs-lookup"><span data-stu-id="0d2bc-113">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="0d2bc-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="0d2bc-114">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="0d2bc-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="0d2bc-115">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="0d2bc-116">#pragma varování</span><span class="sxs-lookup"><span data-stu-id="0d2bc-116">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="0d2bc-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="0d2bc-117">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="0d2bc-118">Další informace a příklady najdete v jednotlivých tématech.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="0d2bc-119">I když kompilátor nemá samostatný preprocesor, direktivy popsané v této části jsou zpracovány, jako by byl jeden.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="0d2bc-120">Používají se k pomoci v podmíněné kompilaci.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="0d2bc-121">Na rozdíl od direktiv C a C++ nelze použít tyto direktivy k vytvoření maker.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="0d2bc-122">Preprocesor směrnice musí být pouze instrukce na řádku.</span><span class="sxs-lookup"><span data-stu-id="0d2bc-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d2bc-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d2bc-123">See also</span></span>

- [<span data-ttu-id="0d2bc-124">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d2bc-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0d2bc-125">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0d2bc-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
