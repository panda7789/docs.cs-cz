---
title: Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 5f0740af49bb369be87a1a33973b67f59acf3ab6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700829"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="86d89-102">Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="86d89-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="86d89-103">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="86d89-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="86d89-104">Klient vyvolat vlastnost nebo metoda komponentu mimo proces a došlo k pokusu o předání odkazem na soukromý objekt jako jeden z argumentů.</span><span class="sxs-lookup"><span data-stu-id="86d89-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="86d89-105">Jako součást mimo proces volal metodu zpětného volání na jeho klienta a došlo k pokusu o předání odkazem na soukromý objekt.</span><span class="sxs-lookup"><span data-stu-id="86d89-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="86d89-106">Jako součást na více instancí procesu došlo k pokusu o odkaz na soukromý objekt předat jako argument, který byl vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="86d89-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="86d89-107">Pokus o přiřazení odkaz na soukromý objekt klienta `ByRef` argument události byla zpracování.</span><span class="sxs-lookup"><span data-stu-id="86d89-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="86d89-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="86d89-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="86d89-109">Odeberte odkaz.</span><span class="sxs-lookup"><span data-stu-id="86d89-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86d89-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86d89-110">See also</span></span>
- [<span data-ttu-id="86d89-111">Private</span><span class="sxs-lookup"><span data-stu-id="86d89-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
