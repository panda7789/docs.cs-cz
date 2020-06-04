---
title: Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: fc163c1069aa6f41766664e0fa5f5a9c34a1f73d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409566"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="4b56e-102">Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.</span><span class="sxs-lookup"><span data-stu-id="4b56e-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="4b56e-103">Proměnná deklarovaná s `Shared` modifikátorem je sdílená proměnná.</span><span class="sxs-lookup"><span data-stu-id="4b56e-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="4b56e-104">Sdílená proměnná identifikuje přesně jedno umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="4b56e-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="4b56e-105">Proměnná deklarovaná pomocí modifikátoru vyhodnotí `WithEvents` , že typ, ke kterému proměnná patří, zpracovává sadu událostí, které proměnná vyvolává.</span><span class="sxs-lookup"><span data-stu-id="4b56e-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="4b56e-106">Když je přiřazena hodnota proměnné, vlastnost vytvořená deklarací odřadí `WithEvents` všechny existující obslužné rutiny události a připojí novou obslužnou rutinu události prostřednictvím `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="4b56e-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="4b56e-107">**ID chyby:** BC30594</span><span class="sxs-lookup"><span data-stu-id="4b56e-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4b56e-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="4b56e-108">To correct this error</span></span>  
  
- <span data-ttu-id="4b56e-109">Deklarujte obslužnou rutinu události `Shared` .</span><span class="sxs-lookup"><span data-stu-id="4b56e-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b56e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="4b56e-110">See also</span></span>

- [<span data-ttu-id="4b56e-111">Shared</span><span class="sxs-lookup"><span data-stu-id="4b56e-111">Shared</span></span>](../modifiers/shared.md)
- [<span data-ttu-id="4b56e-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="4b56e-112">WithEvents</span></span>](../modifiers/withevents.md)
