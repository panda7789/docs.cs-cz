---
description: '#Upozornění – Referenční dokumentace jazyka C#'
title: '#Upozornění – Referenční dokumentace jazyka C#'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: ab2cc5120492fc2a4b94296eb85e563c0a1d5ad3
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137835"
---
# <a name="warning-c-reference"></a><span data-ttu-id="a1c33-103">#warning (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a1c33-103">#warning (C# Reference)</span></span>
<span data-ttu-id="a1c33-104">`#warning` umožňuje generovat upozornění na [CS1030](../../misc/cs1030.md) úrovně jednoho kompilátoru z konkrétního umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="a1c33-104">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="a1c33-105">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a1c33-105">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1c33-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1c33-106">Remarks</span></span>
 <span data-ttu-id="a1c33-107">Běžné použití `#warning` je v podmíněných direktivách.</span><span class="sxs-lookup"><span data-stu-id="a1c33-107">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="a1c33-108">K dispozici je také možnost generovat uživatelem definovanou chybu pomocí [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="a1c33-108">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1c33-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1c33-109">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="a1c33-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1c33-110">See also</span></span>

- [<span data-ttu-id="a1c33-111">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a1c33-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a1c33-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="a1c33-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a1c33-113">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="a1c33-113">C# Preprocessor Directives</span></span>](./index.md)
