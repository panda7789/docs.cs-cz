---
title: '#upozornění – C# referenční informace'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715074"
---
# <a name="warning-c-reference"></a><span data-ttu-id="b2c1e-102">#warning (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b2c1e-102">#warning (C# Reference)</span></span>
<span data-ttu-id="b2c1e-103">`#warning` umožňuje vygenerovat upozornění na [CS1030](../../misc/cs1030.md) úrovně jednoho kompilátoru z konkrétního umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="b2c1e-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="b2c1e-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b2c1e-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="b2c1e-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b2c1e-105">Remarks</span></span>
 <span data-ttu-id="b2c1e-106">Běžné použití `#warning` je v podmíněných direktivách.</span><span class="sxs-lookup"><span data-stu-id="b2c1e-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="b2c1e-107">K dispozici je také možnost generovat uživatelem definovanou chybu pomocí [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="b2c1e-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2c1e-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2c1e-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="b2c1e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2c1e-109">See also</span></span>

- [<span data-ttu-id="b2c1e-110">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="b2c1e-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b2c1e-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b2c1e-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b2c1e-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="b2c1e-112">C# Preprocessor Directives</span></span>](./index.md)
