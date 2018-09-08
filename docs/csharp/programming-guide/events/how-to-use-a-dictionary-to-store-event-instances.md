---
title: 'Postupy: Použití slovníku k ukládání instancí událostí (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: c3a804ce1bf1f5ac8db47f0f0c1f37d1ca5f781b
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44213170"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a><span data-ttu-id="420ad-102">Postupy: Použití slovníku k ukládání instancí událostí (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="420ad-102">How to: Use a Dictionary to Store Event Instances (C# Programming Guide)</span></span>
<span data-ttu-id="420ad-103">Jedním použitím `accessor-declarations` je zveřejnit mnoho událostí bez přidělování pole pro každou událost, ale místo toho použití slovníku k ukládání instancí událostí.</span><span class="sxs-lookup"><span data-stu-id="420ad-103">One use for `accessor-declarations` is to expose many events without allocating a field for each event, but instead using a Dictionary to store the event instances.</span></span> <span data-ttu-id="420ad-104">To je užitečné pouze, pokud máte mnoho událostí, ale očekáváte, že většina události se nebude implementovat.</span><span class="sxs-lookup"><span data-stu-id="420ad-104">This is only useful if you have many events, but you expect most of the events will not be implemented.</span></span>  
  
## <a name="example"></a><span data-ttu-id="420ad-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="420ad-105">Example</span></span>  
 [!code-csharp[csProgGuideEvents#9](../../../csharp/programming-guide/events/codesnippet/CSharp/how-to-use-a-dictionary-to-store-event-instances_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="420ad-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="420ad-106">See Also</span></span>

- [<span data-ttu-id="420ad-107">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="420ad-107">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="420ad-108">Události</span><span class="sxs-lookup"><span data-stu-id="420ad-108">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
- [<span data-ttu-id="420ad-109">Delegáti</span><span class="sxs-lookup"><span data-stu-id="420ad-109">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)
