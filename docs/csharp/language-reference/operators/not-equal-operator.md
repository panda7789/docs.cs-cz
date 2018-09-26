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
ms.openlocfilehash: e974ffb1b25944e24fca23864dc7e932ec1876d5
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47076492"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="15d71-102">!= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="15d71-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="15d71-103">Operátor nerovnosti (`!=`) vrací hodnotu false, pokud jeho operandy jsou stejné, jinak hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="15d71-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="15d71-104">Pro všechny typy, včetně řetězce a objektu jsou předdefinované operátory nerovnost.</span><span class="sxs-lookup"><span data-stu-id="15d71-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="15d71-105">Lze přetěžovat uživatelsky definované typy `!=` operátor.</span><span class="sxs-lookup"><span data-stu-id="15d71-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15d71-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="15d71-106">Remarks</span></span>  
 <span data-ttu-id="15d71-107">Pro předdefinované typy hodnot, operátor nerovnosti (`!=`) vrací hodnotu true, pokud jsou hodnoty jeho operandy různých, false, jinak.</span><span class="sxs-lookup"><span data-stu-id="15d71-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="15d71-108">Pro odkaz na typy jiné než `string`, `!=` vrací true, pokud dva operandy odkazují na různé objekty.</span><span class="sxs-lookup"><span data-stu-id="15d71-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="15d71-109">Pro `string` typ `!=` porovnává hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="15d71-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="15d71-110">Mohou přetížit typy hodnotu definovanou uživatelem `!=` – operátor (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="15d71-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="15d71-111">Proto můžete typy odkazů definované uživatelem, i když se ve výchozím nastavení `!=` chová, jak je popsáno výše u obou typů předdefinované a vlastní odkaz.</span><span class="sxs-lookup"><span data-stu-id="15d71-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="15d71-112">Pokud `!=` je přetížena, [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) musí také být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="15d71-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="15d71-113">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="15d71-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15d71-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="15d71-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="15d71-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="15d71-115">See Also</span></span>

- [<span data-ttu-id="15d71-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15d71-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="15d71-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="15d71-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="15d71-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="15d71-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
