---
title: IHostSyncManager::CreateRWLockReaderEvent – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bb2a7a6650da03796628b647bc0b06174c576538
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33447353"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="4d1f0-102">IHostSyncManager::CreateRWLockReaderEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="4d1f0-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="4d1f0-103">Vytvoří objekt Ruční vynulování události pro implementaci zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d1f0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d1f0-104">Syntax</span></span>  
  
```  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d1f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d1f0-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="4d1f0-106">[v] `true`, pokud `ppEvent` signalizovaného; jinak, by měla být `false`.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="4d1f0-107">[v] Soubor cookie přidružit zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="4d1f0-108">[out] Ukazatel na adresu [ihostmanualevent –](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instanci, nebo hodnota null, pokud nelze vytvořit objekt událostí.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4d1f0-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4d1f0-109">Return Value</span></span>  
  
|<span data-ttu-id="4d1f0-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4d1f0-110">HRESULT</span></span>|<span data-ttu-id="4d1f0-111">Popis</span><span class="sxs-lookup"><span data-stu-id="4d1f0-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4d1f0-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="4d1f0-112">S_OK</span></span>|<span data-ttu-id="4d1f0-113">`CreateRWLockReaderEvent` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="4d1f0-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4d1f0-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4d1f0-115">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4d1f0-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4d1f0-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4d1f0-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-117">The call timed out.</span></span>|  
|<span data-ttu-id="4d1f0-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4d1f0-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4d1f0-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4d1f0-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4d1f0-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4d1f0-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4d1f0-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4d1f0-122">E_FAIL</span></span>|<span data-ttu-id="4d1f0-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4d1f0-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4d1f0-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4d1f0-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="4d1f0-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="4d1f0-127">Nedostatek paměti nebylo k dispozici k vytvoření objektu požadovaná událost.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d1f0-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d1f0-128">Remarks</span></span>  
 <span data-ttu-id="4d1f0-129">Volání CLR `CreateRWLockReaderEvent` získat odkaz na `IHostManualEvent` instance pro použití v jeho implementaci zámek pro čtení.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="4d1f0-130">Hostitele můžete použít soubor cookie k určení úkoly, které čekají na zámek pro čtení pomocí dotazu [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4d1f0-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d1f0-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d1f0-131">Requirements</span></span>  
 <span data-ttu-id="4d1f0-132">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d1f0-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d1f0-133">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4d1f0-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4d1f0-134">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4d1f0-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4d1f0-135">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d1f0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d1f0-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d1f0-136">See Also</span></span>  
 [<span data-ttu-id="4d1f0-137">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d1f0-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="4d1f0-138">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d1f0-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 [<span data-ttu-id="4d1f0-139">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d1f0-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 [<span data-ttu-id="4d1f0-140">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d1f0-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
