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
ms.openlocfilehash: bbf5e299285071ba6d43fd2c40fc724d19bc7b2a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504352"
---
# <a name="iactiononclreventonevent-method"></a><span data-ttu-id="c800e-102">IActionOnCLREvent::OnEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="c800e-102">IActionOnCLREvent::OnEvent Method</span></span>
<span data-ttu-id="c800e-103">Provádí zpětná volání pro události, které byly zaregistrovány pomocí volání metody [ICLROnEventManager:: RegisterActionOnEvent –](iclroneventmanager-registeractiononevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c800e-103">Performs callbacks on events that have been registered by using a call to the [ICLROnEventManager::RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c800e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c800e-104">Syntax</span></span>  
  
```cpp  
HRESULT OnEvent (  
    [in] EClrEvent event,  
    [in] PVOID     data  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c800e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c800e-105">Parameters</span></span>  
 `event`  
 <span data-ttu-id="c800e-106">pro Jedna z hodnot [EClrEvent –](eclrevent-enumeration.md) , která označuje typ události.</span><span class="sxs-lookup"><span data-stu-id="c800e-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, which indicates the type of event.</span></span>  
  
 `data`  
 <span data-ttu-id="c800e-107">pro Ukazatel na objekt, který obsahuje podrobnosti o `event` .</span><span class="sxs-lookup"><span data-stu-id="c800e-107">[in] A pointer to an object that contains details about `event`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c800e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c800e-108">Return Value</span></span>  
  
|<span data-ttu-id="c800e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c800e-109">HRESULT</span></span>|<span data-ttu-id="c800e-110">Description</span><span class="sxs-lookup"><span data-stu-id="c800e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c800e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c800e-111">S_OK</span></span>|<span data-ttu-id="c800e-112">`OnEvent`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c800e-112">`OnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="c800e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c800e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c800e-114">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c800e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c800e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c800e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c800e-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c800e-116">The call timed out.</span></span>|  
|<span data-ttu-id="c800e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c800e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c800e-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c800e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c800e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c800e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c800e-120">Událost byla zrušena při čekání na blokované vlákno nebo vláknu.</span><span class="sxs-lookup"><span data-stu-id="c800e-120">An event was cancelled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c800e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c800e-121">E_FAIL</span></span>|<span data-ttu-id="c800e-122">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="c800e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c800e-123">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="c800e-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c800e-124">Následná volání libovolné metody hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c800e-124">Subsequent calls to any hosting method return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c800e-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c800e-125">Remarks</span></span>  
 <span data-ttu-id="c800e-126">`data`Parametr je ukazatel na objekt neurčeného typu.</span><span class="sxs-lookup"><span data-stu-id="c800e-126">The `data` parameter is a pointer to an object of unspecified type.</span></span> <span data-ttu-id="c800e-127">Pokud `event` je parametr `Event_DomainUnload` , `data` je číselný identifikátor pro <xref:System.AppDomain> , který byl uvolněn.</span><span class="sxs-lookup"><span data-stu-id="c800e-127">If the `event` parameter is `Event_DomainUnload`, `data` is the numeric identifier for the <xref:System.AppDomain> that was unloaded.</span></span> <span data-ttu-id="c800e-128">Hostitel může provést odpovídající akci s použitím tohoto identifikátoru jako klíče.</span><span class="sxs-lookup"><span data-stu-id="c800e-128">The host can take appropriate action using this identifier as a key.</span></span>  
  
 <span data-ttu-id="c800e-129">Pokud `event` je `Event_MDAFired` , `data` je ukazatel na instanci [MDAInfo –](mdainfo-structure.md) , která obsahuje výstup zprávy z pomocníka spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="c800e-129">If `event` is `Event_MDAFired`, `data` is a pointer to an [MDAInfo](mdainfo-structure.md) instance that contains the message output from a Managed Debugging Assistant (MDA).</span></span> <span data-ttu-id="c800e-130">MDA jsou funkcí CLR, které vývojářům umožňují ladit, generováním zpráv XML o událostech, které jsou jinak obtížné zachytit.</span><span class="sxs-lookup"><span data-stu-id="c800e-130">MDAs are a feature of the CLR that help developers with debugging, by generating XML messages about events that are otherwise difficult to trap.</span></span> <span data-ttu-id="c800e-131">Tyto zprávy mohou být obzvláště užitečné při ladění přechodů mezi spravovaným a nespravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="c800e-131">Such messages can be especially useful in debugging transitions between managed and unmanaged code.</span></span> <span data-ttu-id="c800e-132">Další informace najdete v tématu [Diagnostikování chyb pomocí asistentů spravovaného ladění](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span><span class="sxs-lookup"><span data-stu-id="c800e-132">For more information, see [Diagnosing Errors with Managed Debugging Assistants](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c800e-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c800e-133">Requirements</span></span>  
 <span data-ttu-id="c800e-134">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c800e-134">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c800e-135">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c800e-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c800e-136">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="c800e-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c800e-137">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c800e-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c800e-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c800e-138">See also</span></span>

- [<span data-ttu-id="c800e-139">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="c800e-139">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="c800e-140">EClrEvent – výčet</span><span class="sxs-lookup"><span data-stu-id="c800e-140">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="c800e-141">IActionOnCLREvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c800e-141">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="c800e-142">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c800e-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="c800e-143">ICLROnEventManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c800e-143">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
- [<span data-ttu-id="c800e-144">MDAInfo – struktura</span><span class="sxs-lookup"><span data-stu-id="c800e-144">MDAInfo Structure</span></span>](mdainfo-structure.md)
