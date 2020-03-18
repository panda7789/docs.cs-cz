---
title: '#endif - C# Reference'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712543"
---
# <a name="endif-c-reference"></a><span data-ttu-id="8e5ba-102">#endif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8e5ba-102">#endif (C# Reference)</span></span>
<span data-ttu-id="8e5ba-103">`#endif`určuje konec podmíněné směrnice, která začala [#if](./preprocessor-if.md) direktivou.</span><span class="sxs-lookup"><span data-stu-id="8e5ba-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="8e5ba-104">Například:</span><span class="sxs-lookup"><span data-stu-id="8e5ba-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="8e5ba-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8e5ba-105">Remarks</span></span>  
 <span data-ttu-id="8e5ba-106">Podmíněná směrnice, počínaje `#if` směrnice, musí být explicitně ukončena direktivou. `#endif`</span><span class="sxs-lookup"><span data-stu-id="8e5ba-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="8e5ba-107">Příklad použití [viz #if](./preprocessor-if.md) `#endif`.</span><span class="sxs-lookup"><span data-stu-id="8e5ba-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e5ba-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e5ba-108">See also</span></span>

- [<span data-ttu-id="8e5ba-109">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e5ba-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8e5ba-110">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e5ba-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8e5ba-111">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e5ba-111">C# Preprocessor Directives</span></span>](./index.md)
