---
title: "Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ddb4ecbbf456179e91aa0003c2dc5653f153411f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="23878-102">Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="23878-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="23878-103">Tento příklad ukazuje, jak vytvořit vícesměroví delegáti.</span><span class="sxs-lookup"><span data-stu-id="23878-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="23878-104">Užitečné vlastnost [delegovat](../../../csharp/language-reference/keywords/delegate.md) objektů je, že může být přiřazen více objektů do instance jednoho delegáta pomocí `+` operátor.</span><span class="sxs-lookup"><span data-stu-id="23878-104">A useful property of [delegate](../../../csharp/language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="23878-105">Delegát vícesměrového vysílání obsahuje seznam přiřazené delegáti.</span><span class="sxs-lookup"><span data-stu-id="23878-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="23878-106">Když vícesměrového vysílání delegáta je zavolána, vyvolá delegáty v seznamu, v pořadí.</span><span class="sxs-lookup"><span data-stu-id="23878-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="23878-107">Lze spojit pouze delegáti stejného typu.</span><span class="sxs-lookup"><span data-stu-id="23878-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="23878-108">`-` Operátor slouží k odebrání delegáta součásti vícesměrového vysílání delegáta.</span><span class="sxs-lookup"><span data-stu-id="23878-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23878-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="23878-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](../../../csharp/programming-guide/delegates/codesnippet/CSharp/how-to-combine-delegates-multicast-delegates_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="23878-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="23878-110">See Also</span></span>  
 <xref:System.MulticastDelegate>  
 [<span data-ttu-id="23878-111">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="23878-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="23878-112">Události</span><span class="sxs-lookup"><span data-stu-id="23878-112">Events</span></span>](../../../csharp/programming-guide/events/index.md)
