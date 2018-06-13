---
title: '#upozornění (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: c56458e0100c23450655e48b2abfb346e18e0bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268180"
---
# <a name="warning-c-reference"></a><span data-ttu-id="bcac2-102">#warning (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bcac2-102">#warning (C# Reference)</span></span>
<span data-ttu-id="bcac2-103">`#warning` Umožňuje generovat varováním na úrovni jednoho z určitého umístění ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="bcac2-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="bcac2-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="bcac2-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="bcac2-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bcac2-105">Remarks</span></span>  
 <span data-ttu-id="bcac2-106">Běžně se používají `#warning` v podmíněného direktivu.</span><span class="sxs-lookup"><span data-stu-id="bcac2-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="bcac2-107">Je také možné generovat uživatelem definované chybové s [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="bcac2-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcac2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcac2-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bcac2-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="bcac2-109">See Also</span></span>  
 [<span data-ttu-id="bcac2-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bcac2-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bcac2-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bcac2-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bcac2-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="bcac2-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
