---
title: 'Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: e1214a4d281dbcb9d8186770b68510d3d9a4b15f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327392"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="c4781-102">Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="c4781-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="c4781-103">Tento příklad ukazuje, jak vytvořit vícesměroví delegáti.</span><span class="sxs-lookup"><span data-stu-id="c4781-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="c4781-104">Užitečné vlastnost [delegovat](../../../csharp/language-reference/keywords/delegate.md) objektů je, že může být přiřazen více objektů do instance jednoho delegáta pomocí `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="c4781-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="c4781-105">Delegát vícesměrového vysílání obsahuje seznam přiřazené delegáti.</span><span class="sxs-lookup"><span data-stu-id="c4781-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="c4781-106">Když vícesměrového vysílání delegáta je zavolána, vyvolá delegáty v seznamu, v pořadí.</span><span class="sxs-lookup"><span data-stu-id="c4781-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="c4781-107">Lze spojit pouze delegáti stejného typu.</span><span class="sxs-lookup"><span data-stu-id="c4781-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="c4781-108">`-` Operátor slouží k odebrání delegáta součásti vícesměrového vysílání delegáta.</span><span class="sxs-lookup"><span data-stu-id="c4781-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4781-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4781-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="c4781-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4781-110">See Also</span></span>  
 <xref:System.MulticastDelegate>  
 [<span data-ttu-id="c4781-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c4781-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c4781-112">Události</span><span class="sxs-lookup"><span data-stu-id="c4781-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
