---
title: "IHostSyncManager::SetCLRSyncManager – metoda"
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
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fca59f0d2617c6fb244b2b1ed7b5cf46a7d5869f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="6c580-102">IHostSyncManager::SetCLRSyncManager – metoda</span><span class="sxs-lookup"><span data-stu-id="6c580-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="6c580-103">Nastaví [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance přidružení k aktuální [ihostsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="6c580-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c580-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c580-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c580-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c580-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="6c580-106">[v] Ukazatel na `ICLRSyncManager` instance poskytl common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="6c580-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c580-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6c580-107">Return Value</span></span>  
  
|<span data-ttu-id="6c580-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6c580-108">HRESULT</span></span>|<span data-ttu-id="6c580-109">Popis</span><span class="sxs-lookup"><span data-stu-id="6c580-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6c580-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="6c580-110">S_OK</span></span>|<span data-ttu-id="6c580-111">`SetCLRSyncManager`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="6c580-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="6c580-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6c580-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6c580-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="6c580-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6c580-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6c580-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6c580-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="6c580-115">The call timed out.</span></span>|  
|<span data-ttu-id="6c580-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6c580-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6c580-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="6c580-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6c580-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6c580-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6c580-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="6c580-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6c580-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6c580-120">E_FAIL</span></span>|<span data-ttu-id="6c580-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="6c580-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6c580-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="6c580-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6c580-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6c580-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c580-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c580-124">Remarks</span></span>  
 <span data-ttu-id="6c580-125">Usnadňuje komunikaci mezi hostitelem a modulu CLR rozhraní hostování obecně pocházet v párech.</span><span class="sxs-lookup"><span data-stu-id="6c580-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="6c580-126">Jeden člen, které odpovídá páru je implementováno modulem hostitele a jiné člen je implementováno modulem modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6c580-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="6c580-127">Jako na straně hostitele implementace `IHostSyncManager` rozhraní odpovídá `ICLRSyncManager` rozhraní implementované modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6c580-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="6c580-128">Volání CLR `SetCLRSyncManager` k poskytování `ICLRSyncManager` instance pro hostitele, který chcete přidružit k aktuální `IHostSyncManager` instance.</span><span class="sxs-lookup"><span data-stu-id="6c580-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c580-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c580-129">Requirements</span></span>  
 <span data-ttu-id="6c580-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c580-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c580-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c580-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c580-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c580-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c580-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c580-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c580-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c580-134">See Also</span></span>  
 [<span data-ttu-id="6c580-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c580-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="6c580-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c580-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
