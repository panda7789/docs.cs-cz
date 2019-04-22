---
title: Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: 2b32043898986b3e3e68fab18c5f907843d7691c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58838648"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a><span data-ttu-id="8b6ef-102">Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.</span><span class="sxs-lookup"><span data-stu-id="8b6ef-102">Events of shared WithEvents variables cannot be handled by non-shared methods</span></span>
<span data-ttu-id="8b6ef-103">Proměnná deklarovaná pomocí `Shared` jsou sdílené proměnné.</span><span class="sxs-lookup"><span data-stu-id="8b6ef-103">A variable declared with the `Shared` modifier is a shared variable.</span></span> <span data-ttu-id="8b6ef-104">Sdílené proměnné identifikuje přesně jednoho umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="8b6ef-104">A shared variable identifies exactly one storage location.</span></span> <span data-ttu-id="8b6ef-105">Proměnná deklarovaná pomocí `WithEvents` modifikátor vyhodnotí, že typ, ke kterému patří proměnné zpracovává sadu událostí, které vyvolává proměnné.</span><span class="sxs-lookup"><span data-stu-id="8b6ef-105">A variable declared with the `WithEvents` modifier asserts that the type to which the variable belongs handles the set of events the variable raises.</span></span> <span data-ttu-id="8b6ef-106">Pokud je hodnota přiřazena k proměnné, vlastnost vytvořené `WithEvents` deklarace unhooks všechny existující obslužné rutiny události a připojí si novou obslužnou rutinu události prostřednictvím `Add` metody.</span><span class="sxs-lookup"><span data-stu-id="8b6ef-106">When a value is assigned to the variable, the property created by the `WithEvents` declaration unhooks any existing event handler and hooks up the new event handler via the `Add` method.</span></span>  
  
 <span data-ttu-id="8b6ef-107">**ID chyby:** BC30594</span><span class="sxs-lookup"><span data-stu-id="8b6ef-107">**Error ID:** BC30594</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8b6ef-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="8b6ef-108">To correct this error</span></span>  
  
-   <span data-ttu-id="8b6ef-109">Deklarovat obslužnou rutinu události `Shared`.</span><span class="sxs-lookup"><span data-stu-id="8b6ef-109">Declare your event handler `Shared`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b6ef-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8b6ef-110">See also</span></span>

- [<span data-ttu-id="8b6ef-111">Shared</span><span class="sxs-lookup"><span data-stu-id="8b6ef-111">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="8b6ef-112">WithEvents</span><span class="sxs-lookup"><span data-stu-id="8b6ef-112">WithEvents</span></span>](../../../visual-basic/language-reference/modifiers/withevents.md)
