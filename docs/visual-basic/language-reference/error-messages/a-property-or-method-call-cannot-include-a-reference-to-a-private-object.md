---
title: "Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID98
ms.assetid: 059b43e1-202d-4fa2-806b-7bad63c1e7ca
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: cce2bc67beb7e4ac0664b5b7240f5eb3ea0204f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="a-property-or-method-call-cannot-include-a-reference-to-a-private-object-either-as-an-argument-or-as-a-return-value"></a><span data-ttu-id="0c43c-102">Volání vlastnosti nebo metody nemůže obsahovat odkaz na soukromý objekt, a to ani jako argument, ani jako typ návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0c43c-102">A property or method call cannot include a reference to a private object, either as an argument or as a return value</span></span>
<span data-ttu-id="0c43c-103">Mezi možné příčiny této chyby patří:</span><span class="sxs-lookup"><span data-stu-id="0c43c-103">Among the possible causes of this error are:</span></span>  
  
-   <span data-ttu-id="0c43c-104">Klient vyvolat vlastnosti nebo metody komponentu out-of-process a pokus o odkaz na soukromý objekt předat jako jednoho z argumentů.</span><span class="sxs-lookup"><span data-stu-id="0c43c-104">A client invoked a property or method of an out-of-process component and attempted to pass a reference to a private object as one of the arguments.</span></span>  
  
-   <span data-ttu-id="0c43c-105">Komponentu mimo proces volá metodu zpětného volání na svého klienta a pokus o předání odkaz na soukromý objekt.</span><span class="sxs-lookup"><span data-stu-id="0c43c-105">An out-of-process component invoked a call-back method on its client and attempted to pass a reference to a private object.</span></span>  
  
-   <span data-ttu-id="0c43c-106">Odkaz na soukromý objekt předat jako argument události, které se vyvolá pokus o komponentu mimo proces.</span><span class="sxs-lookup"><span data-stu-id="0c43c-106">An out-of-process component attempted to pass a reference to a private object as an argument of an event it was raising.</span></span>  
  
-   <span data-ttu-id="0c43c-107">Pokus o přiřazení odkaz na soukromý objekt klienta `ByRef` argument byl zpracování události.</span><span class="sxs-lookup"><span data-stu-id="0c43c-107">A client attempted to assign a private object reference to a `ByRef` argument of an event it was handling.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0c43c-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0c43c-108">To correct this error</span></span>  
  
1.  <span data-ttu-id="0c43c-109">Odeberte odkaz.</span><span class="sxs-lookup"><span data-stu-id="0c43c-109">Remove the reference.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c43c-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c43c-110">See Also</span></span>  
 [<span data-ttu-id="0c43c-111">Privátní</span><span class="sxs-lookup"><span data-stu-id="0c43c-111">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)
