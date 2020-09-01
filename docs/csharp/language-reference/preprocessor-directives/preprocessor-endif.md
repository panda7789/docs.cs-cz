---
description: '#endif – Referenční dokumentace jazyka C#'
title: '#endif – Referenční dokumentace jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 8068a6e437145178fd5c88763c86692a8700c349
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138160"
---
# <a name="endif-c-reference"></a><span data-ttu-id="a9f01-103">#endif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a9f01-103">#endif (C# Reference)</span></span>
<span data-ttu-id="a9f01-104">`#endif` určuje konec podmíněné direktivy, která začala s direktivou [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="a9f01-104">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="a9f01-105">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a9f01-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="a9f01-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9f01-106">Remarks</span></span>  
 <span data-ttu-id="a9f01-107">Podmíněná direktiva, která začíná `#if` direktivou, musí být explicitně ukončena `#endif` direktivou.</span><span class="sxs-lookup"><span data-stu-id="a9f01-107">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="a9f01-108">Příklad použití naleznete v tématu [#if](./preprocessor-if.md) `#endif` .</span><span class="sxs-lookup"><span data-stu-id="a9f01-108">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9f01-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9f01-109">See also</span></span>

- [<span data-ttu-id="a9f01-110">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a9f01-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a9f01-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a9f01-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a9f01-112">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="a9f01-112">C# Preprocessor Directives</span></span>](./index.md)
