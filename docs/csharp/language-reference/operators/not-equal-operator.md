---
title: '! = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 15f1b5930117e608644a58343fb855562f36b21c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237815"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="7ad6b-102">!= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="7ad6b-102">!= Operator (C# Reference)</span></span>
<span data-ttu-id="7ad6b-103">Operátor nerovnosti (`!=`) vrací hodnotu false, pokud jeho operandy jsou stejné, jinak hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="7ad6b-103">The inequality operator (`!=`) returns false if its operands are equal, true otherwise.</span></span> <span data-ttu-id="7ad6b-104">Pro všechny typy, včetně řetězce a objektu jsou předdefinované operátory nerovnost.</span><span class="sxs-lookup"><span data-stu-id="7ad6b-104">Inequality operators are predefined for all types, including string and object.</span></span> <span data-ttu-id="7ad6b-105">Lze přetěžovat uživatelsky definované typy `!=` operátor.</span><span class="sxs-lookup"><span data-stu-id="7ad6b-105">User-defined types can overload the `!=` operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ad6b-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ad6b-106">Remarks</span></span>  
 <span data-ttu-id="7ad6b-107">Pro předdefinované typy hodnot, operátor nerovnosti (`!=`) vrací hodnotu true, pokud jsou hodnoty jeho operandy různých, false, jinak.</span><span class="sxs-lookup"><span data-stu-id="7ad6b-107">For predefined value types, the inequality operator (`!=`) returns true if the values of its operands are different, false otherwise.</span></span> <span data-ttu-id="7ad6b-108">Pro odkaz na typy jiné než `string`, `!=` vrací true, pokud dva operandy odkazují na různé objekty.</span><span class="sxs-lookup"><span data-stu-id="7ad6b-108">For reference types other than `string`, `!=` returns true if its two operands refer to different objects.</span></span> <span data-ttu-id="7ad6b-109">Pro `string` typ `!=` porovnává hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="7ad6b-109">For the `string` type, `!=` compares the values of the strings.</span></span>  
  
 <span data-ttu-id="7ad6b-110">Mohou přetížit typy hodnotu definovanou uživatelem `!=` – operátor (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="7ad6b-110">User-defined value types can overload the `!=` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="7ad6b-111">Proto můžete typy odkazů definované uživatelem, i když se ve výchozím nastavení `!=` chová, jak je popsáno výše u obou typů předdefinované a vlastní odkaz.</span><span class="sxs-lookup"><span data-stu-id="7ad6b-111">So can user-defined reference types, although by default `!=` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="7ad6b-112">Pokud `!=` je přetížena, [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) musí také být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="7ad6b-112">If `!=` is overloaded, [==](../../../csharp/language-reference/operators/equality-comparison-operator.md) must also be overloaded.</span></span> <span data-ttu-id="7ad6b-113">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="7ad6b-113">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ad6b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ad6b-114">Example</span></span>  
 [!code-csharp[csRefOperators#33](../../../csharp/language-reference/operators/codesnippet/CSharp/not-equal-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7ad6b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ad6b-115">See Also</span></span>

- [<span data-ttu-id="7ad6b-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7ad6b-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="7ad6b-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7ad6b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7ad6b-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7ad6b-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
