---
title: "EClrEvent – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: EClrEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: EClrEvent
helpviewer_keywords: EClrEvent enumeration [.NET Framework hosting]
ms.assetid: 7c36a7c2-75a2-4971-bc23-abf54c812154
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5d453cf7d3c7613397890c2d49a2dbe81a2e5d81
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="1891f-102">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="1891f-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="1891f-103">Najdete popis obvyklých událostí modulu runtime (CLR) jazyk, pro které hostitele může registrace zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="1891f-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1891f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1891f-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="1891f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1891f-105">Members</span></span>  
  
|<span data-ttu-id="1891f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1891f-106">Member</span></span>|<span data-ttu-id="1891f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1891f-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="1891f-108">Určuje závažné chybě CLR.</span><span class="sxs-lookup"><span data-stu-id="1891f-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="1891f-109">Určuje uvolnění konkrétní <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="1891f-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="1891f-110">Určuje, že byla vygenerována zprávu spravované ladění Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="1891f-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="1891f-111">Určuje, že došlo k chybu přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="1891f-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1891f-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1891f-112">Remarks</span></span>  
 <span data-ttu-id="1891f-113">Hostitel může registrace zpětných volání pro všechny typy událostí popsaného `EClrEvent` voláním metod [iclroneventmanager –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1891f-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="1891f-114">Hostitel voláním získá ukazatel toto rozhraní [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="1891f-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="1891f-115">`Event_CLRDisabled` a `Event_DomainUnload` události mohou být vyvolány více než jednou a z různých vláknech signál uvolnění nebo zakázání modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="1891f-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="1891f-116">`Event_MDAFired` Událost se vyvolá vytvoření [mdainfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance, který obsahuje podrobnosti zprávy (mda).</span><span class="sxs-lookup"><span data-stu-id="1891f-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="1891f-117">Další informace o mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="1891f-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1891f-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1891f-118">Requirements</span></span>  
 <span data-ttu-id="1891f-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1891f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1891f-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1891f-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1891f-121">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1891f-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1891f-122">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1891f-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1891f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1891f-123">See Also</span></span>  
 [<span data-ttu-id="1891f-124">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1891f-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 [<span data-ttu-id="1891f-125">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1891f-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="1891f-126">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="1891f-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
