---
title: 'Postupy: Kombinování delegátů (vícesměroví delegáti)- C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 426b9f91d3e3328522ec5c7ab043d5074ececc43
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61711016"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="bcded-102">Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="bcded-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="bcded-103">Tento příklad ukazuje, jak vytvořit vícesměroví delegáti.</span><span class="sxs-lookup"><span data-stu-id="bcded-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="bcded-104">Užitečné vlastnost [delegovat](../../../csharp/language-reference/keywords/delegate.md) objekty je, že více objektů lze přiřadit instanci jednoho delegáta pomocí `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="bcded-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="bcded-105">Vícesměrového vysílání delegát obsahuje seznam přiřazenou delegáti.</span><span class="sxs-lookup"><span data-stu-id="bcded-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="bcded-106">Při volání vícesměrového vysílání delegáta vyvolá Delegáti v seznamu, v pořadí.</span><span class="sxs-lookup"><span data-stu-id="bcded-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="bcded-107">Můžete kombinovat pouze delegáti stejného typu.</span><span class="sxs-lookup"><span data-stu-id="bcded-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="bcded-108">`-` Operátor slouží k odebrání delegáta součásti vícesměrového vysílání delegáta.</span><span class="sxs-lookup"><span data-stu-id="bcded-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bcded-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="bcded-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="bcded-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bcded-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="bcded-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bcded-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="bcded-112">Události</span><span class="sxs-lookup"><span data-stu-id="bcded-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
