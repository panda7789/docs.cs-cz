---
title: IHostCrst::TryEnter – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 08e4c395026a743323b40e5b1ace3db64e368078
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087251"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="122f7-102">IHostCrst::TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="122f7-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="122f7-103">Pokusí se zadejte kritický oddíl reprezentované aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="122f7-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="122f7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="122f7-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="122f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="122f7-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="122f7-106">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty označující, jaká akce by hostitele zabrat Pokud operace bloky.</span><span class="sxs-lookup"><span data-stu-id="122f7-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="122f7-107">[out] `true` Pokud kritický oddíl lze zadat; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="122f7-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="122f7-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="122f7-108">Return Value</span></span>  
  
|<span data-ttu-id="122f7-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="122f7-109">HRESULT</span></span>|<span data-ttu-id="122f7-110">Popis</span><span class="sxs-lookup"><span data-stu-id="122f7-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="122f7-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="122f7-111">S_OK</span></span>|<span data-ttu-id="122f7-112">`TryEnter` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="122f7-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="122f7-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="122f7-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="122f7-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="122f7-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="122f7-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="122f7-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="122f7-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="122f7-116">The call timed out.</span></span>|  
|<span data-ttu-id="122f7-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="122f7-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="122f7-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="122f7-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="122f7-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="122f7-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="122f7-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="122f7-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="122f7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="122f7-121">E_FAIL</span></span>|<span data-ttu-id="122f7-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="122f7-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="122f7-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="122f7-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="122f7-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="122f7-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="122f7-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="122f7-125">Remarks</span></span>  
 <span data-ttu-id="122f7-126">`TryEnter` Vrátí hodnotu okamžitě a označuje, zda volající vlákno zadány kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="122f7-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="122f7-127">Tato metoda zrcadlí Wind32 `TryEnterCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="122f7-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="122f7-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="122f7-128">Requirements</span></span>  
 <span data-ttu-id="122f7-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="122f7-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="122f7-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="122f7-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="122f7-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="122f7-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="122f7-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="122f7-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="122f7-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="122f7-133">See also</span></span>

- [<span data-ttu-id="122f7-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="122f7-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="122f7-135">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="122f7-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="122f7-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="122f7-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
