---
title: / – operátor (Referenční dokumentace jazyka C#)
ms.date: 04/04/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 9d0bbff1fd9f4ab3c93c879d12ccd5fde1187b44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33272568"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0de2c-102">/ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0de2c-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="0de2c-103">Operátor dělení (`/`) rozděluje jeho první operand podle jeho Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="0de2c-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="0de2c-104">Všechny číselné typy obsahuje předdefinované operátory dělení.</span><span class="sxs-lookup"><span data-stu-id="0de2c-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="0de2c-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0de2c-105">Remarks</span></span>  
 <span data-ttu-id="0de2c-106">Uživatelem definované typy může přetížit `/` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="0de2c-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="0de2c-107">Přetížení `/` operátor implicitně přetížení [/ = – operátor](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="0de2c-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="0de2c-108">Pokud budete provádět dělení dvě celá čísla, výsledkem je vždy celé číslo.</span><span class="sxs-lookup"><span data-stu-id="0de2c-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="0de2c-109">Například výsledek 7 / 3 je 2.</span><span class="sxs-lookup"><span data-stu-id="0de2c-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="0de2c-110">Toto je Nezaměňovat s floored dělení, jako `/` operátor zaokrouhlí směrem k nule: -7 -2 je 3.</span><span class="sxs-lookup"><span data-stu-id="0de2c-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="0de2c-111">Chcete-li získat koeficient jako racionální číslo, použijte `float`, `double`, nebo `decimal` typy.</span><span class="sxs-lookup"><span data-stu-id="0de2c-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="0de2c-112">Existuje celá řada způsobů pro převod mezi [součástí číselnými typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span><span class="sxs-lookup"><span data-stu-id="0de2c-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="0de2c-113">K určení zbývající, použijte [operátor zbytku](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span><span class="sxs-lookup"><span data-stu-id="0de2c-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0de2c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="0de2c-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="0de2c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="0de2c-115">See Also</span></span>  
 [<span data-ttu-id="0de2c-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0de2c-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0de2c-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0de2c-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0de2c-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0de2c-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
