---
title: '#Chyba – C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 3aa31ce7e189684bd60c238905df3bcbd1818ed6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559333"
---
# <a name="error-c-reference"></a><span data-ttu-id="88836-102">#error (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="88836-102">#error (C# Reference)</span></span>
<span data-ttu-id="88836-103">`#error` Umožňuje generovat [CS1029](../compiler-messages/cs1029.md) uživatelem definované chybové z určitého umístění ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="88836-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="88836-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="88836-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="88836-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88836-105">Remarks</span></span>  
 <span data-ttu-id="88836-106">Běžně `#error` v podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="88836-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="88836-107">Je také možné generovat upozornění definované uživatelem s [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="88836-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88836-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="88836-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="88836-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88836-109">See also</span></span>

- [<span data-ttu-id="88836-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88836-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="88836-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="88836-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="88836-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="88836-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
