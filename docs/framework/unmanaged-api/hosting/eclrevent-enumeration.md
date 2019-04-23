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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13d564be68d6b49a1616be97710312f33f828d48
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59176342"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="65995-102">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="65995-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="65995-103">Najdete popis obvyklých událostí modulu runtime (CLR) jazyk, pro které hostitele může registrace zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="65995-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65995-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65995-104">Syntax</span></span>  
  
```  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="65995-105">Členové</span><span class="sxs-lookup"><span data-stu-id="65995-105">Members</span></span>  
  
|<span data-ttu-id="65995-106">Člen</span><span class="sxs-lookup"><span data-stu-id="65995-106">Member</span></span>|<span data-ttu-id="65995-107">Popis</span><span class="sxs-lookup"><span data-stu-id="65995-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="65995-108">Určuje závažná chyba CLR.</span><span class="sxs-lookup"><span data-stu-id="65995-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="65995-109">Určuje uvolnění konkrétní <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="65995-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="65995-110">Určuje, zda byl vytvořen zprávu spravované ladění Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="65995-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="65995-111">Určuje, že došlo k chybě přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="65995-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65995-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65995-112">Remarks</span></span>  
 <span data-ttu-id="65995-113">Hostitel může registrace zpětných volání pro všechny typy událostí popsal `EClrEvent` voláním metod [iclroneventmanager –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="65995-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="65995-114">Hostitel získá ukazatel na toto rozhraní voláním [iclrcontrol::getclrmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="65995-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="65995-115">`Event_CLRDisabled` a `Event_DomainUnload` události mohou být vyvolány více než jednou a z různých vláken, který signalizuje, že uvolnění z paměti nebo vypnutí CLR.</span><span class="sxs-lookup"><span data-stu-id="65995-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="65995-116">`Event_MDAFired` Vyvolává událost vytvoření [mdainfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance, která obsahuje podrobnosti o zprávě MDA.</span><span class="sxs-lookup"><span data-stu-id="65995-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="65995-117">Další informace o mda najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="65995-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65995-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65995-118">Requirements</span></span>  
 <span data-ttu-id="65995-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65995-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65995-120">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65995-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65995-121">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65995-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65995-122">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65995-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65995-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65995-123">See also</span></span>

- [<span data-ttu-id="65995-124">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65995-124">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="65995-125">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65995-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="65995-126">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="65995-126">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
