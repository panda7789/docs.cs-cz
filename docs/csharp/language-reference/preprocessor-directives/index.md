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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608595"
---
# <a name="c-preprocessor-directives"></a><span data-ttu-id="385b1-102">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="385b1-102">C# preprocessor directives</span></span>
<span data-ttu-id="385b1-103">Tato část obsahuje informace o následujících C# direktivách preprocesoru:</span><span class="sxs-lookup"><span data-stu-id="385b1-103">This section contains information about the following C# preprocessor directives:</span></span>

- [<span data-ttu-id="385b1-104">#if</span><span class="sxs-lookup"><span data-stu-id="385b1-104">#if</span></span>](./preprocessor-if.md)
- [<span data-ttu-id="385b1-105">#else</span><span class="sxs-lookup"><span data-stu-id="385b1-105">#else</span></span>](./preprocessor-else.md)
- [<span data-ttu-id="385b1-106">#elif</span><span class="sxs-lookup"><span data-stu-id="385b1-106">#elif</span></span>](./preprocessor-elif.md)
- [<span data-ttu-id="385b1-107">#endif</span><span class="sxs-lookup"><span data-stu-id="385b1-107">#endif</span></span>](./preprocessor-endif.md)
- [<span data-ttu-id="385b1-108">#define</span><span class="sxs-lookup"><span data-stu-id="385b1-108">#define</span></span>](./preprocessor-define.md)
- [<span data-ttu-id="385b1-109">#undef</span><span class="sxs-lookup"><span data-stu-id="385b1-109">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="385b1-110">#warning</span><span class="sxs-lookup"><span data-stu-id="385b1-110">#warning</span></span>](./preprocessor-warning.md)
- [<span data-ttu-id="385b1-111">#error</span><span class="sxs-lookup"><span data-stu-id="385b1-111">#error</span></span>](./preprocessor-error.md)
- [<span data-ttu-id="385b1-112">#line</span><span class="sxs-lookup"><span data-stu-id="385b1-112">#line</span></span>](./preprocessor-line.md)
- [<span data-ttu-id="385b1-113">#region</span><span class="sxs-lookup"><span data-stu-id="385b1-113">#region</span></span>](./preprocessor-region.md)
- [<span data-ttu-id="385b1-114">#endregion</span><span class="sxs-lookup"><span data-stu-id="385b1-114">#endregion</span></span>](./preprocessor-endregion.md)
- [<span data-ttu-id="385b1-115">#pragma</span><span class="sxs-lookup"><span data-stu-id="385b1-115">#pragma</span></span>](./preprocessor-pragma.md)
- [<span data-ttu-id="385b1-116">#pragma warning</span><span class="sxs-lookup"><span data-stu-id="385b1-116">#pragma warning</span></span>](./preprocessor-pragma-warning.md)
- [<span data-ttu-id="385b1-117">#pragma checksum</span><span class="sxs-lookup"><span data-stu-id="385b1-117">#pragma checksum</span></span>](./preprocessor-pragma-checksum.md)

<span data-ttu-id="385b1-118">Další informace a příklady najdete v jednotlivých tématech.</span><span class="sxs-lookup"><span data-stu-id="385b1-118">See the individual topics for more information and examples.</span></span>

<span data-ttu-id="385b1-119">I když kompilátor nemá samostatný preprocesor, směrnice popsané v této části jsou zpracovávány, jako kdyby existovala jedna z nich.</span><span class="sxs-lookup"><span data-stu-id="385b1-119">Although the compiler doesn't have a separate preprocessor, the directives described in this section are processed as if there were one.</span></span> <span data-ttu-id="385b1-120">Používají se k nápovědě při podmíněné kompilaci.</span><span class="sxs-lookup"><span data-stu-id="385b1-120">They are used to help in conditional compilation.</span></span> <span data-ttu-id="385b1-121">Na rozdíl od jazyka C++ C a direktiv nemůžete pomocí těchto direktiv vytvořit makra.</span><span class="sxs-lookup"><span data-stu-id="385b1-121">Unlike C and C++ directives, you cannot use these directives to create macros.</span></span>

<span data-ttu-id="385b1-122">Direktiva preprocesoru musí být jedinou instrukcí na řádku.</span><span class="sxs-lookup"><span data-stu-id="385b1-122">A preprocessor directive must be the only instruction on a line.</span></span>

## <a name="see-also"></a><span data-ttu-id="385b1-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="385b1-123">See also</span></span>

- [<span data-ttu-id="385b1-124">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="385b1-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="385b1-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="385b1-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
