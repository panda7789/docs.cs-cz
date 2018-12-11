---
title: '#Upozornění: C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 08fcefd904ad43c781017087082592120e21f5cd
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236827"
---
# <a name="warning-c-reference"></a><span data-ttu-id="4dba7-102">#warning (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4dba7-102">#warning (C# Reference)</span></span>
<span data-ttu-id="4dba7-103">`#warning` Umožňuje generovat [CS1030](../../misc/cs1030.md) úroveň jedno upozornění kompilátoru z určitého umístění ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="4dba7-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="4dba7-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="4dba7-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="4dba7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4dba7-105">Remarks</span></span>
 <span data-ttu-id="4dba7-106">Běžně `#warning` v podmíněnou direktivu.</span><span class="sxs-lookup"><span data-stu-id="4dba7-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="4dba7-107">Je také možné vytvořit uživatelem definované chybové s [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="4dba7-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dba7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="4dba7-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="4dba7-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="4dba7-109">See Also</span></span>

- [<span data-ttu-id="4dba7-110">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4dba7-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="4dba7-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4dba7-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4dba7-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="4dba7-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
