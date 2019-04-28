---
title: '#Upozornění: C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 55768a354b2841021607ed40b4ef87b9767edcad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659953"
---
# <a name="warning-c-reference"></a><span data-ttu-id="f86ac-102">#warning (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f86ac-102">#warning (C# Reference)</span></span>
<span data-ttu-id="f86ac-103">`#warning` Umožňuje generovat [CS1030](../../misc/cs1030.md) úroveň jedno upozornění kompilátoru z určitého umístění ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="f86ac-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="f86ac-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f86ac-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="f86ac-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f86ac-105">Remarks</span></span>
 <span data-ttu-id="f86ac-106">Běžně `#warning` v podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="f86ac-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="f86ac-107">Je také možné vytvořit uživatelem definované chybové s [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="f86ac-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f86ac-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f86ac-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="f86ac-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f86ac-109">See also</span></span>

- [<span data-ttu-id="f86ac-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f86ac-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="f86ac-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f86ac-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="f86ac-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="f86ac-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
