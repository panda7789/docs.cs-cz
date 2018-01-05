---
title: "IHostCrst::TryEnter – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostCrst.TryEnter
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1ddec99069e3cd7777e45031e7f0e8d3eabeccd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="35d5e-102">IHostCrst::TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="35d5e-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="35d5e-103">Pokusí se zadejte kritická sekce reprezentována aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="35d5e-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35d5e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35d5e-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35d5e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35d5e-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="35d5e-106">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty, která určuje, jaké akce hostitele by měla přijmout, pokud operace bloky.</span><span class="sxs-lookup"><span data-stu-id="35d5e-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="35d5e-107">[out] `true` Pokud kritická sekce lze zadat; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="35d5e-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="35d5e-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="35d5e-108">Return Value</span></span>  
  
|<span data-ttu-id="35d5e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="35d5e-109">HRESULT</span></span>|<span data-ttu-id="35d5e-110">Popis</span><span class="sxs-lookup"><span data-stu-id="35d5e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="35d5e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="35d5e-111">S_OK</span></span>|<span data-ttu-id="35d5e-112">`TryEnter`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="35d5e-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="35d5e-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="35d5e-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="35d5e-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="35d5e-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="35d5e-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="35d5e-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="35d5e-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="35d5e-116">The call timed out.</span></span>|  
|<span data-ttu-id="35d5e-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="35d5e-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="35d5e-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="35d5e-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="35d5e-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="35d5e-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="35d5e-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="35d5e-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="35d5e-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="35d5e-121">E_FAIL</span></span>|<span data-ttu-id="35d5e-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="35d5e-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="35d5e-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="35d5e-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="35d5e-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="35d5e-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35d5e-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35d5e-125">Remarks</span></span>  
 <span data-ttu-id="35d5e-126">`TryEnter`Vrátí okamžitě a označuje, zda volající vlákno zadány kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="35d5e-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="35d5e-127">Tato metoda odpovídá Wind32 `TryEnterCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="35d5e-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35d5e-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35d5e-128">Requirements</span></span>  
 <span data-ttu-id="35d5e-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35d5e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35d5e-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="35d5e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="35d5e-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="35d5e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="35d5e-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35d5e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35d5e-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="35d5e-133">See Also</span></span>  
 [<span data-ttu-id="35d5e-134">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35d5e-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="35d5e-135">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35d5e-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="35d5e-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35d5e-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
