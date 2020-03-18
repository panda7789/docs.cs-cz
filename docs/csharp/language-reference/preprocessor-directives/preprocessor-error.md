---
title: '#chyba – odkaz jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 28e77304edee617adc1422e6a52d0a617cd9b3bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173403"
---
# <a name="error-c-reference"></a><span data-ttu-id="9448b-102">#error (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9448b-102">#error (C# Reference)</span></span>
<span data-ttu-id="9448b-103">`#error`umožňuje generovat chybu definovanou uživatelem [CS1029](../compiler-messages/cs1029.md) z určitého umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="9448b-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="9448b-104">Například:</span><span class="sxs-lookup"><span data-stu-id="9448b-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="9448b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9448b-105">Remarks</span></span>  
 <span data-ttu-id="9448b-106">Běžné použití `#error` je v podmíněné směrnice.</span><span class="sxs-lookup"><span data-stu-id="9448b-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="9448b-107">Je také možné generovat uživatelem definované upozornění s [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="9448b-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9448b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9448b-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9448b-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="9448b-109">See also</span></span>

- [<span data-ttu-id="9448b-110">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9448b-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9448b-111">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9448b-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9448b-112">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9448b-112">C# Preprocessor Directives</span></span>](./index.md)
