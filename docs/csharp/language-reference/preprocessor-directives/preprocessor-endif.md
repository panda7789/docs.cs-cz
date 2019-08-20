---
title: '#endif- C# reference'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 74205c836b4eeb2d8b17b907bb13708f3225df08
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608577"
---
# <a name="endif-c-reference"></a><span data-ttu-id="eedd3-102">#endif (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="eedd3-102">#endif (C# Reference)</span></span>
<span data-ttu-id="eedd3-103">`#endif`určuje konec podmíněné direktivy, která začala s direktivou [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="eedd3-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="eedd3-104">Například</span><span class="sxs-lookup"><span data-stu-id="eedd3-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="eedd3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eedd3-105">Remarks</span></span>  
 <span data-ttu-id="eedd3-106">Podmíněná direktiva, která `#if` začíná direktivou, musí být explicitně ukončena `#endif` direktivou.</span><span class="sxs-lookup"><span data-stu-id="eedd3-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="eedd3-107">Příklad [](./preprocessor-if.md) použití `#endif`naleznete v tématu #if.</span><span class="sxs-lookup"><span data-stu-id="eedd3-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eedd3-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eedd3-108">See also</span></span>

- [<span data-ttu-id="eedd3-109">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="eedd3-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eedd3-110">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="eedd3-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eedd3-111">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="eedd3-111">C# Preprocessor Directives</span></span>](./index.md)
