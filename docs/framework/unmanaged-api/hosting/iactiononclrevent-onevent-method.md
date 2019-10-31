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
ms.openlocfilehash: 98807717fc913052dae15f9f3cbd462d4f537ad4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126916"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="c6440-102">IActionOnCLREvent::OnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="c6440-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="c6440-103">Provádí zpětná volání pro události, které byly zaregistrovány pomocí volání metody [ICLROnEventManager:: RegisterActionOnEvent –](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c6440-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6440-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6440-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6440-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6440-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="c6440-106">pro Jedna z hodnot [EClrEvent –](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) , která označuje typ události.</span><span class="sxs-lookup"><span data-stu-id="c6440-106">[in] One of the [EClrEvent](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="c6440-107">pro Ukazatel na objekt, který obsahuje podrobnosti o `event`.</span><span class="sxs-lookup"><span data-stu-id="c6440-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6440-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c6440-108">Return Value</span></span>  
  
|<span data-ttu-id="c6440-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6440-109">HRESULT</span></span>|<span data-ttu-id="c6440-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c6440-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6440-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6440-111">S_OK</span></span>|<span data-ttu-id="c6440-112">`OnEvent` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c6440-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c6440-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6440-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6440-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c6440-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6440-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6440-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6440-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c6440-116">The call timed out.</span></span>|  
|<span data-ttu-id="c6440-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6440-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6440-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c6440-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6440-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6440-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6440-120">Událost byla zrušena při čekání na blokované vlákno nebo vláknu.</span><span class="sxs-lookup"><span data-stu-id="c6440-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6440-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c6440-121">E_FAIL</span></span>|<span data-ttu-id="c6440-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c6440-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6440-123">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="c6440-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6440-124">Následná volání libovolné metody hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c6440-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6440-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6440-125">Remarks</span></span>  
 <span data-ttu-id="c6440-126">Parametr `data` je ukazatel na objekt neurčeného typu.</span><span class="sxs-lookup"><span data-stu-id="c6440-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="c6440-127">Pokud je parametr `event` `Event_DomainUnload`, `data` číselným identifikátorem <xref:System.AppDomain>, který byl uvolněn.</span><span class="sxs-lookup"><span data-stu-id="c6440-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="c6440-128">Hostitel může provést odpovídající akci s použitím tohoto identifikátoru jako klíče.</span><span class="sxs-lookup"><span data-stu-id="c6440-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="c6440-129">Pokud je `event` `Event_MDAFired`, `data` je ukazatel na instanci [MDAInfo –](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) , která obsahuje výstup zprávy z pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="c6440-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="c6440-130">MDA jsou funkcí CLR, které vývojářům umožňují ladit, generováním zpráv XML o událostech, které jsou jinak obtížné zachytit.</span><span class="sxs-lookup"><span data-stu-id="c6440-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="c6440-131">Tyto zprávy mohou být obzvláště užitečné při ladění přechodů mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="c6440-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="c6440-132">Další informace najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="c6440-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6440-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6440-133">Requirements</span></span>  
 <span data-ttu-id="c6440-134">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6440-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6440-135">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c6440-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6440-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c6440-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6440-137">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6440-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6440-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6440-138">See also</span></span>

- [<span data-ttu-id="c6440-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c6440-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c6440-140">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="c6440-140">EClrEvent Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/eclrevent-enumeration.md)
- [<span data-ttu-id="c6440-141">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6440-141">IActionOnCLREvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)
- [<span data-ttu-id="c6440-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6440-142">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="c6440-143">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6440-143">ICLROnEventManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)
- [<span data-ttu-id="c6440-144">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="c6440-144">MDAInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/mdainfo-structure.md)
