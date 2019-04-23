---
title: Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 04124ca044ad8dbff58f85230d7e10ea336d41e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59341471"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="aedd7-102">Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="aedd7-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="aedd7-103">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="aedd7-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="aedd7-104">Klient vyvolat vlastnost nebo metoda komponentu mimo proces a došlo k pokusu o předání odkazem na soukromý objekt jako jeden z argumentů.</span><span class="sxs-lookup"><span data-stu-id="aedd7-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="aedd7-105">Jako součást mimo proces volal metodu zpětného volání na jeho klienta a došlo k pokusu o předání odkazem na soukromý objekt.</span><span class="sxs-lookup"><span data-stu-id="aedd7-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="aedd7-106">Jako součást na více instancí procesu došlo k pokusu o odkaz na soukromý objekt předat jako argument, který byl vyvolání události.</span><span class="sxs-lookup"><span data-stu-id="aedd7-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="aedd7-107">Pokus o přiřazení odkaz na soukromý objekt klienta `ByRef` argument události byla zpracování.</span><span class="sxs-lookup"><span data-stu-id="aedd7-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="aedd7-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="aedd7-108">To correct this error</span></span>  
  
1. <span data-ttu-id="aedd7-109">Odeberte odkaz.</span><span class="sxs-lookup"><span data-stu-id="aedd7-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedd7-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aedd7-110">See also</span></span>

- [<span data-ttu-id="aedd7-111">Private</span><span class="sxs-lookup"><span data-stu-id="aedd7-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
