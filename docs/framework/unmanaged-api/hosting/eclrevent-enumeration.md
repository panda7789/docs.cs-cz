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
ms.openlocfilehash: 388f0de26983f8bb876f40a527f60d8bc59191a3
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616343"
---
# <a name="eclrevent-enumeration"></a><span data-ttu-id="4d80e-102">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="4d80e-102">EClrEvent Enumeration</span></span>
<span data-ttu-id="4d80e-103">Popisuje události modulu CLR (Common Language Runtime), pro které může hostitel registrovat zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="4d80e-103">Describes the common language runtime (CLR) events for which the host can register callbacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d80e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d80e-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    Event_ClrDisabled,  
    Event_DomainUnload,  
    Event_MDAFired,  
    Event_StackOverflow  
} EClrEvent;  
```  
  
## <a name="members"></a><span data-ttu-id="4d80e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="4d80e-105">Members</span></span>  
  
|<span data-ttu-id="4d80e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="4d80e-106">Member</span></span>|<span data-ttu-id="4d80e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4d80e-107">Description</span></span>|  
|------------|-----------------|  
|`Event_ClrDisabled`|<span data-ttu-id="4d80e-108">Určuje závažnou chybu modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="4d80e-108">Specifies a fatal CLR error.</span></span>|  
|`Event_DomainUnload`|<span data-ttu-id="4d80e-109">Určuje odložení konkrétního <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="4d80e-109">Specifies the unloading of a particular <xref:System.AppDomain>.</span></span>|  
|`Event_MDAFired`|<span data-ttu-id="4d80e-110">Určuje, že se vygenerovala zpráva pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="4d80e-110">Specifies that a Managed Debugging Assistant (MDA) message has been generated.</span></span>|  
|`Event_StackOverflow`|<span data-ttu-id="4d80e-111">Určuje, že došlo k chybě přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="4d80e-111">Specifies that a stack overflow error has occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d80e-112">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d80e-112">Remarks</span></span>  
 <span data-ttu-id="4d80e-113">Hostitel může registrovat zpětná volání pro jakýkoli typ události, který je popsán `EClrEvent` voláním metod rozhraní [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="4d80e-113">The host can register callbacks for any of the event types described by `EClrEvent` by calling methods of the [ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md) interface.</span></span> <span data-ttu-id="4d80e-114">Hostitel získá ukazatel na toto rozhraní voláním metody [ICLRControl:: GetCLRManager –](iclrcontrol-getclrmanager-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4d80e-114">The host gets a pointer to this interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
 <span data-ttu-id="4d80e-115">`Event_CLRDisabled`Události a `Event_DomainUnload` mohou být vyvolány více než jednou a z různých vláken k signalizaci uvolnění nebo zakázání CLR.</span><span class="sxs-lookup"><span data-stu-id="4d80e-115">The `Event_CLRDisabled` and `Event_DomainUnload` events can be raised more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
 <span data-ttu-id="4d80e-116">`Event_MDAFired`Událost vyvolává vytvoření instance [MDAInfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) , která obsahuje podrobnosti zprávy MDA.</span><span class="sxs-lookup"><span data-stu-id="4d80e-116">The `Event_MDAFired` event raises the creation of an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the details of the MDA message.</span></span> <span data-ttu-id="4d80e-117">Další informace o MDA najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="4d80e-117">For more information about MDAs, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d80e-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d80e-118">Requirements</span></span>  
 <span data-ttu-id="4d80e-119">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d80e-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d80e-120">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4d80e-120">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d80e-121">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4d80e-121">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d80e-122">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d80e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d80e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d80e-123">See also</span></span>

- [<span data-ttu-id="4d80e-124">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d80e-124">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="4d80e-125">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d80e-125">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="4d80e-126">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="4d80e-126">Hosting Enumerations</span></span>](hosting-enumerations.md)
