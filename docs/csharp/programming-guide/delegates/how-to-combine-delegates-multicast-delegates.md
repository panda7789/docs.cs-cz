---
title: Postup kombinování delegátů (Delegáti vícesměrového vysílání) – Průvodce programováním v C#
description: Naučte se kombinovat delegáty a vytvořit delegáty vícesměrového vysílání. Podívejte se na příklad kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], combining
- multicast delegates [C#]
ms.assetid: 4e689450-6d0c-46de-acfd-f961018ae5dd
ms.openlocfilehash: d23ea758c9da2c3399f5d98e81360cc250b428a1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87302734"
---
# <a name="how-to-combine-delegates-multicast-delegates-c-programming-guide"></a><span data-ttu-id="eb62a-104">Jak kombinovat delegáty (vícesměrové delegáty) (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="eb62a-104">How to combine delegates (Multicast Delegates) (C# Programming Guide)</span></span>
<span data-ttu-id="eb62a-105">Tento příklad ukazuje, jak vytvořit delegáty vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="eb62a-105">This example demonstrates how to create multicast delegates.</span></span> <span data-ttu-id="eb62a-106">Užitečnou vlastností objektů [delegáta](../../language-reference/builtin-types/reference-types.md) je, že více objektů lze přiřadit k jedné instanci delegáta pomocí `+` operátoru.</span><span class="sxs-lookup"><span data-stu-id="eb62a-106">A useful property of [delegate](../../language-reference/builtin-types/reference-types.md) objects is that multiple objects can be assigned to one delegate instance by using the `+` operator.</span></span> <span data-ttu-id="eb62a-107">Delegát vícesměrového vysílání obsahuje seznam přiřazených delegátů.</span><span class="sxs-lookup"><span data-stu-id="eb62a-107">The multicast delegate contains a list of the assigned delegates.</span></span> <span data-ttu-id="eb62a-108">Při volání delegáta vícesměrového vysílání vyvolá delegáty v seznamu v pořadí.</span><span class="sxs-lookup"><span data-stu-id="eb62a-108">When the multicast delegate is called, it invokes the delegates in the list, in order.</span></span> <span data-ttu-id="eb62a-109">Kombinovat lze pouze delegáty stejného typu.</span><span class="sxs-lookup"><span data-stu-id="eb62a-109">Only delegates of the same type can be combined.</span></span>  
  
 <span data-ttu-id="eb62a-110">`-`Operátor lze použít k odebrání delegáta komponenty z delegáta vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="eb62a-110">The `-` operator can be used to remove a component delegate from a multicast delegate.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb62a-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb62a-111">Example</span></span>  
 [!code-csharp[csProgGuideDelegates#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#11)]  
  
## <a name="see-also"></a><span data-ttu-id="eb62a-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eb62a-112">See also</span></span>

- <xref:System.MulticastDelegate>
- [<span data-ttu-id="eb62a-113">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="eb62a-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="eb62a-114">Události</span><span class="sxs-lookup"><span data-stu-id="eb62a-114">Events</span></span>](../events/index.md)
