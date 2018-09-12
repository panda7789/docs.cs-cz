---
title: -&gt; – Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: fb95e508ce1339868723bcc3178851e8c1355c1f
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44700580"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="a8ec2-102">-&gt; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="a8ec2-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="a8ec2-103">`->` Operátor kombinuje ukazatel přesměrování a člen přístup.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a8ec2-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a8ec2-104">Remarks</span></span>  
 <span data-ttu-id="a8ec2-105">Výraz formuláře</span><span class="sxs-lookup"><span data-stu-id="a8ec2-105">An expression of the form,</span></span>  
  
```csharp  
x->y  
```  
  
 <span data-ttu-id="a8ec2-106">(kde `x` je ukazatel typu `T*` a `y` je členem skupiny `T`) je ekvivalentní,</span><span class="sxs-lookup"><span data-stu-id="a8ec2-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```csharp  
(*x).y  
```  
  
 <span data-ttu-id="a8ec2-107">`->` Operátor lze použít pouze v kódu, který je označen jako [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="a8ec2-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="a8ec2-108">`->` Operátor nelze přetížit.</span><span class="sxs-lookup"><span data-stu-id="a8ec2-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8ec2-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8ec2-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="a8ec2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8ec2-110">See Also</span></span>

- [<span data-ttu-id="a8ec2-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8ec2-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a8ec2-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a8ec2-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a8ec2-113">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a8ec2-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
