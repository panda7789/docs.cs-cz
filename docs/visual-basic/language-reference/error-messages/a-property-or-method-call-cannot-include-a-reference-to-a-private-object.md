---
title: Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 1f36526eab1bc0964bf89398b6e0f3e74d09fdc6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583822"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="08318-102">Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="08318-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="08318-103">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="08318-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="08318-104">Klient vyvolat vlastnosti nebo metody komponentu out-of-process a pokus o odkaz na soukromý objekt předat jako jednoho z argumentů.</span><span class="sxs-lookup"><span data-stu-id="08318-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="08318-105">Komponentu mimo proces volá metodu zpětného volání na svého klienta a pokus o předání odkaz na soukromý objekt.</span><span class="sxs-lookup"><span data-stu-id="08318-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="08318-106">Odkaz na soukromý objekt předat jako argument události, které se vyvolá pokus o komponentu mimo proces.</span><span class="sxs-lookup"><span data-stu-id="08318-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="08318-107">Pokus o přiřazení odkaz na soukromý objekt klienta `ByRef` argument byl zpracování události.</span><span class="sxs-lookup"><span data-stu-id="08318-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="08318-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="08318-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="08318-109">Odeberte odkaz.</span><span class="sxs-lookup"><span data-stu-id="08318-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08318-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="08318-110">See Also</span></span>  
 [<span data-ttu-id="08318-111">Private</span><span class="sxs-lookup"><span data-stu-id="08318-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
