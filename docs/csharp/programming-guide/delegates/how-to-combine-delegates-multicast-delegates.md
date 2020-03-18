---
title: Jak kombinovat delegáty (vícesměrové delegáty) – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: 7b5b9ba5c9bf70983fac9f869836b4c8c5449eca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705376"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="3b055-102">Jak kombinovat delegáty (vícesměrové delegáty) (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="3b055-102">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="3b055-103">Tento příklad ukazuje, jak vytvořit delegáty vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="3b055-103">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="3b055-104">Užitečnou vlastností [objektů delegáta](../../language-reference/builtin-types/reference-types.md) je, že pomocí operátoru `+` lze přiřadit více objektů jedné instanci delegáta.</span><span class="sxs-lookup"><span data-stu-id="3b055-104">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="3b055-105">Delegát vícesměrového vysílání obsahuje seznam přiřazených delegátů.</span><span class="sxs-lookup"><span data-stu-id="3b055-105">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="3b055-106">Při volání delegáta vícesměrového vysílání vyvolá delegáty v seznamu v pořadí.</span><span class="sxs-lookup"><span data-stu-id="3b055-106">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="3b055-107">Lze kombinovat pouze delegáty stejného typu.</span><span class="sxs-lookup"><span data-stu-id="3b055-107">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="3b055-108">Operátor `-` lze odebrat delegáta komponenty z delegáta vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="3b055-108">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b055-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b055-109">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="3b055-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="3b055-110">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="3b055-111">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3b055-111">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3b055-112">Akce</span><span class="sxs-lookup"><span data-stu-id="3b055-112">Events</span></span>](../events/index.md)
