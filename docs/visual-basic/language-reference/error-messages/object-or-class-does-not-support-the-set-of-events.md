---
title: Objekt nebo třída nepodporuje sadu událostí.
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: ad9176b5332a75f03968e742501c3fce541055de
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59342879"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="343f9-102">Objekt nebo třída nepodporuje sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="343f9-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="343f9-103">Pokusili jste se použít `WithEvents` proměnné s komponentou, která nemůže fungovat jako zdroj událostí pro zadanou sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="343f9-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="343f9-104">Například Kdybyste chtěli zpracování událostí objektu a pak vytvořte jiný objekt, který `Implements` první objekt.</span><span class="sxs-lookup"><span data-stu-id="343f9-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="343f9-105">I když možná myslíte, že může zpracování událostí z objektu implementované, to není vždy případu.</span><span class="sxs-lookup"><span data-stu-id="343f9-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="343f9-106">`Implements` pouze implementuje rozhraní pro metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="343f9-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="343f9-107">`WithEvents` není podporováno pro privátní `UserControls`, protože typ informace potřebné k vyvolání `ObjectEvent` není k dispozici v době běhu.</span><span class="sxs-lookup"><span data-stu-id="343f9-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="343f9-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="343f9-108">To correct this error</span></span>  
  
1. <span data-ttu-id="343f9-109">Nelze jímky událostí pro komponentu, která není zdroje událostí.</span><span class="sxs-lookup"><span data-stu-id="343f9-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="343f9-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="343f9-110">See also</span></span>

- [<span data-ttu-id="343f9-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="343f9-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
- [<span data-ttu-id="343f9-112">Příkaz Implements</span><span class="sxs-lookup"><span data-stu-id="343f9-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
