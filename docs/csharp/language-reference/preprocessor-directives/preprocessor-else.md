---
description: '#Reference else-C#'
title: '#Reference else-C#'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: fb1a9f30a42c78b5c4c7323ec213ab8c20b9bb76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138173"
---
# <a name="else-c-reference"></a><span data-ttu-id="3067b-103">#else (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3067b-103">#else (C# Reference)</span></span>
<span data-ttu-id="3067b-104">`#else` umožňuje vytvořit složenou podmíněnou direktivu, takže pokud žádný z výrazů v předchozích [#if](./preprocessor-if.md) nebo (volitelné) [#elif](./preprocessor-elif.md) direktivách vyhodnotit `true` , kompilátor vyhodnotí celý kód mezi `#else` a následnými `#endif` .</span><span class="sxs-lookup"><span data-stu-id="3067b-104">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3067b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3067b-105">Remarks</span></span>  
 <span data-ttu-id="3067b-106">[#endif](./preprocessor-endif.md) musí být následující direktiva preprocesoru po `#else` .</span><span class="sxs-lookup"><span data-stu-id="3067b-106">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="3067b-107">Příklad použití naleznete v tématu [#if](./preprocessor-if.md) `#else` .</span><span class="sxs-lookup"><span data-stu-id="3067b-107">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3067b-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="3067b-108">See also</span></span>

- [<span data-ttu-id="3067b-109">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3067b-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3067b-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="3067b-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3067b-111">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="3067b-111">C# Preprocessor Directives</span></span>](./index.md)
