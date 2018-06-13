---
title: -&gt; Operátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 037229b2081a43077cb4b5d02a8929b06ba9e077
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171977"
---
# <a name="-gt-operator-c-reference"></a><span data-ttu-id="d6bb3-102">-&gt; Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d6bb3-102">-&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="d6bb3-103">`->` Operátor kombinuje ukazatel vyhodnocení a člen přístup.</span><span class="sxs-lookup"><span data-stu-id="d6bb3-103">The `->` operator combines pointer dereferencing and member access.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d6bb3-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6bb3-104">Remarks</span></span>  
 <span data-ttu-id="d6bb3-105">Výraz formuláře,</span><span class="sxs-lookup"><span data-stu-id="d6bb3-105">An expression of the form,</span></span>  
  
```csharp  
x->y  
```  
  
 <span data-ttu-id="d6bb3-106">(kde `x` je ukazatel typu `T*` a `y` je členem `T`) je ekvivalentní,</span><span class="sxs-lookup"><span data-stu-id="d6bb3-106">(where `x` is a pointer of type `T*` and `y` is a member of `T`) is equivalent to,</span></span>  
  
```csharp  
(*x).y  
```  
  
 <span data-ttu-id="d6bb3-107">`->` Operátor lze použít pouze v kódu, který je označený jako [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="d6bb3-107">The `->` operator can be used only in code that is marked as [unsafe](../../../csharp/language-reference/keywords/unsafe.md).</span></span>  
  
 <span data-ttu-id="d6bb3-108">`->` Operátor nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="d6bb3-108">The `->` operator cannot be overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6bb3-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6bb3-109">Example</span></span>  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d6bb3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6bb3-110">See Also</span></span>  
 [<span data-ttu-id="d6bb3-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d6bb3-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d6bb3-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d6bb3-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d6bb3-113">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d6bb3-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
