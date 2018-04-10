---
title: = – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c7188abe54cb69678720b4dbbf4dbdea1be4abe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ddcb2-102">= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ddcb2-102">= Operator (C# Reference)</span></span>
<span data-ttu-id="ddcb2-103">Operátor přiřazení (`=`) ukládá hodnotu identifikátoru jeho pravém operand v umístění úložiště, vlastnost nebo indexer označený jako jeho levé operand a vrátí hodnotu jako svůj výsledek.</span><span class="sxs-lookup"><span data-stu-id="ddcb2-103">The assignment operator (`=`) stores the value of its right-hand operand in the storage location, property, or indexer denoted by its left-hand operand and returns the value as its result.</span></span> <span data-ttu-id="ddcb2-104">Operandy musí být stejného typu (nebo pravém operand musí být implicitně převést na typ levé operand).</span><span class="sxs-lookup"><span data-stu-id="ddcb2-104">The operands must be of the same type (or the right-hand operand must be implicitly convertible to the type of the left-hand operand).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddcb2-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddcb2-105">Remarks</span></span>  
 <span data-ttu-id="ddcb2-106">Operátor přiřazení nemohou být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="ddcb2-106">The assignment operator cannot be overloaded.</span></span> <span data-ttu-id="ddcb2-107">Však můžete definovat operátory implicitního převodu na typ, které vám umožní použít operátor přiřazení s těmito typy.</span><span class="sxs-lookup"><span data-stu-id="ddcb2-107">However, you can define implicit conversion operators for a type, which enable you to use the assignment operator with those types.</span></span> <span data-ttu-id="ddcb2-108">Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="ddcb2-108">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddcb2-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ddcb2-109">Example</span></span>  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ddcb2-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="ddcb2-110">See Also</span></span>  
 [<span data-ttu-id="ddcb2-111">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ddcb2-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ddcb2-112">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ddcb2-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ddcb2-113">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ddcb2-113">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
