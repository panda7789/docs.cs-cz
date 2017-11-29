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
ms.openlocfilehash: c6b622666c3bda806c77329d0d0a10726b4838c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="f5436-102">IHostCrst::TryEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="f5436-102">IHostCrst::TryEnter Method</span></span>
<span data-ttu-id="f5436-103">Pokusí se zadejte kritická sekce reprezentována aktuální [ihostcrst –](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="f5436-103">Attempts to enter the critical section represented by the current [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5436-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5436-104">Syntax</span></span>  
  
```  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5436-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f5436-105">Parameters</span></span>  
 `option`  
 <span data-ttu-id="f5436-106">[v] Jeden z [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) hodnoty, která určuje, jaké akce hostitele by měla přijmout, pokud operace bloky.</span><span class="sxs-lookup"><span data-stu-id="f5436-106">[in] One of the [WAIT_OPTION](../../../../docs/framework/unmanaged-api/hosting/wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="f5436-107">[out] `true` Pokud kritická sekce lze zadat; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="f5436-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5436-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f5436-108">Return Value</span></span>  
  
|<span data-ttu-id="f5436-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5436-109">HRESULT</span></span>|<span data-ttu-id="f5436-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f5436-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5436-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5436-111">S_OK</span></span>|<span data-ttu-id="f5436-112">`TryEnter`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f5436-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="f5436-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5436-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5436-114">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f5436-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5436-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5436-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5436-116">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f5436-116">The call timed out.</span></span>|  
|<span data-ttu-id="f5436-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5436-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5436-118">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="f5436-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5436-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5436-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5436-120">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="f5436-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5436-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5436-121">E_FAIL</span></span>|<span data-ttu-id="f5436-122">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="f5436-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5436-123">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f5436-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5436-124">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5436-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5436-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5436-125">Remarks</span></span>  
 <span data-ttu-id="f5436-126">`TryEnter`Vrátí okamžitě a označuje, zda volající vlákno zadány kritická sekce.</span><span class="sxs-lookup"><span data-stu-id="f5436-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="f5436-127">Tato metoda odpovídá Wind32 `TryEnterCriticalSection` funkce.</span><span class="sxs-lookup"><span data-stu-id="f5436-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5436-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5436-128">Requirements</span></span>  
 <span data-ttu-id="f5436-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5436-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5436-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5436-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5436-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f5436-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5436-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5436-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5436-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5436-133">See Also</span></span>  
 [<span data-ttu-id="f5436-134">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5436-134">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="f5436-135">Ihostcrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5436-135">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 [<span data-ttu-id="f5436-136">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5436-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
