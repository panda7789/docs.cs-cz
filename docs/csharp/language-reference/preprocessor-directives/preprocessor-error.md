---
title: '#Chyba (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 9ea4c24dcc3c0a4d39499bee5900cb9c6cc768c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269396"
---
# <a name="error-c-reference"></a><span data-ttu-id="19373-102">#error (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="19373-102">#error (C# Reference)</span></span>
<span data-ttu-id="19373-103">`#error` Umožňuje generovat chybu z určitého umístění ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="19373-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="19373-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="19373-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="19373-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19373-105">Remarks</span></span>  
 <span data-ttu-id="19373-106">Běžně se používají `#error` v podmíněného direktivu.</span><span class="sxs-lookup"><span data-stu-id="19373-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="19373-107">Je také možné upozornění na uživatelem definované s [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="19373-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19373-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="19373-108">Example</span></span>  
  
```csharp
// preprocessor_error.cs  
// CS1029 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#error DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="19373-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="19373-109">See Also</span></span>  
 [<span data-ttu-id="19373-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="19373-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="19373-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="19373-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="19373-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="19373-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
