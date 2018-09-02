---
title: '#endif (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: a652c1226f8f0c624ec8ebf0e665a4aa77ddf6f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420811"
---
# <a name="endif-c-reference"></a><span data-ttu-id="fb61a-102">#endif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fb61a-102">#endif (C# Reference)</span></span>
<span data-ttu-id="fb61a-103">`#endif` Určuje konec podmíněné direktivy, který začal [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) směrnice.</span><span class="sxs-lookup"><span data-stu-id="fb61a-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="fb61a-104">Například</span><span class="sxs-lookup"><span data-stu-id="fb61a-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="fb61a-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fb61a-105">Remarks</span></span>  
 <span data-ttu-id="fb61a-106">Podmíněnou direktivu, počínaje `#if` směrnice, musí být explicitně ukončen direktivou `#endif` směrnice.</span><span class="sxs-lookup"><span data-stu-id="fb61a-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="fb61a-107">Zobrazit [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad, jak používat `#endif`.</span><span class="sxs-lookup"><span data-stu-id="fb61a-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb61a-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb61a-108">See Also</span></span>

- [<span data-ttu-id="fb61a-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fb61a-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="fb61a-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fb61a-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fb61a-111">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="fb61a-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
