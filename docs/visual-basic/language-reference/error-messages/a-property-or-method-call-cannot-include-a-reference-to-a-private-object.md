---
title: Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.
ms.date: 07/20/2015
f1_keywords:
- vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
ms.openlocfilehash: 36c71cdb345d0fdc0da2b58865a1f11956bcb944
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409969"
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="81f21-102">Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="81f21-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>

<span data-ttu-id="81f21-103">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="81f21-103">Among the possible causes of this error are:</span></span>  
  
- <span data-ttu-id="81f21-104">Klient vyvolal vlastnost nebo metodu komponenty mimo proces a pokusil se předat odkaz na privátní objekt jako jeden z argumentů.</span><span class="sxs-lookup"><span data-stu-id="81f21-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
- <span data-ttu-id="81f21-105">Mimo procesová komponenta vyvolala na svém klientovi metodu zpětného volání a pokusila se předat odkaz na privátní objekt.</span><span class="sxs-lookup"><span data-stu-id="81f21-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
- <span data-ttu-id="81f21-106">Neprocesní komponenta se pokusila předat odkaz na privátní objekt jako argument události, kterou vyvolal.</span><span class="sxs-lookup"><span data-stu-id="81f21-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
- <span data-ttu-id="81f21-107">Klient se pokusil přiřadit odkaz na privátní objekt k `ByRef` argumentu události, kterou zpracovává.</span><span class="sxs-lookup"><span data-stu-id="81f21-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="81f21-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="81f21-108">To correct this error</span></span>  
  
1. <span data-ttu-id="81f21-109">Odeberte odkaz.</span><span class="sxs-lookup"><span data-stu-id="81f21-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f21-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="81f21-110">See also</span></span>

- [<span data-ttu-id="81f21-111">Hlášen</span><span class="sxs-lookup"><span data-stu-id="81f21-111">Private</span></span>](../modifiers/private.md)
