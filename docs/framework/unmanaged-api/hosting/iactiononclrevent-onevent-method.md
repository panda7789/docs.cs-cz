---
title: IActionOnCLREvent::OnEvent – metoda
ms.date: 03/30/2017
api_name:
- IActionOnCLREvent.OnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IActionOnCLREvent::OnEvent
helpviewer_keywords:
- OnEvent method [.NET Framework hosting]
- IActionOnCLREvent::OnEvent method [.NET Framework hosting]
ms.assetid: 0970f10c-4304-4c12-91c0-83e51455afb4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e7045d3b095b6a35be8b55e1066b459e9583c93
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61970232"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="c5eef-102">IActionOnCLREvent::OnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="c5eef-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="c5eef-103">Provádí zpětná volání na události, které byly zaregistrovány pomocí volání [iclroneventmanager::registeractiononevent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c5eef-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5eef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5eef-104">Syntax</span></span>  
  
```  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5eef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c5eef-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="c5eef-106">[in] Jeden z [eclrevent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) hodnoty, které určuje typ události.</span><span class="sxs-lookup"><span data-stu-id="c5eef-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="c5eef-107">[in] Ukazatel na objekt, který obsahuje podrobnosti o `event`.</span><span class="sxs-lookup"><span data-stu-id="c5eef-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5eef-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c5eef-108">Return Value</span></span>  
  
|<span data-ttu-id="c5eef-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c5eef-109">HRESULT</span></span>|<span data-ttu-id="c5eef-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c5eef-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c5eef-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c5eef-111">S_OK</span></span>|<span data-ttu-id="c5eef-112">`OnEvent` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c5eef-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c5eef-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c5eef-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c5eef-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c5eef-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c5eef-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c5eef-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c5eef-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c5eef-116">The call timed out.</span></span>|  
|<span data-ttu-id="c5eef-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c5eef-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c5eef-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c5eef-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c5eef-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c5eef-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c5eef-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c5eef-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c5eef-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c5eef-121">E_FAIL</span></span>|<span data-ttu-id="c5eef-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c5eef-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c5eef-123">Pokud metoda vrátí E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c5eef-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c5eef-124">Následná volání na jakoukoli metodu, hostování vrátit HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c5eef-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c5eef-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c5eef-125">Remarks</span></span>  
 <span data-ttu-id="c5eef-126">`data` Parametrem je ukazatel na objekt neurčeného typu.</span><span class="sxs-lookup"><span data-stu-id="c5eef-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="c5eef-127">Pokud `event` parametr `Event_DomainUnload`, `data` je číselný identifikátor pro <xref:System.AppDomain> , která byla uvolněna.</span><span class="sxs-lookup"><span data-stu-id="c5eef-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="c5eef-128">Hostitel může přijmout vhodná opatření používá tento identifikátor jako klíč.</span><span class="sxs-lookup"><span data-stu-id="c5eef-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="c5eef-129">Pokud `event` je `Event_MDAFired`, `data` je ukazatel [mdainfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance, která obsahuje výstupní zprávy z na spravované ladění Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="c5eef-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="c5eef-130">Mda jsou funkce modulu CLR, který vývojářům pomoci s laděním, vygenerováním XML zprávy o událostech, které jsou jinak obtížné zachytit.</span><span class="sxs-lookup"><span data-stu-id="c5eef-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="c5eef-131">Takové zprávy může být zvláště užitečné při ladění přechody mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="c5eef-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="c5eef-132">Další informace najdete v tématu [diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="c5eef-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5eef-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5eef-133">Requirements</span></span>  
 <span data-ttu-id="c5eef-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5eef-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5eef-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c5eef-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c5eef-136">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c5eef-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c5eef-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5eef-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5eef-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5eef-138">See also</span></span>

- [<span data-ttu-id="c5eef-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c5eef-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c5eef-140">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="c5eef-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="c5eef-141">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5eef-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="c5eef-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5eef-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c5eef-143">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c5eef-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="c5eef-144">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="c5eef-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
