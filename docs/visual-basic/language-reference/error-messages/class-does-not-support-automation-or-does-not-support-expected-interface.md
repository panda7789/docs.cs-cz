---
title: "Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID430
ms.assetid: d985bb7e-e48e-443e-86f2-ddb86758757c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6528ceabeb7fb7a1cdc0beff2fd362632a0a0c9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="class-does-not-support-automation-or-does-not-support-expected-interface"></a><span data-ttu-id="5288b-102">Třída nepodporuje automatizaci nebo nepodporuje očekávané rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5288b-102">Class does not support Automation or does not support expected interface</span></span>
<span data-ttu-id="5288b-103">Třída zadaná v `GetObject` nebo `CreateObject` volání funkce nebyl vystaven programovatelnosti rozhraní nebo změnit projekt z .dll .exe, nebo naopak.</span><span class="sxs-lookup"><span data-stu-id="5288b-103">Either the class you specified in the `GetObject` or `CreateObject` function call has not exposed a programmability interface, or you changed a project from .dll to .exe, or vice versa.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="5288b-104">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="5288b-104">To correct this error</span></span>  
  
1.  <span data-ttu-id="5288b-105">Podívejte se do dokumentace aplikace, která vytvořila objekt pro omezení na využití automatizace s touto třídou objektu.</span><span class="sxs-lookup"><span data-stu-id="5288b-105">Check the documentation of the application that created the object for limitations on the use of automation with this class of object.</span></span>  
  
2.  <span data-ttu-id="5288b-106">Pokud jste změnili projektu z .dll .exe nebo naopak, musíte ručně registraci staré .dll nebo .exe.</span><span class="sxs-lookup"><span data-stu-id="5288b-106">If you changed a project from .dll to .exe or vice versa, you must manually unregister the old .dll or .exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5288b-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="5288b-107">See Also</span></span>  
 [<span data-ttu-id="5288b-108">Typy chyb</span><span class="sxs-lookup"><span data-stu-id="5288b-108">Error Types</span></span>](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [<span data-ttu-id="5288b-109">Kontaktujte nás</span><span class="sxs-lookup"><span data-stu-id="5288b-109">Talk to Us</span></span>](/visualstudio/ide/talk-to-us)
