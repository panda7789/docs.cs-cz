---
title: / – operátor (Referenční dokumentace jazyka C#)
ms.date: 04/04/2018
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
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5b17d122e3e3f75012e084903b6f8975fb53d46c
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d7dc7-102">/ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d7dc7-102">/ Operator (C# Reference)</span></span>
<span data-ttu-id="d7dc7-103">Operátor dělení (`/`) rozděluje jeho první operand podle jeho Druhý operand.</span><span class="sxs-lookup"><span data-stu-id="d7dc7-103">The division operator (`/`) divides its first operand by its second operand.</span></span> <span data-ttu-id="d7dc7-104">Všechny číselné typy obsahuje předdefinované operátory dělení.</span><span class="sxs-lookup"><span data-stu-id="d7dc7-104">All numeric types have predefined division operators.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="d7dc7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7dc7-105">Remarks</span></span>  
 <span data-ttu-id="d7dc7-106">Uživatelem definované typy může přetížit `/` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d7dc7-106">User-defined types can overload the `/` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="d7dc7-107">Přetížení `/` operátor implicitně přetížení [/ = – operátor](division-assignment-operator.md).</span><span class="sxs-lookup"><span data-stu-id="d7dc7-107">An overload of the `/` operator implicitly overloads the [/= operator](division-assignment-operator.md).</span></span>  
  
 <span data-ttu-id="d7dc7-108">Pokud budete provádět dělení dvě celá čísla, výsledkem je vždy celé číslo.</span><span class="sxs-lookup"><span data-stu-id="d7dc7-108">When you divide two integers, the result is always an integer.</span></span> <span data-ttu-id="d7dc7-109">Například výsledek 7 / 3 je 2.</span><span class="sxs-lookup"><span data-stu-id="d7dc7-109">For example, the result of 7 / 3 is 2.</span></span> <span data-ttu-id="d7dc7-110">Toto je Nezaměňovat s floored dělení, jako `/` operátor zaokrouhlí směrem k nule: -7 -2 je 3.</span><span class="sxs-lookup"><span data-stu-id="d7dc7-110">This is not to be confused with floored division, as the `/` operator rounds towards zero: -7 / 3 is -2.</span></span>  
  
 <span data-ttu-id="d7dc7-111">Chcete-li získat koeficient jako racionální číslo, použijte `float`, `double`, nebo `decimal` typy.</span><span class="sxs-lookup"><span data-stu-id="d7dc7-111">To obtain a quotient as a rational number, use the `float`, `double`, or `decimal` types.</span></span> <span data-ttu-id="d7dc7-112">Existuje celá řada způsobů pro převod mezi [součástí číselnými typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span><span class="sxs-lookup"><span data-stu-id="d7dc7-112">There are many ways to convert between [built in numeric types](../../../csharp/language-reference/keywords/reference-tables-for-types.md).</span></span>  
  
 <span data-ttu-id="d7dc7-113">K určení zbývající, použijte [operátor zbytku](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span><span class="sxs-lookup"><span data-stu-id="d7dc7-113">To determine the remainder, use the [remainder operator](../../../csharp/language-reference/operators/remainder-operator.md) `%`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7dc7-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7dc7-114">Example</span></span>  
 [!code-csharp[csRefOperators#42](../../../csharp/language-reference/operators/codesnippet/CSharp/division-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d7dc7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7dc7-115">See Also</span></span>  
 [<span data-ttu-id="d7dc7-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d7dc7-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d7dc7-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d7dc7-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d7dc7-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d7dc7-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
