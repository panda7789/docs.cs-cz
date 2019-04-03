---
title: Objekt nebo třída nepodporuje sadu událostí.
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: 2e00bdd624b54e19f19b6dabf6681bbf89709e60
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822577"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="cd7e4-102">Objekt nebo třída nepodporuje sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="cd7e4-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="cd7e4-103">Pokusili jste se použít `WithEvents` proměnné s komponentou, která nemůže fungovat jako zdroj událostí pro zadanou sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="cd7e4-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="cd7e4-104">Například Kdybyste chtěli zpracování událostí objektu a pak vytvořte jiný objekt, který `Implements` první objekt.</span><span class="sxs-lookup"><span data-stu-id="cd7e4-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="cd7e4-105">I když možná myslíte, že může zpracování událostí z objektu implementované, to není vždy případu.</span><span class="sxs-lookup"><span data-stu-id="cd7e4-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="cd7e4-106">`Implements` pouze implementuje rozhraní pro metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cd7e4-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="cd7e4-107">`WithEvents` není podporováno pro privátní `UserControls`, protože typ informace potřebné k vyvolání `ObjectEvent` není k dispozici v době běhu.</span><span class="sxs-lookup"><span data-stu-id="cd7e4-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="cd7e4-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="cd7e4-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="cd7e4-109">Nelze jímky událostí pro komponentu, která není zdroje událostí.</span><span class="sxs-lookup"><span data-stu-id="cd7e4-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd7e4-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd7e4-110">See also</span></span>

- [<span data-ttu-id="cd7e4-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="cd7e4-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="cd7e4-112">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="cd7e4-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
