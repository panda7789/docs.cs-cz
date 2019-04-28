---
title: Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní.
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: 4545c6d3bc302dba0c37e5ae6ebefa8939b0cff9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61649904"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="fd5bb-102">Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fd5bb-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="fd5bb-103">Třída zadaná v `GetObject` nebo `CreateObject` volání funkce nebyla vystavena programovatelnosti rozhraní, nebo je změnit projekt z knihovny DLL na .exe, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="fd5bb-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="fd5bb-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="fd5bb-104">To correct this error</span></span>  
  
1. <span data-ttu-id="fd5bb-105">Přečtěte si dokumentaci k aplikace, která vytvoří objekt pro omezení týkající se použití automatizace pomocí této třídy objektu.</span><span class="sxs-lookup"><span data-stu-id="fd5bb-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2. <span data-ttu-id="fd5bb-106">Pokud jste změnili projekt z .dll, .exe nebo naopak, musíte ručně zrušíte původní .dll nebo .exe.</span><span class="sxs-lookup"><span data-stu-id="fd5bb-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5bb-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd5bb-107">See also</span></span>

- [<span data-ttu-id="fd5bb-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="fd5bb-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)
- [<span data-ttu-id="fd5bb-109">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="fd5bb-109">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
