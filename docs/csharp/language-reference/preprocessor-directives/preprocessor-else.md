---
title: '#else - Odkaz jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 967ef38687b739ef3bea3f8923ab26bba0b6cea9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712556"
---
# <a name="else-c-reference"></a><span data-ttu-id="6ffff-102">#else (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6ffff-102">#else (C# Reference)</span></span>
<span data-ttu-id="6ffff-103">`#else`umožňuje vytvořit složené podmíněné směrnice tak, aby pokud žádný z výrazů v předchozí [#if](./preprocessor-if.md) nebo (volitelné) direktivy [#elif](./preprocessor-elif.md) vyhodnotit `true`na , kompilátor vyhodnotí všechny kód mezi `#else` a následné `#endif`.</span><span class="sxs-lookup"><span data-stu-id="6ffff-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ffff-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ffff-104">Remarks</span></span>  
 <span data-ttu-id="6ffff-105">[#endif](./preprocessor-endif.md) musí být další direktiva preprocesoru po `#else`.</span><span class="sxs-lookup"><span data-stu-id="6ffff-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="6ffff-106">Příklad použití [viz #if](./preprocessor-if.md) `#else`.</span><span class="sxs-lookup"><span data-stu-id="6ffff-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ffff-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ffff-107">See also</span></span>

- [<span data-ttu-id="6ffff-108">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6ffff-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6ffff-109">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6ffff-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6ffff-110">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6ffff-110">C# Preprocessor Directives</span></span>](./index.md)
