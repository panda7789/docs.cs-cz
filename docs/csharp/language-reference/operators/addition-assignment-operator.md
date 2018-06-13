---
title: += – operátor (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- +=_CSharpKeyword
helpviewer_keywords:
- += operator [C#]
- addition assignment operator (+=) [C#]
ms.assetid: 9cdf97e6-331d-492b-85e1-3ec3171484e9
ms.openlocfilehash: bcd56acad8e2b08585e5ae60f1c3cf8183b5664a
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171876"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4302c-102">+= – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4302c-102">+= Operator (C# Reference)</span></span>
<span data-ttu-id="4302c-103">Operátor přiřazení sčítání.</span><span class="sxs-lookup"><span data-stu-id="4302c-103">The addition assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4302c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4302c-104">Remarks</span></span>  
 <span data-ttu-id="4302c-105">K pomocí výrazu `+=` operátor přiřazení, jako například</span><span class="sxs-lookup"><span data-stu-id="4302c-105">An expression using the `+=` assignment operator, such as</span></span>  
  
```csharp  
x += y  
```  
  
 <span data-ttu-id="4302c-106">je ekvivalentem</span><span class="sxs-lookup"><span data-stu-id="4302c-106">is equivalent to</span></span>  
  
```csharp  
x = x + y  
```  
  
 <span data-ttu-id="4302c-107">Kromě toho, že `x` je Vyhodnocená jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="4302c-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="4302c-108">Význam [+ – operátor](../../../csharp/language-reference/operators/addition-operator.md) závisí na typech `x` a `y` (přidání pro číselné operandy, zřetězení pro operandy řetězec a tak dále).</span><span class="sxs-lookup"><span data-stu-id="4302c-108">The meaning of the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) depends on the types of `x` and `y` (addition for numeric operands, concatenation for string operands, and so forth).</span></span>  
  
 <span data-ttu-id="4302c-109">`+=` Operátor nemohou být přetíženy přímo, ale může přetížit uživatelem definované typy [+ – operátor](../../../csharp/language-reference/operators/addition-operator.md) (viz [operátor](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="4302c-109">The `+=` operator cannot be overloaded directly, but user-defined types can overload the [+ operator](../../../csharp/language-reference/operators/addition-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
 <span data-ttu-id="4302c-110">`+=` Operátor slouží také k určení metodu, která bude volána v reakci na událost; tyto metody jsou volány obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="4302c-110">The `+=` operator is also used to specify a method that will be called in response to an event; such methods are called event handlers.</span></span> <span data-ttu-id="4302c-111">Použití `+=` operátor v tomto kontextu se označuje jako *odběr pro událost*.</span><span class="sxs-lookup"><span data-stu-id="4302c-111">The use of the `+=` operator in this context is referred to as *subscribing to an event*.</span></span> <span data-ttu-id="4302c-112">Další informace najdete v tématu [postupy: přihlášení a odhlášení odběru událostí](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) a [delegáti](../../../csharp/programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="4302c-112">For more information, see [How to: Subscribe to and Unsubscribe from Events](../../../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md) and [Delegates](../../../csharp/programming-guide/delegates/index.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4302c-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4302c-113">Example</span></span>  
 [!code-csharp[csRefOperators#35](../../../csharp/language-reference/operators/codesnippet/CSharp/addition-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4302c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="4302c-114">See Also</span></span>  
 [<span data-ttu-id="4302c-115">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4302c-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="4302c-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4302c-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="4302c-117">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4302c-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
