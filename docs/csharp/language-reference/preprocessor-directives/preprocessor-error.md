---
title: '#Chyba – C# referenční informace'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: f18dbd007e80397b815256231a1d56e5ca50010e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608555"
---
# <a name="error-c-reference"></a><span data-ttu-id="ccb57-102">#error (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ccb57-102">#error (C# Reference)</span></span>
<span data-ttu-id="ccb57-103">`#error`umožňuje generovat [CS1029](../compiler-messages/cs1029.md) uživatelem definované chyby z konkrétního umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="ccb57-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="ccb57-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ccb57-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="ccb57-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccb57-105">Remarks</span></span>  
 <span data-ttu-id="ccb57-106">Běžné použití `#error` je v podmíněných direktivách.</span><span class="sxs-lookup"><span data-stu-id="ccb57-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="ccb57-107">Je také možné vygenerovat upozornění definované uživatelem pomocí [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="ccb57-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ccb57-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccb57-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ccb57-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccb57-109">See also</span></span>

- [<span data-ttu-id="ccb57-110">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="ccb57-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ccb57-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ccb57-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ccb57-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="ccb57-112">C# Preprocessor Directives</span></span>](./index.md)
