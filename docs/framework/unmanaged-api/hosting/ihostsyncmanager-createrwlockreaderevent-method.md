---
title: "IHostSyncManager::CreateRWLockReaderEvent – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.CreateRWLockReaderEvent
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a783f4511e27b5d230a90444e5a91b34327543cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="e338b-102">IHostSyncManager::CreateRWLockReaderEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="e338b-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="e338b-103">Vytvoří objekt Ruční vynulování události pro implementaci zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e338b-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e338b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e338b-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e338b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e338b-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="e338b-106">[v] `true`, pokud `ppEvent` signalizovaného; jinak, by měla být `false`.</span><span class="sxs-lookup"><span data-stu-id="e338b-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="e338b-107">[v] Soubor cookie přidružit zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e338b-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="e338b-108">[out] Ukazatel na adresu [ihostmanualevent –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt událostí.</span><span class="sxs-lookup"><span data-stu-id="e338b-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e338b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e338b-109">Return Value</span></span>  
  
|<span data-ttu-id="e338b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e338b-110">HRESULT</span></span>|<span data-ttu-id="e338b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="e338b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e338b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="e338b-112">S_OK</span></span>|<span data-ttu-id="e338b-113">`CreateRWLockReaderEvent`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e338b-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="e338b-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e338b-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e338b-115">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e338b-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e338b-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e338b-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e338b-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e338b-117">The call timed out.</span></span>|  
|<span data-ttu-id="e338b-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e338b-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e338b-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e338b-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e338b-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e338b-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e338b-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e338b-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e338b-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e338b-122">E_FAIL</span></span>|<span data-ttu-id="e338b-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e338b-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e338b-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e338b-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e338b-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e338b-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="e338b-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="e338b-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="e338b-127">Nedostatek paměti nebylo k dispozici k vytvoření objektu požadovaná událost.</span><span class="sxs-lookup"><span data-stu-id="e338b-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e338b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e338b-128">Remarks</span></span>  
 <span data-ttu-id="e338b-129">Volání CLR `CreateRWLockReaderEvent` získat odkaz na `IHostManualEvent` instance pro použití v jeho implementaci zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="e338b-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="e338b-130">Hostitele můžete použít soubor cookie k určení úkoly, které čekají na zámek pro čtení pomocí dotazu [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e338b-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e338b-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e338b-131">Requirements</span></span>  
 <span data-ttu-id="e338b-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e338b-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e338b-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e338b-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e338b-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e338b-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e338b-135">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e338b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e338b-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="e338b-136">See Also</span></span>  
 [<span data-ttu-id="e338b-137">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e338b-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="e338b-138">Ihostautoevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e338b-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="e338b-139">Ihostmanualevent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e338b-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="e338b-140">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e338b-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
