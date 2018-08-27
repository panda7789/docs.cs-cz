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
ms.openlocfilehash: 8af25217f9e7e66796192783a0b8e3415604dc90
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42933179"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="219f2-102">~ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="219f2-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="219f2-103">`~` Operátor provádí operaci s bitový doplněk svého operandu, což má za následek vrácení každý bit.</span><span class="sxs-lookup"><span data-stu-id="219f2-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="219f2-104">Operátory bitového doplňku jsou předdefinované pro [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), a [ulong](../../../csharp/language-reference/keywords/ulong.md).</span><span class="sxs-lookup"><span data-stu-id="219f2-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="219f2-105">`~` Symbol se také používá k deklaraci finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="219f2-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="219f2-106">Další informace najdete v tématu [finalizační metody](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span><span class="sxs-lookup"><span data-stu-id="219f2-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="219f2-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="219f2-107">Remarks</span></span>  
 <span data-ttu-id="219f2-108">Lze přetěžovat uživatelsky definované typy `~` operátor.</span><span class="sxs-lookup"><span data-stu-id="219f2-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="219f2-109">Další informace najdete v tématu [operátor](../../../csharp/language-reference/keywords/operator.md).</span><span class="sxs-lookup"><span data-stu-id="219f2-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="219f2-110">Operace interních typů jsou obecně povoleny na výčet.</span><span class="sxs-lookup"><span data-stu-id="219f2-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="219f2-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="219f2-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="219f2-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="219f2-112">See Also</span></span>

- [<span data-ttu-id="219f2-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="219f2-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="219f2-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="219f2-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="219f2-115">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="219f2-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="219f2-116">Finalizační metody</span><span class="sxs-lookup"><span data-stu-id="219f2-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
