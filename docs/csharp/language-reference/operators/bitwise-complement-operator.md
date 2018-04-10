---
title: ~ – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a9b0cabcb101fce8422b1390ec8c4cb3b3849631
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="39569-102">~ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="39569-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="39569-103">`~` Operátor provádí operaci bitového doplňku na jeho operand, což má za následek Prohodit každý bit.</span><span class="sxs-lookup"><span data-stu-id="39569-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="39569-104">Operátory bitového doplňku jsou předdefinované pro [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), a [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="39569-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39569-105">`~` Symbol také se používá k deklaraci finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="39569-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="39569-106">Další informace najdete v tématu [finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="39569-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="39569-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39569-107">Remarks</span></span>  
 <span data-ttu-id="39569-108">Uživatelem definované typy může přetížit `~` operátor.</span><span class="sxs-lookup"><span data-stu-id="39569-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="39569-109">Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="39569-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="39569-110">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="39569-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39569-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="39569-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="39569-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="39569-112">See Also</span></span>  
 [<span data-ttu-id="39569-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="39569-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="39569-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="39569-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="39569-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="39569-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="39569-116">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="39569-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
