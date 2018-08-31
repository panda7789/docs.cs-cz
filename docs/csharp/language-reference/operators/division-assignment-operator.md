---
title: /= – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 8fff048cc441181aa3f0e3c0c638d501aaf9de3f
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2018
ms.locfileid: "43330929"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="1f794-102">/= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1f794-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="1f794-103">Operátor přiřazení dělení.</span><span class="sxs-lookup"><span data-stu-id="1f794-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f794-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1f794-104">Remarks</span></span>  
 <span data-ttu-id="1f794-105">Pomocí výrazu `/=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="1f794-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```csharp  
x /= y  
```  
  
 <span data-ttu-id="1f794-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="1f794-106">is equivalent to</span></span>  
  
```csharp  
x = x / y  
```  
  
 <span data-ttu-id="1f794-107">s tím rozdílem, že `x` se jenom vyhodnotí jednou.</span><span class="sxs-lookup"><span data-stu-id="1f794-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="1f794-108">[/ – Operátor](../../../csharp/language-reference/operators/division-operator.md) je předdefinovaný pro číselné typy provádět dělení.</span><span class="sxs-lookup"><span data-stu-id="1f794-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="1f794-109">`/=` Operátor nelze přetížit přímo, ale lze přetěžovat uživatelsky definované typy [/ – operátor](../../../csharp/language-reference/operators/division-operator.md) (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1f794-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="1f794-110">Na všechny složené operátory přiřazení implicitně přetížení binární operátor přetížení ekvivalentní složeného přiřazení.</span><span class="sxs-lookup"><span data-stu-id="1f794-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f794-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f794-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="1f794-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f794-112">See Also</span></span>

- [<span data-ttu-id="1f794-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1f794-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1f794-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1f794-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1f794-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1f794-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
