---
title: '#C# odkaz else'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 967ef38687b739ef3bea3f8923ab26bba0b6cea9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712556"
---
# <a name="else-c-reference"></a><span data-ttu-id="68c41-102">#else (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="68c41-102">#else (C# Reference)</span></span>
<span data-ttu-id="68c41-103">`#else` umožňuje vytvořit složenou podmíněnou direktivu, takže pokud žádné výrazy v předchozích [#if](./preprocessor-if.md) nebo (volitelné) [#elif](./preprocessor-elif.md) direktivy vyhodnotí na `true`, kompilátor vyhodnotí veškerý kód mezi `#else`y a následnými `#endif`y.</span><span class="sxs-lookup"><span data-stu-id="68c41-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68c41-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68c41-104">Remarks</span></span>  
 <span data-ttu-id="68c41-105">[#endif](./preprocessor-endif.md) musí být následující direktiva preprocesoru po `#else`.</span><span class="sxs-lookup"><span data-stu-id="68c41-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="68c41-106">Příklad použití `#else`naleznete v tématu [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="68c41-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c41-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="68c41-107">See also</span></span>

- [<span data-ttu-id="68c41-108">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="68c41-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="68c41-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="68c41-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="68c41-110">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="68c41-110">C# Preprocessor Directives</span></span>](./index.md)
