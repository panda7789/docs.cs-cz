---
title: "IHostSyncManager::CreateRWLockReaderEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6b583e7b5dd1a83ecb891591c25802ae257ad7c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="205cf-102">IHostSyncManager::CreateRWLockReaderEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="205cf-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="205cf-103">Vytvoří objekt Ruční vynulování události pro implementaci zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="205cf-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="205cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="205cf-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="205cf-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="205cf-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="205cf-106">[v] `true`, pokud `ppEvent` signalizovaného; jinak, by měla být `false`.</span><span class="sxs-lookup"><span data-stu-id="205cf-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="205cf-107">[v] Soubor cookie přidružit zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="205cf-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="205cf-108">[out] Ukazatel na adresu [ihostmanualevent –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt událostí.</span><span class="sxs-lookup"><span data-stu-id="205cf-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="205cf-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="205cf-109">Return Value</span></span>  
  
|<span data-ttu-id="205cf-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="205cf-110">HRESULT</span></span>|<span data-ttu-id="205cf-111">Popis</span><span class="sxs-lookup"><span data-stu-id="205cf-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="205cf-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="205cf-112">S_OK</span></span>|<span data-ttu-id="205cf-113">`CreateRWLockReaderEvent`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="205cf-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="205cf-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="205cf-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="205cf-115">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="205cf-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="205cf-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="205cf-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="205cf-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="205cf-117">The call timed out.</span></span>|  
|<span data-ttu-id="205cf-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="205cf-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="205cf-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="205cf-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="205cf-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="205cf-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="205cf-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="205cf-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="205cf-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="205cf-122">E_FAIL</span></span>|<span data-ttu-id="205cf-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="205cf-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="205cf-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="205cf-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="205cf-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="205cf-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="205cf-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="205cf-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="205cf-127">Nedostatek paměti nebylo k dispozici k vytvoření objektu požadovaná událost.</span><span class="sxs-lookup"><span data-stu-id="205cf-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="205cf-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="205cf-128">Remarks</span></span>  
 <span data-ttu-id="205cf-129">Volání CLR `CreateRWLockReaderEvent` získat odkaz na `IHostManualEvent` instance pro použití v jeho implementaci zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="205cf-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="205cf-130">Hostitele můžete použít soubor cookie k určení úkoly, které čekají na zámek pro čtení pomocí dotazu [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="205cf-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="205cf-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="205cf-131">Requirements</span></span>  
 <span data-ttu-id="205cf-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="205cf-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="205cf-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="205cf-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="205cf-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="205cf-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="205cf-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="205cf-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205cf-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="205cf-136">See Also</span></span>  
 [<span data-ttu-id="205cf-137">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="205cf-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="205cf-138">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="205cf-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="205cf-139">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="205cf-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="205cf-140">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="205cf-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
