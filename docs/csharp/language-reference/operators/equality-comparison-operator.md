---
title: == – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: d9d7dcf3b38939e681fb51d6c674151cee78b3d0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421109"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="023ed-102">== – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="023ed-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="023ed-103">Pro předdefinované typy hodnot, operátor rovnosti (`==`) vrací hodnotu true, pokud jsou si rovny, hodnoty jeho operandy `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="023ed-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="023ed-104">Pro odkaz na typy jiné než [řetězec](../../../csharp/language-reference/keywords/string.md), `==` vrátí `true` Pokud dva operandy odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="023ed-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="023ed-105">Pro `string` typ `==` porovnává hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="023ed-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="023ed-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="023ed-106">Remarks</span></span>  
 <span data-ttu-id="023ed-107">Mohou přetížit typy hodnotu definovanou uživatelem `==` – operátor (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="023ed-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="023ed-108">Proto můžete typy odkazů definované uživatelem, i když se ve výchozím nastavení `==` chová, jak je popsáno výše u obou typů předdefinované a vlastní odkaz.</span><span class="sxs-lookup"><span data-stu-id="023ed-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="023ed-109">Pokud `==` je přetížena, [! =](../../../csharp/language-reference/operators/not-equal-operator.md) musí také být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="023ed-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="023ed-110">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="023ed-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="023ed-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="023ed-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="023ed-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="023ed-112">See Also</span></span>

- [<span data-ttu-id="023ed-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="023ed-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="023ed-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="023ed-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="023ed-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="023ed-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
