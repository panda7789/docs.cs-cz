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
ms.openlocfilehash: 64cf6c80ab1cf4b3ca52c60d6e72b54c438f9f4a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73195842"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="3fd6b-102">IHostSyncManager::CreateRWLockReaderEvent – metoda</span><span class="sxs-lookup"><span data-stu-id="3fd6b-102">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>
<span data-ttu-id="3fd6b-103">Vytvoří objekt události ručního resetování pro implementaci zámku čtecího modulu.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-103">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fd6b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3fd6b-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fd6b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3fd6b-105">Parameters</span></span>  
 `bInitialState`  
 <span data-ttu-id="3fd6b-106">[in] `true`, pokud by `ppEvent` mělo být signalizace; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-106">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="3fd6b-107">pro Soubor cookie, který se má přidružit k zámku čtečky.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-107">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="3fd6b-108">mimo Ukazatel na adresu instance [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) nebo hodnotu null, pokud objekt události nelze vytvořit.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-108">[out] A pointer to the address of an [IHostManualEvent](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fd6b-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3fd6b-109">Return Value</span></span>  
  
|<span data-ttu-id="3fd6b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3fd6b-110">HRESULT</span></span>|<span data-ttu-id="3fd6b-111">Popis</span><span class="sxs-lookup"><span data-stu-id="3fd6b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3fd6b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="3fd6b-112">S_OK</span></span>|<span data-ttu-id="3fd6b-113">`CreateRWLockReaderEvent` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-113">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="3fd6b-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3fd6b-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3fd6b-115">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3fd6b-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3fd6b-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3fd6b-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-117">The call timed out.</span></span>|  
|<span data-ttu-id="3fd6b-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3fd6b-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3fd6b-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3fd6b-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3fd6b-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3fd6b-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3fd6b-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3fd6b-122">E_FAIL</span></span>|<span data-ttu-id="3fd6b-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3fd6b-124">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3fd6b-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3fd6b-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="3fd6b-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="3fd6b-127">Pro vytvoření požadovaného objektu události není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-127">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3fd6b-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3fd6b-128">Remarks</span></span>  
 <span data-ttu-id="3fd6b-129">Modul CLR volá `CreateRWLockReaderEvent`, aby získal odkaz na instanci `IHostManualEvent`, která se má použít při implementaci zámku čtecího modulu.</span><span class="sxs-lookup"><span data-stu-id="3fd6b-129">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="3fd6b-130">Hostitel může pomocí souboru cookie určit, které úlohy čekají na zámek čtečky, pomocí dotazování rozhraní [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="3fd6b-130">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fd6b-131">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3fd6b-131">Requirements</span></span>  
 <span data-ttu-id="3fd6b-132">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fd6b-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fd6b-133">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3fd6b-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3fd6b-134">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3fd6b-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3fd6b-135">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fd6b-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fd6b-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3fd6b-136">See also</span></span>

- [<span data-ttu-id="3fd6b-137">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fd6b-137">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="3fd6b-138">IHostAutoEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fd6b-138">IHostAutoEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)
- [<span data-ttu-id="3fd6b-139">IHostManualEvent – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fd6b-139">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="3fd6b-140">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3fd6b-140">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
