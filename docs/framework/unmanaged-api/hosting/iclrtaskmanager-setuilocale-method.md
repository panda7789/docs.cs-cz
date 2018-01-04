---
title: "ICLRTaskManager::SetUILocale – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.SetUILocale
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fab9da8f7e63ad000595378f5bc36f3aadc2ac3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="e338f-102">ICLRTaskManager::SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="e338f-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="e338f-103">Modul CLR (CLR), aby hostitel byl upraven, národní prostředí uživatelského rozhraní (UI) nebo jazykovou verzi, upozorní na aktuálně spuštěné úlohy.</span><span class="sxs-lookup"><span data-stu-id="e338f-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e338f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e338f-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e338f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e338f-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="e338f-106">[v] Hodnota identifikátoru národního prostředí, která se mapuje na nově přiřazené zeměpisné jazykovou verzi a jazyk uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e338f-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e338f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e338f-107">Return Value</span></span>  
  
|<span data-ttu-id="e338f-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e338f-108">HRESULT</span></span>|<span data-ttu-id="e338f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="e338f-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e338f-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="e338f-110">S_OK</span></span>|<span data-ttu-id="e338f-111">`SetUILocale`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="e338f-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="e338f-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e338f-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e338f-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="e338f-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e338f-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e338f-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e338f-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="e338f-115">The call timed out.</span></span>|  
|<span data-ttu-id="e338f-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e338f-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e338f-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="e338f-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e338f-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e338f-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e338f-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="e338f-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e338f-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e338f-120">E_FAIL</span></span>|<span data-ttu-id="e338f-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="e338f-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e338f-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="e338f-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e338f-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="e338f-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e338f-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e338f-124">Remarks</span></span>  
 <span data-ttu-id="e338f-125">`SetUILocale`poskytuje možnost pro hostitele k provedení nějaké mechanismy, které může mít pro synchronizaci národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="e338f-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e338f-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e338f-126">Requirements</span></span>  
 <span data-ttu-id="e338f-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e338f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e338f-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e338f-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e338f-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e338f-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e338f-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e338f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e338f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="e338f-131">See Also</span></span>  
 [<span data-ttu-id="e338f-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e338f-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="e338f-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e338f-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="e338f-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e338f-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="e338f-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e338f-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
