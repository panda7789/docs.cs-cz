---
title: '#Chyba (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: ed43c1f85142ec6c54e44db5e3b0b7de3ef36bb8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43565402"
---
# <a name="error-c-reference"></a><span data-ttu-id="a93a7-102">#error (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a93a7-102">#error (C# Reference)</span></span>
<span data-ttu-id="a93a7-103">`#error` Umožňuje generovat [CS1029](../compiler-messages/cs1029.md) uživatelem definované chybové z určitého umístění ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="a93a7-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="a93a7-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a93a7-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="a93a7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a93a7-105">Remarks</span></span>  
 <span data-ttu-id="a93a7-106">Běžně `#error` v podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="a93a7-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="a93a7-107">Je také možné generovat upozornění definované uživatelem s [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="a93a7-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a93a7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a93a7-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a93a7-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="a93a7-109">See Also</span></span>

- [<span data-ttu-id="a93a7-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a93a7-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a93a7-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a93a7-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a93a7-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="a93a7-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
