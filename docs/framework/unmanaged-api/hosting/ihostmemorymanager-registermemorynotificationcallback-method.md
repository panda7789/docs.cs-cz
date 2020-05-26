---
title: IHostMemoryManager::RegisterMemoryNotificationCallback – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.RegisterMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback
helpviewer_keywords:
- IHostMemoryManager::RegisterMemoryNotificationCallback method [.NET Framework hosting]
- RegisterMemoryNotificationCallback method [.NET Framework hosting]
ms.assetid: 65d301f6-4dbb-4b5f-8eff-82540e2b6465
topic_type:
- apiref
ms.openlocfilehash: 0c20df85560f715e829fe02be599788854fcb0f1
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804481"
---
# <a name="ihostmemorymanagerregistermemorynotificationcallback-method"></a><span data-ttu-id="37918-102">IHostMemoryManager::RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="37918-102">IHostMemoryManager::RegisterMemoryNotificationCallback Method</span></span>
<span data-ttu-id="37918-103">Registruje ukazatel na funkci zpětného volání, kterou hostitel vyvolá, aby upozornil na modul CLR (Common Language Runtime) aktuálního zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="37918-103">Registers a pointer to a callback function that the host invokes to notify the common language runtime (CLR) of the current memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37918-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37918-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterMemoryNotificationCallback (  
    [in] ICLRMemoryNotificationCallback* pCallback  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37918-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="37918-105">Parameters</span></span>  
 `pCallback`  
 <span data-ttu-id="37918-106">pro Ukazatel rozhraní na instanci [ICLRMemoryNotificationCallback –](iclrmemorynotificationcallback-interface.md) , která je implementována modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="37918-106">[in] An interface pointer to an [ICLRMemoryNotificationCallback](iclrmemorynotificationcallback-interface.md) instance that is implemented by the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37918-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="37918-107">Return Value</span></span>  
  
|<span data-ttu-id="37918-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37918-108">HRESULT</span></span>|<span data-ttu-id="37918-109">Popis</span><span class="sxs-lookup"><span data-stu-id="37918-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37918-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="37918-110">S_OK</span></span>|<span data-ttu-id="37918-111">`RegisterMemoryNotificationCallback`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="37918-111">`RegisterMemoryNotificationCallback` returned successfully.</span></span>|  
|<span data-ttu-id="37918-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37918-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37918-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="37918-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37918-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37918-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37918-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="37918-115">The call timed out.</span></span>|  
|<span data-ttu-id="37918-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37918-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37918-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="37918-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37918-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37918-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37918-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="37918-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37918-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37918-120">E_FAIL</span></span>|<span data-ttu-id="37918-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="37918-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37918-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="37918-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37918-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="37918-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37918-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37918-124">Remarks</span></span>  
 <span data-ttu-id="37918-125">Vzhledem k tomu `ICLRMemoryNotificationCallback` , že rozhraní definuje pouze jednu metodu ([ICLRMemoryNotificationCallback –:: OnMemoryNotification –](iclrmemorynotificationcallback-onmemorynotification-method.md)) a protože `pCallback` je ukazatel na `ICLRMemoryNotificationCallback` instanci poskytovanou modulem CLR, je registrace pro samotnou funkci zpětného volání efektivní.</span><span class="sxs-lookup"><span data-stu-id="37918-125">Because the `ICLRMemoryNotificationCallback` interface defines only one method ([ICLRMemoryNotificationCallback::OnMemoryNotification](iclrmemorynotificationcallback-onmemorynotification-method.md)), and because `pCallback` is a pointer to an `ICLRMemoryNotificationCallback` instance provided by the CLR, the registration is effectively for the callback function itself.</span></span> <span data-ttu-id="37918-126">Hostitel vyvolá `OnMemoryNotification` hlášení stavů paměti místo použití standardní `CreateMemoryResourceNotification` funkce Win32.</span><span class="sxs-lookup"><span data-stu-id="37918-126">The host invokes `OnMemoryNotification` to report memory pressure conditions, rather than using the standard Win32 `CreateMemoryResourceNotification` function.</span></span> <span data-ttu-id="37918-127">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="37918-127">For more information, see the Windows Platform documentation.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="37918-128">Volání `OnMemoryNotification` nikdy neblokuje.</span><span class="sxs-lookup"><span data-stu-id="37918-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="37918-129">Vždycky se vrátí hned.</span><span class="sxs-lookup"><span data-stu-id="37918-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37918-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37918-130">Requirements</span></span>  
 <span data-ttu-id="37918-131">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37918-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37918-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="37918-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37918-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="37918-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37918-134">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37918-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37918-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="37918-135">See also</span></span>

- [<span data-ttu-id="37918-136">ICLRMemoryNotificationCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37918-136">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
- [<span data-ttu-id="37918-137">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37918-137">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
