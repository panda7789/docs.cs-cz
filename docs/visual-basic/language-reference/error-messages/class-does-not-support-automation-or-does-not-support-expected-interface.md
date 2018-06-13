---
title: Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní.
ms.date: 07/20/2015
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
ms.openlocfilehash: 860c472794495ef2be37aea7c7d8305c237dfd13
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585666"
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="49733-102">Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní.</span><span class="sxs-lookup"><span data-stu-id="49733-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="49733-103">Třída zadaná v `GetObject` nebo `CreateObject` volání funkce nebyl vystaven programovatelnosti rozhraní nebo změnit projekt z .dll .exe, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="49733-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="49733-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="49733-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="49733-105">Podívejte se do dokumentace aplikace, která vytvořila objekt pro omezení na využití automatizace s touto třídou objektu.</span><span class="sxs-lookup"><span data-stu-id="49733-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2.  <span data-ttu-id="49733-106">Pokud jste změnili projektu z .dll .exe nebo naopak, musíte ručně registraci staré .dll nebo .exe.</span><span class="sxs-lookup"><span data-stu-id="49733-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49733-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="49733-107">See Also</span></span>  
 [<span data-ttu-id="49733-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="49733-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="49733-109">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="49733-109">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
