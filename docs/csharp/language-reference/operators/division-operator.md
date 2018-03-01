---
title: "/ – operátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9e12e5c472266ea75d3f572a2091bd0784ea5dcf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="2ce13-102">/ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2ce13-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="2ce13-103">Operátor dělení (`/`) rozděluje jeho první operand podle jeho Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="2ce13-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="2ce13-104">Všechny číselné typy obsahuje předdefinované operátory dělení.</span><span class="sxs-lookup"><span data-stu-id="2ce13-104">All numeric types have predefined division operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2ce13-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ce13-105">Remarks</span></span>  
 <span data-ttu-id="2ce13-106">Uživatelem definované typy může přetížit `/` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="2ce13-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="2ce13-107">Přetížení `/` operátor implicitně přetížení [/ = – operátor](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2ce13-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="2ce13-108">Pokud budete provádět dělení dvě celá čísla, výsledkem je vždy celé číslo.</span><span class="sxs-lookup"><span data-stu-id="2ce13-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="2ce13-109">Například výsledek 7 / 3 je 2.</span><span class="sxs-lookup"><span data-stu-id="2ce13-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="2ce13-110">Chcete-li zjistit zbytek 7 / 3, použijte operátor zbytku ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span><span class="sxs-lookup"><span data-stu-id="2ce13-110">To determine the remainder of 7 / 3, use the remainder operator ([%](../../../csharp/language-reference/operators/modulus-operator.md)).</span></span> <span data-ttu-id="2ce13-111">Pro získání podílu jako racionální číslo nebo zlomek, získat typ dělenec nebo dělitel `float` nebo typ `double`.</span><span class="sxs-lookup"><span data-stu-id="2ce13-111">To obtain a quotient as a rational number or fraction, give the dividend or divisor type `float` or type `double`.</span></span> <span data-ttu-id="2ce13-112">Typ můžete přiřadit implicitně Pokud express dělenec nebo dělitel jako datový typ decimal umístěním číslice na pravé straně od desetinné čárky, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="2ce13-112">You can assign the type implicitly if you express the dividend or divisor as a decimal by putting a digit to the right side of the decimal point, as the following example shows.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ce13-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ce13-113">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="2ce13-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ce13-114">See Also</span></span>  
 [<span data-ttu-id="2ce13-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2ce13-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2ce13-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2ce13-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2ce13-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2ce13-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
