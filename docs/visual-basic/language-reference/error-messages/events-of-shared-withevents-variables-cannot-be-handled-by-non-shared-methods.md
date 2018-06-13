---
title: Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f61f4cd17b1bb3088117e0a0d91b186fd40db3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585168"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="c6003-102">Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.</span><span class="sxs-lookup"><span data-stu-id="c6003-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="c6003-103">Proměnná definovaná s `Shared` se modifikátor sdílené proměnné.</span><span class="sxs-lookup"><span data-stu-id="c6003-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="c6003-104">Sdílené proměnné identifikuje přesně jedno umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="c6003-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="c6003-105">Proměnná definovaná s `WithEvents` modifikátor vyhodnotí, že typem, ke kterému patří proměnnou zpracovává sadu událostí vyvolá proměnnou.</span><span class="sxs-lookup"><span data-stu-id="c6003-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="c6003-106">Když je hodnotu přiřazenou proměnné, vytvořené vlastnost `WithEvents` deklarace unhooks všechny stávající obslužné rutiny události a zachytí si novou obslužnou rutinu události prostřednictvím `Add` metoda.</span><span class="sxs-lookup"><span data-stu-id="c6003-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="c6003-107">**ID chyby:** BC30594</span><span class="sxs-lookup"><span data-stu-id="c6003-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6003-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="c6003-108">To correct this error</span></span>  
  
-   <span data-ttu-id="c6003-109">Deklarovat vaší obslužné rutiny události `Shared`.</span><span class="sxs-lookup"><span data-stu-id="c6003-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6003-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6003-110">See Also</span></span>  
 [<span data-ttu-id="c6003-111">Shared</span><span class="sxs-lookup"><span data-stu-id="c6003-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="c6003-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="c6003-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
