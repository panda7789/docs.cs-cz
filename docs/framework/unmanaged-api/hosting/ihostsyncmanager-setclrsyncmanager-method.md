---
title: "IHostSyncManager::SetCLRSyncManager – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostSyncManager.SetCLRSyncManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45899e3cb6a08aef6a9b8df197541c4d0233d92d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="dcdd8-102">IHostSyncManager::SetCLRSyncManager – metoda</span><span class="sxs-lookup"><span data-stu-id="dcdd8-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="dcdd8-103">Nastaví [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance přidružení k aktuální [ihostsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcdd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcdd8-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dcdd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dcdd8-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="dcdd8-106">[v] Ukazatel na `ICLRSyncManager` instance poskytl common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="dcdd8-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dcdd8-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dcdd8-107">Return Value</span></span>  
  
|<span data-ttu-id="dcdd8-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dcdd8-108">HRESULT</span></span>|<span data-ttu-id="dcdd8-109">Popis</span><span class="sxs-lookup"><span data-stu-id="dcdd8-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dcdd8-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dcdd8-110">S_OK</span></span>|<span data-ttu-id="dcdd8-111">`SetCLRSyncManager`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="dcdd8-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dcdd8-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dcdd8-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dcdd8-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dcdd8-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dcdd8-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-115">The call timed out.</span></span>|  
|<span data-ttu-id="dcdd8-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dcdd8-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dcdd8-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dcdd8-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dcdd8-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dcdd8-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dcdd8-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dcdd8-120">E_FAIL</span></span>|<span data-ttu-id="dcdd8-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dcdd8-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dcdd8-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcdd8-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcdd8-124">Remarks</span></span>  
 <span data-ttu-id="dcdd8-125">Usnadňuje komunikaci mezi hostitelem a modulu CLR rozhraní hostování obecně pocházet v párech.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="dcdd8-126">Jeden člen, které odpovídá páru je implementováno modulem hostitele a jiné člen je implementováno modulem modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="dcdd8-127">Jako na straně hostitele implementace `IHostSyncManager` rozhraní odpovídá `ICLRSyncManager` rozhraní implementované modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="dcdd8-128">Volání CLR `SetCLRSyncManager` k poskytování `ICLRSyncManager` instance pro hostitele, který chcete přidružit k aktuální `IHostSyncManager` instance.</span><span class="sxs-lookup"><span data-stu-id="dcdd8-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcdd8-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcdd8-129">Requirements</span></span>  
 <span data-ttu-id="dcdd8-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcdd8-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcdd8-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dcdd8-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcdd8-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dcdd8-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcdd8-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcdd8-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcdd8-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="dcdd8-134">See Also</span></span>  
 [<span data-ttu-id="dcdd8-135">Iclrsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcdd8-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 [<span data-ttu-id="dcdd8-136">Ihostsyncmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcdd8-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
