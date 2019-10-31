---
title: EClrEvent – výčet
ms.date: 03/30/2017
api_name:
- EClrEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrEvent
helpviewer_keywords:
- EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type:
- apiref
ms.openlocfilehash: ee749fd40f440e92f1d1b09c2ea5e7bdd51f1cbe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131137"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="a73ad-102">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="a73ad-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="a73ad-103">Popisuje události modulu CLR (Common Language Runtime), pro které může hostitel registrovat zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="a73ad-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a73ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a73ad-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="a73ad-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a73ad-105">Members</span></span>  
  
|<span data-ttu-id="a73ad-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a73ad-106">Member</span></span>|<span data-ttu-id="a73ad-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a73ad-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="a73ad-108">Určuje závažnou chybu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="a73ad-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="a73ad-109">Určuje uvolnění konkrétní <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a73ad-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="a73ad-110">Určuje, že se vygenerovala zpráva pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="a73ad-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="a73ad-111">Určuje, že došlo k chybě přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a73ad-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a73ad-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a73ad-112">Remarks</span></span>  
 <span data-ttu-id="a73ad-113">Hostitel může zaregistrovat zpětná volání pro jakýkoli typ události popsanou `EClrEvent` voláním metod rozhraní [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a73ad-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="a73ad-114">Hostitel získá ukazatel na toto rozhraní voláním metody [ICLRControl:: GetCLRManager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a73ad-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="a73ad-115">Události `Event_CLRDisabled` a `Event_DomainUnload` lze vyvolat více než jednou a z různých vláken k signalizaci uvolnění nebo zakázání CLR.</span><span class="sxs-lookup"><span data-stu-id="a73ad-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="a73ad-116">Událost `Event_MDAFired` vyvolává vytvoření instance [MDAInfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) , která obsahuje podrobnosti zprávy MDA.</span><span class="sxs-lookup"><span data-stu-id="a73ad-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="a73ad-117">Další informace o MDA najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="a73ad-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a73ad-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a73ad-118">Requirements</span></span>  
 <span data-ttu-id="a73ad-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a73ad-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a73ad-120">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a73ad-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a73ad-121">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a73ad-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a73ad-122">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a73ad-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a73ad-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a73ad-123">See also</span></span>

- [<span data-ttu-id="a73ad-124">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a73ad-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="a73ad-125">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a73ad-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="a73ad-126">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="a73ad-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
