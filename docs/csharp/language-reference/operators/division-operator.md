---
title: / – operátor (Referenční dokumentace jazyka C#)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: bddf6d234f3536ad64f0cd876cc7ade4494916d9
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255472"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b483c-102">/ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b483c-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="b483c-103">Operátor dělení (`/`) rozděluje svůj první operand tak svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="b483c-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="b483c-104">Všechny číselné typy obsahuje předdefinované operátory dělení.</span><span class="sxs-lookup"><span data-stu-id="b483c-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="b483c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b483c-105">Remarks</span></span>  
 <span data-ttu-id="b483c-106">Lze přetěžovat uživatelsky definované typy `/` – operátor (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b483c-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="b483c-107">Přetížení `/` implicitně přetížení operátoru [/ = – operátor](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="b483c-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="b483c-108">Při dělení dvou celých čísel, výsledek je vždycky celé číslo.</span><span class="sxs-lookup"><span data-stu-id="b483c-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="b483c-109">Například výsledek 7 / 3 je 2.</span><span class="sxs-lookup"><span data-stu-id="b483c-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="b483c-110">Toto je nezaměňovat floored dělení, jako `/` operátor zaokrouhlí směrem k nule.: -7 / 3 -2.</span><span class="sxs-lookup"><span data-stu-id="b483c-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="b483c-111">Chcete-li získat podíl racionální číslo as, použijte `float`, `double`, nebo `decimal` typy.</span><span class="sxs-lookup"><span data-stu-id="b483c-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="b483c-112">Existuje mnoho způsobů, jak převést mezi [integrovaným číselné typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span><span class="sxs-lookup"><span data-stu-id="b483c-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="b483c-113">Chcete-li určit zbývající, použijte [operátor zbytku](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span><span class="sxs-lookup"><span data-stu-id="b483c-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b483c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="b483c-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b483c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b483c-115">See Also</span></span>

- [<span data-ttu-id="b483c-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b483c-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b483c-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b483c-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b483c-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b483c-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
