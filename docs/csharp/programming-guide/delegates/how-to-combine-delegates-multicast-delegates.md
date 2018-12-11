---
title: 'Postupy: Kombinování delegátů (vícesměroví delegáti)- C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d835f9b22fef550d6e73cbd620a283bd71e393ec
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237789"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="e208c-102">Postupy: Kombinování delegátů (vícesměroví delegáti) (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="e208c-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="e208c-103">Tento příklad ukazuje, jak vytvořit vícesměroví delegáti.</span><span class="sxs-lookup"><span data-stu-id="e208c-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="e208c-104">Užitečné vlastnost [delegovat](../../../csharp/language-reference/keywords/delegate.md) objekty je, že více objektů lze přiřadit instanci jednoho delegáta pomocí `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="e208c-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="e208c-105">Vícesměrového vysílání delegát obsahuje seznam přiřazenou delegáti.</span><span class="sxs-lookup"><span data-stu-id="e208c-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="e208c-106">Při volání vícesměrového vysílání delegáta vyvolá Delegáti v seznamu, v pořadí.</span><span class="sxs-lookup"><span data-stu-id="e208c-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="e208c-107">Můžete kombinovat pouze delegáti stejného typu.</span><span class="sxs-lookup"><span data-stu-id="e208c-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="e208c-108">`-` Operátor slouží k odebrání delegáta součásti vícesměrového vysílání delegáta.</span><span class="sxs-lookup"><span data-stu-id="e208c-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e208c-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e208c-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e208c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e208c-110">See Also</span></span>

- <xref:System.MulticastDelegate>  
- [<span data-ttu-id="e208c-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e208c-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e208c-112">Události</span><span class="sxs-lookup"><span data-stu-id="e208c-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
