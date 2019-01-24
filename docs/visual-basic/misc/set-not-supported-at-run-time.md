---
title: Metoda Set není podporována v době běhu
ms.date: 07/20/2015
f1_keywords:
- vbrID382
ms.assetid: cb7285d3-778f-423d-a2be-88573be8ad48
ms.openlocfilehash: c5ab1fe0dc6f588f710cb2879aad7896d13be800
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537774"
---
# <a name="set-not-supported-at-run-time"></a><span data-ttu-id="f4cf6-102">Metoda Set není podporována v době běhu</span><span class="sxs-lookup"><span data-stu-id="f4cf6-102">Set not supported at run time</span></span>
<span data-ttu-id="f4cf6-103">Pokusili jste se nastavit nebo změnit vlastnost, jejíž hodnota lze nastavit pouze v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="f4cf6-103">You tried to set or change a property whose value can only be set at design time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="f4cf6-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="f4cf6-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="f4cf6-105">Odeberte odkaz na vlastnost z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="f4cf6-105">Remove the reference to the property from your code.</span></span>  
  
2.  <span data-ttu-id="f4cf6-106">Změňte odkaz na pouze vrátí hodnotu vlastnosti v době běhu.</span><span class="sxs-lookup"><span data-stu-id="f4cf6-106">Change the reference to only return the value of the property at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4cf6-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4cf6-107">See also</span></span>
- [<span data-ttu-id="f4cf6-108">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="f4cf6-108">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
