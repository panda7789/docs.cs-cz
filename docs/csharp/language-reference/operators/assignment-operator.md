---
title: = – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 979250c91cfe2abdf7295ae3866cd6b4294285cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269277"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="68b17-102">= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="68b17-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="68b17-103">Operátor přiřazení (`=`) ukládá hodnotu identifikátoru jeho pravém operand v umístění úložiště, vlastnost nebo indexer označený jako jeho levé operand a vrátí hodnotu jako svůj výsledek.</span><span class="sxs-lookup"><span data-stu-id="68b17-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="68b17-104">Operandy musí být stejného typu (nebo pravém operand musí být implicitně převést na typ levé operand).</span><span class="sxs-lookup"><span data-stu-id="68b17-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68b17-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68b17-105">Remarks</span></span>  
 <span data-ttu-id="68b17-106">Operátor přiřazení nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="68b17-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="68b17-107">Však můžete definovat operátory implicitního převodu na typ, které vám umožní použít operátor přiřazení s těmito typy.</span><span class="sxs-lookup"><span data-stu-id="68b17-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="68b17-108">Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="68b17-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="68b17-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="68b17-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="68b17-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="68b17-110">See Also</span></span>  
 [<span data-ttu-id="68b17-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="68b17-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="68b17-112">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="68b17-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="68b17-113">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="68b17-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
