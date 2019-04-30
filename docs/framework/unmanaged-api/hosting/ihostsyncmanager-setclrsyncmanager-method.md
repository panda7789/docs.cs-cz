---
title: IHostSyncManager::SetCLRSyncManager – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5006e171e2d5bbdd0d9d4a484299b1860c079b3f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789555"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="c4ba5-102">IHostSyncManager::SetCLRSyncManager – metoda</span><span class="sxs-lookup"><span data-stu-id="c4ba5-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="c4ba5-103">Nastaví [iclrsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instanci přidružit s aktuálním [ihostsyncmanager –](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-103">Sets the [ICLRSyncManager](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ba5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4ba5-104">Syntax</span></span>  
  
```  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c4ba5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c4ba5-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="c4ba5-106">[in] Ukazatel `ICLRSyncManager` instance zadané modulem common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c4ba5-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c4ba5-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c4ba5-107">Return Value</span></span>  
  
|<span data-ttu-id="c4ba5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c4ba5-108">HRESULT</span></span>|<span data-ttu-id="c4ba5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="c4ba5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c4ba5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c4ba5-110">S_OK</span></span>|<span data-ttu-id="c4ba5-111">`SetCLRSyncManager` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="c4ba5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c4ba5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c4ba5-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c4ba5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c4ba5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c4ba5-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-115">The call timed out.</span></span>|  
|<span data-ttu-id="c4ba5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c4ba5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c4ba5-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c4ba5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c4ba5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c4ba5-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c4ba5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c4ba5-120">E_FAIL</span></span>|<span data-ttu-id="c4ba5-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c4ba5-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c4ba5-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4ba5-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4ba5-124">Remarks</span></span>  
 <span data-ttu-id="c4ba5-125">Usnadňuje komunikaci mezi hostitelem a CLR hostitelských rozhraní obecně mít dvojice.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="c4ba5-126">Jednoho člena, které odpovídá páru je implementováno hostitele a jiný člen je implementováno modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="c4ba5-127">Jako na straně hostitele implementace `IHostSyncManager` rozhraní odpovídá `ICLRSyncManager` rozhraní implementované CLR.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="c4ba5-128">Volání CLR `SetCLRSyncManager` slouží k poskytování `ICLRSyncManager` instance hostitele pro přidružení k aktuální `IHostSyncManager` instance.</span><span class="sxs-lookup"><span data-stu-id="c4ba5-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4ba5-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4ba5-129">Requirements</span></span>  
 <span data-ttu-id="c4ba5-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4ba5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4ba5-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c4ba5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c4ba5-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4ba5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4ba5-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4ba5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ba5-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4ba5-134">See also</span></span>

- [<span data-ttu-id="c4ba5-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4ba5-135">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="c4ba5-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4ba5-136">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
