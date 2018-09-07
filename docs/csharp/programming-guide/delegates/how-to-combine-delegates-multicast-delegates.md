---
title: 'Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e3cc3f9082bd86004a7821b64c01253408c07641
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083274"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="d6115-102">Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="d6115-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="d6115-103">Tento příklad ukazuje, jak vytvořit vícesměroví delegáti.</span><span class="sxs-lookup"><span data-stu-id="d6115-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="d6115-104">Užitečné vlastnost [delegovat](../../../csharp/language-reference/keywords/delegate.md) objekty je, že více objektů lze přiřadit instanci jednoho delegáta pomocí `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="d6115-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="d6115-105">Vícesměrového vysílání delegát obsahuje seznam přiřazenou delegáti.</span><span class="sxs-lookup"><span data-stu-id="d6115-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="d6115-106">Při volání vícesměrového vysílání delegáta vyvolá Delegáti v seznamu, v pořadí.</span><span class="sxs-lookup"><span data-stu-id="d6115-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="d6115-107">Můžete kombinovat pouze delegáti stejného typu.</span><span class="sxs-lookup"><span data-stu-id="d6115-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="d6115-108">`-` Operátor slouží k odebrání delegáta součásti vícesměrového vysílání delegáta.</span><span class="sxs-lookup"><span data-stu-id="d6115-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6115-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6115-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d6115-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6115-110">See Also</span></span>

- <xref:System.MulticastDelegate>  
- [<span data-ttu-id="d6115-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d6115-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d6115-112">Události</span><span class="sxs-lookup"><span data-stu-id="d6115-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
