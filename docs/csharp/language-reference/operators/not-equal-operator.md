---
title: '!= – operátor (Referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: e409e2a80886fd5f7f4cdbeaa9b4e3325f8a967b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272436"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2933b-102">!= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2933b-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="2933b-103">Operátor nerovnosti (`!=`) vrátí hodnotu false, pokud jejími operandy, jsou stejné, jinak hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="2933b-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="2933b-104">Operátory nerovnosti jsou předdefinovány pro všechny typy, včetně řetězec a objekt.</span><span class="sxs-lookup"><span data-stu-id="2933b-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="2933b-105">Uživatelem definované typy může přetížit `!=` operátor.</span><span class="sxs-lookup"><span data-stu-id="2933b-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2933b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2933b-106">Remarks</span></span>  
 <span data-ttu-id="2933b-107">Pro předdefinované typy hodnot, operátor nerovnosti (`!=`) vrátí hodnotu true, pokud jsou hodnoty jejími operandy, jiný, false, jinak hodnota.</span><span class="sxs-lookup"><span data-stu-id="2933b-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="2933b-108">Pro odkaz na typy jiné než `string`, `!=` vrátí hodnotu true, pokud jeho dva operandy odkazovat na jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="2933b-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="2933b-109">Pro `string` typu `!=` porovnává hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="2933b-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="2933b-110">Typy hodnotu definovanou uživatelem může přetížit `!=` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="2933b-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="2933b-111">Proto můžete odkaz na uživatelem definované typy, i když ve výchozím nastavení `!=` chová, jak je popsáno výše pro oba typy předdefinované a vlastní odkaz.</span><span class="sxs-lookup"><span data-stu-id="2933b-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="2933b-112">Pokud `!=` je přetížena [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) také musí být přetížený.</span><span class="sxs-lookup"><span data-stu-id="2933b-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="2933b-113">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="2933b-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2933b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2933b-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2933b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2933b-115">See Also</span></span>  
 [<span data-ttu-id="2933b-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2933b-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2933b-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2933b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2933b-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2933b-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
