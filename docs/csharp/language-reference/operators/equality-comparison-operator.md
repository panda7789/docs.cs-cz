---
title: == – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca22846325968519a1f7625461867c0d83a1a9f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3e761-102">== – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3e761-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="3e761-103">Pro předdefinované typy hodnot, operátor rovnosti (`==`) vrátí hodnotu true, pokud hodnoty jejími operandy, jsou stejné, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="3e761-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="3e761-104">Pro odkaz na typy jiné než [řetězec](../../../csharp/language-reference/keywords/string.md), `==` vrátí `true` pokud jeho dva operandy odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="3e761-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="3e761-105">Pro `string` typu `==` porovnává hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="3e761-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3e761-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e761-106">Remarks</span></span>  
 <span data-ttu-id="3e761-107">Typy hodnotu definovanou uživatelem může přetížit `==` – operátor (najdete v části [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3e761-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="3e761-108">Proto můžete odkaz na uživatelem definované typy, i když ve výchozím nastavení `==` chová, jak je popsáno výše pro oba typy předdefinované a vlastní odkaz.</span><span class="sxs-lookup"><span data-stu-id="3e761-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="3e761-109">Pokud `==` je přetížena [! =](../../../csharp/language-reference/operators/not-equal-operator.md) také musí být přetížený.</span><span class="sxs-lookup"><span data-stu-id="3e761-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="3e761-110">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="3e761-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e761-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="3e761-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="3e761-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e761-112">See Also</span></span>  
 [<span data-ttu-id="3e761-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3e761-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3e761-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="3e761-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3e761-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3e761-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
