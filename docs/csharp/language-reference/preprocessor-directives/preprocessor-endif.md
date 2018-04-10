---
title: '#endif (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d7e68dd20d914052c3fe5cabcb83abdae100465c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="endif-c-reference"></a><span data-ttu-id="81980-102">#endif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="81980-102">#endif (C# Reference)</span></span>
<span data-ttu-id="81980-103">`#endif`Určuje konec podmíněného – direktiva, což začal s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) – direktiva.</span><span class="sxs-lookup"><span data-stu-id="81980-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="81980-104">Například</span><span class="sxs-lookup"><span data-stu-id="81980-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="81980-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81980-105">Remarks</span></span>  
 <span data-ttu-id="81980-106">Podmíněné – direktiva, počínaje `#if` – direktiva, musí být explicitně ukončena s `#endif` – direktiva.</span><span class="sxs-lookup"><span data-stu-id="81980-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="81980-107">V tématu [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) příklad použití `#endif`.</span><span class="sxs-lookup"><span data-stu-id="81980-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81980-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="81980-108">See Also</span></span>  
 [<span data-ttu-id="81980-109">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="81980-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="81980-110">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="81980-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="81980-111">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="81980-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
