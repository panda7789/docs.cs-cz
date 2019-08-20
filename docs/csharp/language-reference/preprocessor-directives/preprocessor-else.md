---
title: '#C# odkaz else'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: d6a514f71b3526b2ffe347cdd971b81907fb0aad
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605713"
---
# <a name="else-c-reference"></a><span data-ttu-id="21fbd-102">#else (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="21fbd-102">#else (C# Reference)</span></span>
<span data-ttu-id="21fbd-103">`#else`umožňuje vytvořit složenou podmíněnou direktivu, takže pokud žádný z výrazů v předchozích [#if](./preprocessor-if.md) nebo (volitelné) [#elif](./preprocessor-elif.md) `true`direktivách vyhodnotit, kompilátor vyhodnotí veškerý kód mezi `#else` a následné `#endif`.</span><span class="sxs-lookup"><span data-stu-id="21fbd-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](./preprocessor-if.md) or (optional) [#elif](./preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21fbd-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="21fbd-104">Remarks</span></span>  
 <span data-ttu-id="21fbd-105">[#endif](./preprocessor-endif.md) musí být následující direktiva preprocesoru po `#else`.</span><span class="sxs-lookup"><span data-stu-id="21fbd-105">[#endif](./preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="21fbd-106">Příklad [](./preprocessor-if.md) použití `#else`naleznete v tématu #if.</span><span class="sxs-lookup"><span data-stu-id="21fbd-106">See [#if](./preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21fbd-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21fbd-107">See also</span></span>

- [<span data-ttu-id="21fbd-108">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="21fbd-108">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="21fbd-109">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="21fbd-109">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="21fbd-110">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="21fbd-110">C# Preprocessor Directives</span></span>](./index.md)
