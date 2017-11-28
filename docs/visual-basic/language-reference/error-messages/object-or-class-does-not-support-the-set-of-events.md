---
title: "Objekt nebo třída nepodporuje sadu událostí."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be4b9140222ef969bfb836fd74f45b8f662360b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="a98fe-102">Objekt nebo třída nepodporuje sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="a98fe-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="a98fe-103">Pokusili jste se použít `WithEvents` proměnné s komponenty, která nemůže pracovat jako zdroje událostí pro zadanou sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="a98fe-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="a98fe-104">Například Kdybyste chtěli jímky událostí objektu a pak vytvořte jiný objekt, který `Implements` první objekt.</span><span class="sxs-lookup"><span data-stu-id="a98fe-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="a98fe-105">I když může si myslíte, že by mohla jímky událostí z implementovaná objektu, to není vždy případu.</span><span class="sxs-lookup"><span data-stu-id="a98fe-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="a98fe-106">`Implements`pouze implementuje rozhraní pro metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a98fe-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="a98fe-107">`WithEvents`není podporováno pro privátní `UserControls`, protože typ informace potřebné k vyvolat `ObjectEvent` není k dispozici v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a98fe-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a98fe-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a98fe-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="a98fe-109">Nelze jímky událostí pro komponenty, která není zdroje událostí.</span><span class="sxs-lookup"><span data-stu-id="a98fe-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98fe-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="a98fe-110">See Also</span></span>  
 [<span data-ttu-id="a98fe-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="a98fe-111">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)  
 [<span data-ttu-id="a98fe-112">Implements – příkaz</span><span class="sxs-lookup"><span data-stu-id="a98fe-112">Implements Statement</span></span>](../../../visual-basic/language-reference/statements/implements-statement.md)
