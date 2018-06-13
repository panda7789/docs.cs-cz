---
title: '#endif (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 1686e706ce5cae3b2eaa28a7e1c89b5694b2be88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269974"
---
# <a name="endif-c-reference"></a><span data-ttu-id="7989b-102">#endif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7989b-102">#endif (C# Reference)</span></span>
<span data-ttu-id="7989b-103">`#endif` Určuje konec podmíněného – direktiva, což začal s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) – direktiva.</span><span class="sxs-lookup"><span data-stu-id="7989b-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="7989b-104">Například</span><span class="sxs-lookup"><span data-stu-id="7989b-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="7989b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7989b-105">Remarks</span></span>  
 <span data-ttu-id="7989b-106">Podmíněné – direktiva, počínaje `#if` – direktiva, musí být explicitně ukončena s `#endif` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="7989b-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="7989b-107">V tématu [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad použití `#endif`.</span><span class="sxs-lookup"><span data-stu-id="7989b-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7989b-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="7989b-108">See Also</span></span>  
 [<span data-ttu-id="7989b-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7989b-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="7989b-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7989b-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7989b-111">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="7989b-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
