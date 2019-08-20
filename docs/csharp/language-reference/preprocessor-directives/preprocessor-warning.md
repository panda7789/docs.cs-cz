---
title: '#upozornění – C# referenční informace'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 3d09cd95ef4d53e3f11d9feb9675ebba22d6f857
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608521"
---
# <a name="warning-c-reference"></a><span data-ttu-id="0aec4-102">#warning (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0aec4-102">#warning (C# Reference)</span></span>
<span data-ttu-id="0aec4-103">`#warning`umožňuje generovat upozornění na [CS1030](../../misc/cs1030.md) úrovně jednoho kompilátoru z konkrétního umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="0aec4-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="0aec4-104">Příklad:</span><span class="sxs-lookup"><span data-stu-id="0aec4-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="0aec4-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0aec4-105">Remarks</span></span>
 <span data-ttu-id="0aec4-106">Běžné použití `#warning` je v podmíněných direktivách.</span><span class="sxs-lookup"><span data-stu-id="0aec4-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="0aec4-107">K dispozici je také možnost generovat uživatelem definovanou chybu pomocí [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="0aec4-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0aec4-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="0aec4-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="0aec4-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0aec4-109">See also</span></span>

- [<span data-ttu-id="0aec4-110">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="0aec4-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0aec4-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0aec4-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0aec4-112">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="0aec4-112">C# Preprocessor Directives</span></span>](./index.md)
