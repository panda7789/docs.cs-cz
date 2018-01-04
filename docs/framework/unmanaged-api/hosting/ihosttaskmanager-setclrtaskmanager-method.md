---
title: "IHostTaskManager::SetCLRTaskManager – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetCLRTaskManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9f009fee3f9bc439ce61d859759870f9cbb54f09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="e9086-102">IHostTaskManager::SetCLRTaskManager – metoda</span><span class="sxs-lookup"><span data-stu-id="e9086-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="e9086-103">Poskytuje ukazatele rozhraní na hostiteli [iclrtaskmanager –](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implementované common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="e9086-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9086-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9086-104">Syntax</span></span>  
  
```  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e9086-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9086-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="e9086-106">[v] Ukazatel na `ICLRTaskManager` instance implementované modul common language runtime.</span><span class="sxs-lookup"><span data-stu-id="e9086-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e9086-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e9086-107">Return Value</span></span>  
  
|<span data-ttu-id="e9086-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e9086-108">HRESULT</span></span>|<span data-ttu-id="e9086-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e9086-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e9086-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e9086-110">S_OK</span></span>|<span data-ttu-id="e9086-111">`SetCLRTaskManager`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e9086-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="e9086-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e9086-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e9086-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e9086-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e9086-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e9086-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e9086-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e9086-115">The call timed out.</span></span>|  
|<span data-ttu-id="e9086-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e9086-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e9086-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e9086-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e9086-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e9086-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e9086-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e9086-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e9086-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e9086-120">E_FAIL</span></span>|<span data-ttu-id="e9086-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e9086-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e9086-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e9086-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e9086-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e9086-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9086-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9086-124">Remarks</span></span>  
 <span data-ttu-id="e9086-125">Volání modulu runtime `SetCLRTaskManager` poskytnout ukazatele rozhraní na hostiteli `ICLRTaskManager` instance.</span><span class="sxs-lookup"><span data-stu-id="e9086-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9086-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9086-126">Requirements</span></span>  
 <span data-ttu-id="e9086-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9086-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9086-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9086-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9086-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9086-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9086-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9086-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9086-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="e9086-131">See Also</span></span>  
 [<span data-ttu-id="e9086-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9086-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e9086-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9086-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e9086-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9086-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e9086-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9086-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
