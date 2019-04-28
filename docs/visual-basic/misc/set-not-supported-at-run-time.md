---
title: Metoda Set není podporována v době běhu
ms.date: 07/20/2015
f1_keywords:
- vbrID382
ms.assetid: cb7285d3-778f-423d-a2be-88573be8ad48
ms.openlocfilehash: 1b3f8aa3811baae240e6baa546082d0dcf2cf667
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61594864"
---
# <a name="set-not-supported-at-run-time"></a><span data-ttu-id="a10e3-102">Metoda Set není podporována v době běhu</span><span class="sxs-lookup"><span data-stu-id="a10e3-102">Set not supported at run time</span></span>
<span data-ttu-id="a10e3-103">Pokusili jste se nastavit nebo změnit vlastnost, jejíž hodnota lze nastavit pouze v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="a10e3-103">You tried to set or change a property whose value can only be set at design time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a10e3-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="a10e3-104">To correct this error</span></span>  
  
1. <span data-ttu-id="a10e3-105">Odeberte odkaz na vlastnost z vašeho kódu.</span><span class="sxs-lookup"><span data-stu-id="a10e3-105">Remove the reference to the property from your code.</span></span>  
  
2. <span data-ttu-id="a10e3-106">Změňte odkaz na pouze vrátí hodnotu vlastnosti v době běhu.</span><span class="sxs-lookup"><span data-stu-id="a10e3-106">Change the reference to only return the value of the property at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a10e3-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a10e3-107">See also</span></span>

- [<span data-ttu-id="a10e3-108">Správa vlastností projektů a řešení</span><span class="sxs-lookup"><span data-stu-id="a10e3-108">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
