---
title: '#Chyba – C# referenční informace'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 7203e1271da66e78bfbd70717b0f5e536a7ebd86
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712517"
---
# <a name="error-c-reference"></a><span data-ttu-id="6de0b-102">#error (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6de0b-102">#error (C# Reference)</span></span>
<span data-ttu-id="6de0b-103">`#error` umožňuje vygenerovat [CS1029](../compiler-messages/cs1029.md) uživatelem definovanou chybu z konkrétního umístění ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="6de0b-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="6de0b-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6de0b-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="6de0b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6de0b-105">Remarks</span></span>  
 <span data-ttu-id="6de0b-106">Běžné použití `#error` je v podmíněných direktivách.</span><span class="sxs-lookup"><span data-stu-id="6de0b-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="6de0b-107">Je také možné vygenerovat upozornění definované uživatelem pomocí [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="6de0b-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6de0b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="6de0b-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6de0b-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6de0b-109">See also</span></span>

- [<span data-ttu-id="6de0b-110">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="6de0b-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6de0b-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6de0b-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6de0b-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="6de0b-112">C# Preprocessor Directives</span></span>](./index.md)
