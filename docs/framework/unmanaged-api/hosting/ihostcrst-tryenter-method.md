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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087251"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="61419-102">IHostCrst::TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="61419-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="61419-103">Pokusí se zadejte kritický oddíl reprezentované aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="61419-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61419-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61419-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61419-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61419-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="61419-106">[in] Jeden z [wait_option –](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty označující, jaká akce by hostitele zabrat Pokud operace bloky.</span><span class="sxs-lookup"><span data-stu-id="61419-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="61419-107">[out] `true` Pokud kritický oddíl lze zadat; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="61419-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61419-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="61419-108">Return Value</span></span>  
  
|<span data-ttu-id="61419-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61419-109">HRESULT</span></span>|<span data-ttu-id="61419-110">Popis</span><span class="sxs-lookup"><span data-stu-id="61419-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61419-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="61419-111">S_OK</span></span>|`TryEnter` <span data-ttu-id="61419-112">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="61419-112">returned successfully.</span></span>|  
|<span data-ttu-id="61419-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61419-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61419-114">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="61419-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="61419-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="61419-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="61419-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="61419-116">The call timed out.</span></span>|  
|<span data-ttu-id="61419-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="61419-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="61419-118">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="61419-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="61419-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="61419-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="61419-120">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="61419-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="61419-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="61419-121">E_FAIL</span></span>|<span data-ttu-id="61419-122">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="61419-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="61419-123">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="61419-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="61419-124">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="61419-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61419-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61419-125">Remarks</span></span>  
 `TryEnter` <span data-ttu-id="61419-126">Vrátí hodnotu okamžitě a označuje, zda volající vlákno zadány kritický oddíl.</span><span class="sxs-lookup"><span data-stu-id="61419-126">returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="61419-127">Tato metoda zrcadlí Wind32 `TryEnterCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="61419-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61419-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61419-128">Requirements</span></span>  
 <span data-ttu-id="61419-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61419-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61419-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="61419-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61419-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61419-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="61419-132">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="61419-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="61419-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61419-133">See also</span></span>

- [<span data-ttu-id="61419-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61419-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="61419-135">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61419-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="61419-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61419-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
