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
ms.openlocfilehash: e9c463b055f5bd7d965e2df9428ee7c4a1e612dd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675228"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="a16ca-102">IHostCrst::TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="a16ca-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="a16ca-103">Pokusí se zadejte kritický oddíl reprezentované aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="a16ca-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a16ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a16ca-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a16ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a16ca-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="a16ca-106">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty označující, jaká akce by hostitele zabrat Pokud operace bloky.</span><span class="sxs-lookup"><span data-stu-id="a16ca-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="a16ca-107">[out] `true` Pokud kritický oddíl lze zadat; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="a16ca-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a16ca-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a16ca-108">Return Value</span></span>  
  
|<span data-ttu-id="a16ca-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a16ca-109">HRESULT</span></span>|<span data-ttu-id="a16ca-110">Popis</span><span class="sxs-lookup"><span data-stu-id="a16ca-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a16ca-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a16ca-111">S_OK</span></span>|<span data-ttu-id="a16ca-112">`TryEnter` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a16ca-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="a16ca-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a16ca-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a16ca-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a16ca-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a16ca-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a16ca-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a16ca-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a16ca-116">The call timed out.</span></span>|  
|<span data-ttu-id="a16ca-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a16ca-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a16ca-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="a16ca-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a16ca-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a16ca-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a16ca-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="a16ca-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a16ca-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a16ca-121">E_FAIL</span></span>|<span data-ttu-id="a16ca-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="a16ca-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a16ca-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a16ca-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a16ca-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a16ca-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a16ca-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a16ca-125">Remarks</span></span>  
 <span data-ttu-id="a16ca-126">`TryEnter` Vrátí hodnotu okamžitě a označuje, zda volající vlákno zadány kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="a16ca-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="a16ca-127">Tato metoda zrcadlí Wind32 `TryEnterCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="a16ca-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a16ca-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a16ca-128">Requirements</span></span>  
 <span data-ttu-id="a16ca-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a16ca-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a16ca-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a16ca-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a16ca-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a16ca-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a16ca-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a16ca-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a16ca-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a16ca-133">See also</span></span>
- [<span data-ttu-id="a16ca-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a16ca-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="a16ca-135">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a16ca-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="a16ca-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a16ca-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
