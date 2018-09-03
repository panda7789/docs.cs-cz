---
title: '#upozornění (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 59ca63d5089e377627a9116f24f9a0a1681bb4b2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43461680"
---
# <a name="warning-c-reference"></a><span data-ttu-id="e0b94-102">#warning (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e0b94-102">#warning (C# Reference)</span></span>
<span data-ttu-id="e0b94-103">`#warning` Umožňuje generovat [CS1030](../../misc/cs1030.md) úroveň jedno upozornění kompilátoru z určitého umístění ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="e0b94-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="e0b94-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="e0b94-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0b94-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0b94-105">Remarks</span></span>
 <span data-ttu-id="e0b94-106">Běžně `#warning` v podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="e0b94-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="e0b94-107">Je také možné vytvořit uživatelem definované chybové s [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="e0b94-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0b94-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0b94-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="e0b94-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0b94-109">See Also</span></span>

- [<span data-ttu-id="e0b94-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e0b94-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="e0b94-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e0b94-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e0b94-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="e0b94-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
