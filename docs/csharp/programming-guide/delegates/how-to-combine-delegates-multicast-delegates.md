---
title: 'Postupy: Kombinování delegátů (delegáti C# vícesměrového vysílání) – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d9430021e6a9b438822f1a6dc201f64adf4fdb0f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590661"
---
# <a name="how-to-combine-delegates-multicast-delegatesc-programming-guide"></a><span data-ttu-id="e56d6-102">Postupy: Kombinování delegátů (vícesměroví delegáti) (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="e56d6-102">How to: Combine Delegates (Multicast Delegates)(C# Programming Guide)</span></span>
<span data-ttu-id="e56d6-103">Tento příklad ukazuje, jak vytvořit delegáty vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="e56d6-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="e56d6-104">Užitečnou vlastností objektů [delegáta](../../language-reference/keywords/delegate.md) je, že více objektů lze přiřadit k jedné instanci delegáta pomocí `+` operátoru.</span><span class="sxs-lookup"><span data-stu-id="e56d6-104">A useful property of [delegate](../../language-reference/keywords/delegate.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="e56d6-105">Delegát vícesměrového vysílání obsahuje seznam přiřazených delegátů.</span><span class="sxs-lookup"><span data-stu-id="e56d6-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="e56d6-106">Při volání delegáta vícesměrového vysílání vyvolá delegáty v seznamu v pořadí.</span><span class="sxs-lookup"><span data-stu-id="e56d6-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="e56d6-107">Kombinovat lze pouze delegáty stejného typu.</span><span class="sxs-lookup"><span data-stu-id="e56d6-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="e56d6-108">`-` Operátor lze použít k odebrání delegáta komponenty z delegáta vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="e56d6-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e56d6-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="e56d6-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="e56d6-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e56d6-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="e56d6-111">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e56d6-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e56d6-112">Události</span><span class="sxs-lookup"><span data-stu-id="e56d6-112">Events</span></span>](../events/index.md)
