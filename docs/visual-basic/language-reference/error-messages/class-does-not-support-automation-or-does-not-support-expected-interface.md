---
title: Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní.
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: 856c3f5ef503a7e5919e9e602532c56d9557482f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84415398"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="e961c-102">Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e961c-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="e961c-103">Buď třída, kterou jste zadali ve `GetObject` `CreateObject` volání funkce, nebyla vystavena rozhraní programovatelnosti nebo jste změnili projekt z. dll na. exe, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="e961c-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="e961c-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="e961c-104">To correct this error</span></span>  
  
1. <span data-ttu-id="e961c-105">Podívejte se na dokumentaci aplikace, která vytvořila objekt pro omezení použití automatizace s touto třídou objektu.</span><span class="sxs-lookup"><span data-stu-id="e961c-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="e961c-106">Pokud jste změnili projekt z. dll na. exe nebo naopak, je nutné ručně zrušit registraci starého souboru. dll nebo. exe.</span><span class="sxs-lookup"><span data-stu-id="e961c-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e961c-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="e961c-107">See also</span></span>

- [<span data-ttu-id="e961c-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="e961c-108">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="e961c-109">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="e961c-109">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
