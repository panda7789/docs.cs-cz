---
title: '#upozornění - Odkaz jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715074"
---
# <a name="warning-c-reference"></a><span data-ttu-id="cbbd5-102">#warning (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cbbd5-102">#warning (C# Reference)</span></span>
<span data-ttu-id="cbbd5-103">`#warning`umožňuje generovat upozornění kompilátoru úrovně [CS1030](../../misc/cs1030.md) z určitého umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="cbbd5-104">Například:</span><span class="sxs-lookup"><span data-stu-id="cbbd5-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="cbbd5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cbbd5-105">Remarks</span></span>
 <span data-ttu-id="cbbd5-106">Běžné použití `#warning` je v podmíněné směrnice.</span><span class="sxs-lookup"><span data-stu-id="cbbd5-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="cbbd5-107">Je také možné generovat uživatelem definovanou chybu s [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="cbbd5-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cbbd5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbbd5-108">Example</span></span>  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="cbbd5-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="cbbd5-109">See also</span></span>

- [<span data-ttu-id="cbbd5-110">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cbbd5-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cbbd5-111">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cbbd5-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cbbd5-112">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cbbd5-112">C# Preprocessor Directives</span></span>](./index.md)
