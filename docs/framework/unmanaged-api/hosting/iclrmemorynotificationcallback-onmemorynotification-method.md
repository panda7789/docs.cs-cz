---
title: ICLRMemoryNotificationCallback::OnMemoryNotification – metoda
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
ms.openlocfilehash: d88abcc523eca06c8ec50cac2d2984b26099174a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703786"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="b75ef-102">ICLRMemoryNotificationCallback::OnMemoryNotification – metoda</span><span class="sxs-lookup"><span data-stu-id="b75ef-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="b75ef-103">Upozorňuje modul CLR (Common Language Runtime) na zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="b75ef-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b75ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b75ef-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b75ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b75ef-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="b75ef-106">pro Jedna z hodnot [EMemoryAvailable –](ememoryavailable-enumeration.md) , která označuje tlak na paměť, na kterém je počítač v současné době.</span><span class="sxs-lookup"><span data-stu-id="b75ef-106">[in] One of the [EMemoryAvailable](ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b75ef-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b75ef-107">Return Value</span></span>  
  
|<span data-ttu-id="b75ef-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b75ef-108">HRESULT</span></span>|<span data-ttu-id="b75ef-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b75ef-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b75ef-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b75ef-110">S_OK</span></span>|<span data-ttu-id="b75ef-111">`OnMemoryNotification`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="b75ef-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="b75ef-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b75ef-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b75ef-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b75ef-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b75ef-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b75ef-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b75ef-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b75ef-115">The call timed out.</span></span>|  
|<span data-ttu-id="b75ef-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b75ef-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b75ef-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b75ef-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b75ef-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b75ef-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b75ef-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b75ef-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b75ef-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b75ef-120">E_FAIL</span></span>|<span data-ttu-id="b75ef-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b75ef-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b75ef-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="b75ef-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b75ef-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b75ef-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b75ef-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b75ef-124">Remarks</span></span>  
 <span data-ttu-id="b75ef-125">Modul CLR zaregistruje zpětné volání do pomocí `OnMemoryNotification` volání metody [IHostMemoryManager:: RegisterMemoryNotificationCallback –](ihostmemorymanager-registermemorynotificationcallback-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b75ef-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="b75ef-126">Modul runtime používá informace vrácené ve zpětném volání k uvolnění další paměti, pokud hostitel hlásí, že paměťové prostředky mají nízký provoz.</span><span class="sxs-lookup"><span data-stu-id="b75ef-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b75ef-127">Volání `OnMemoryNotification` nikdy neblokuje.</span><span class="sxs-lookup"><span data-stu-id="b75ef-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="b75ef-128">Vždycky se vrátí hned.</span><span class="sxs-lookup"><span data-stu-id="b75ef-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b75ef-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b75ef-129">Requirements</span></span>  
 <span data-ttu-id="b75ef-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b75ef-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b75ef-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b75ef-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b75ef-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b75ef-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b75ef-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b75ef-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b75ef-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b75ef-134">See also</span></span>

- [<span data-ttu-id="b75ef-135">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b75ef-135">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="b75ef-136">RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="b75ef-136">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="b75ef-137">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b75ef-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
