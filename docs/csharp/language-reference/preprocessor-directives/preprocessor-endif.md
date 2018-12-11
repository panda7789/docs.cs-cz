---
title: '#endif – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 13b43919b666dcc8c5adfc3490eaad73960547ae
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243896"
---
# <a name="endif-c-reference"></a><span data-ttu-id="4e998-102">#endif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4e998-102">#endif (C# Reference)</span></span>
<span data-ttu-id="4e998-103">`#endif` Určuje konec podmíněné direktivy, který začal [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) směrnice.</span><span class="sxs-lookup"><span data-stu-id="4e998-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="4e998-104">Například</span><span class="sxs-lookup"><span data-stu-id="4e998-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="4e998-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4e998-105">Remarks</span></span>  
 <span data-ttu-id="4e998-106">Podmíněnou direktivu, počínaje `#if` směrnice, musí být explicitně ukončen direktivou `#endif` směrnice.</span><span class="sxs-lookup"><span data-stu-id="4e998-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="4e998-107">Zobrazit [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad, jak používat `#endif`.</span><span class="sxs-lookup"><span data-stu-id="4e998-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e998-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e998-108">See Also</span></span>

- [<span data-ttu-id="4e998-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4e998-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="4e998-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4e998-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4e998-111">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="4e998-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
