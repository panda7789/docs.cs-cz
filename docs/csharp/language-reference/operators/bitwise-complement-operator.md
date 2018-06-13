---
title: ~ – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 25b157fafde7d2b75cd8b112848a01e9b3fb0db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270300"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="995a4-102">~ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="995a4-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="995a4-103">`~` Operátor provádí operaci bitového doplňku na jeho operand, což má za následek Prohodit každý bit.</span><span class="sxs-lookup"><span data-stu-id="995a4-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="995a4-104">Operátory bitového doplňku jsou předdefinované pro [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), a [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="995a4-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="995a4-105">`~` Symbol také se používá k deklaraci finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="995a4-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="995a4-106">Další informace najdete v tématu [finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="995a4-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="995a4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="995a4-107">Remarks</span></span>  
 <span data-ttu-id="995a4-108">Uživatelem definované typy může přetížit `~` operátor.</span><span class="sxs-lookup"><span data-stu-id="995a4-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="995a4-109">Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="995a4-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="995a4-110">Operace u celočíselných typů jsou obecně povoleny na výčtu.</span><span class="sxs-lookup"><span data-stu-id="995a4-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="995a4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="995a4-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="995a4-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="995a4-112">See Also</span></span>  
 [<span data-ttu-id="995a4-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="995a4-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="995a4-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="995a4-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="995a4-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="995a4-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="995a4-116">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="995a4-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
