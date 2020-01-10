---
title: '#endif- C# reference'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712543"
---
# <a name="endif-c-reference"></a><span data-ttu-id="4846b-102">#endif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4846b-102">#endif (C# Reference)</span></span>
<span data-ttu-id="4846b-103">`#endif` určuje konec podmíněné direktivy, která začala s direktivou [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="4846b-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="4846b-104">Například</span><span class="sxs-lookup"><span data-stu-id="4846b-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="4846b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4846b-105">Remarks</span></span>  
 <span data-ttu-id="4846b-106">Podmíněná direktiva, počínaje direktivou `#if`, se musí explicitně ukončit s direktivou `#endif`.</span><span class="sxs-lookup"><span data-stu-id="4846b-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="4846b-107">Příklad použití `#endif`naleznete v tématu [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="4846b-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4846b-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4846b-108">See also</span></span>

- [<span data-ttu-id="4846b-109">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="4846b-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4846b-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4846b-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4846b-111">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="4846b-111">C# Preprocessor Directives</span></span>](./index.md)
