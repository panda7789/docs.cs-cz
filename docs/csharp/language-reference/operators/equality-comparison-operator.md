---
title: == – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: c6f93be4d422fe42787e36f5b86e2cccbfc645b7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239011"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="9c845-102">== – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9c845-102">== Operator (C# Reference)</span></span>
<span data-ttu-id="9c845-103">Pro předdefinované typy hodnot, operátor rovnosti (`==`) vrací hodnotu true, pokud jsou si rovny, hodnoty jeho operandy `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="9c845-103">For predefined value types, the equality operator (`==`) returns true if the values of its operands are equal, `false` otherwise.</span></span> <span data-ttu-id="9c845-104">Pro odkaz na typy jiné než [řetězec](../../../csharp/language-reference/keywords/string.md), `==` vrátí `true` Pokud dva operandy odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="9c845-104">For reference types other than [string](../../../csharp/language-reference/keywords/string.md), `==` returns `true` if its two operands refer to the same object.</span></span> <span data-ttu-id="9c845-105">Pro `string` typ `==` porovnává hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="9c845-105">For the `string` type, `==` compares the values of the strings.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c845-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c845-106">Remarks</span></span>  
 <span data-ttu-id="9c845-107">Mohou přetížit typy hodnotu definovanou uživatelem `==` – operátor (naleznete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="9c845-107">User-defined value types can overload the `==` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="9c845-108">Proto můžete typy odkazů definované uživatelem, i když se ve výchozím nastavení `==` chová, jak je popsáno výše u obou typů předdefinované a vlastní odkaz.</span><span class="sxs-lookup"><span data-stu-id="9c845-108">So can user-defined reference types, although by default `==` behaves as described above for both predefined and user-defined reference types.</span></span> <span data-ttu-id="9c845-109">Pokud `==` je přetížena, [! =](../../../csharp/language-reference/operators/not-equal-operator.md) musí také být přetíženy.</span><span class="sxs-lookup"><span data-stu-id="9c845-109">If `==` is overloaded, [!=](../../../csharp/language-reference/operators/not-equal-operator.md) must also be overloaded.</span></span> <span data-ttu-id="9c845-110">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="9c845-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c845-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="9c845-111">Example</span></span>  
 [!code-csharp[csRefOperators#36](../../../csharp/language-reference/operators/codesnippet/CSharp/equality-comparison-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="9c845-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c845-112">See Also</span></span>

- [<span data-ttu-id="9c845-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9c845-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9c845-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9c845-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9c845-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9c845-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
