---
title: "ICLRTaskManager::SetLocale – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRTaskManager.SetLocale
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bbed6bff52d7ccad38eb45d12a31d08dc8b1b774
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="664cc-102">ICLRTaskManager::SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="664cc-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="664cc-103">Upozorní common language runtime (CLR), aby hostitel změnil hodnotu identifikátoru národního prostředí (která se mapuje na zeměpisné jazykovou verzi a jazyk) na aktuálně spuštěné úlohy.</span><span class="sxs-lookup"><span data-stu-id="664cc-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="664cc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="664cc-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="664cc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="664cc-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="664cc-106">[v] Hodnota identifikátoru národního prostředí, která se mapuje na nově přiřazené zeměpisné jazykovou verzi a jazyka.</span><span class="sxs-lookup"><span data-stu-id="664cc-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="664cc-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="664cc-107">Return Value</span></span>  
  
|<span data-ttu-id="664cc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="664cc-108">HRESULT</span></span>|<span data-ttu-id="664cc-109">Popis</span><span class="sxs-lookup"><span data-stu-id="664cc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="664cc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="664cc-110">S_OK</span></span>|<span data-ttu-id="664cc-111">Metoda úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="664cc-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="664cc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="664cc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="664cc-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="664cc-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="664cc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="664cc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="664cc-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="664cc-115">The call timed out.</span></span>|  
|<span data-ttu-id="664cc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="664cc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="664cc-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="664cc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="664cc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="664cc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="664cc-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="664cc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="664cc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="664cc-120">E_FAIL</span></span>|<span data-ttu-id="664cc-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="664cc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="664cc-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="664cc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="664cc-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="664cc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="664cc-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="664cc-124">Remarks</span></span>  
 <span data-ttu-id="664cc-125">`SetLocale`poskytuje hostitele příležitost provést nějaké mechanismy, které může mít pro synchronizaci národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="664cc-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="664cc-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="664cc-126">Requirements</span></span>  
 <span data-ttu-id="664cc-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="664cc-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="664cc-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="664cc-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="664cc-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="664cc-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="664cc-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="664cc-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="664cc-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="664cc-131">See Also</span></span>  
 [<span data-ttu-id="664cc-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="664cc-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="664cc-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="664cc-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="664cc-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="664cc-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="664cc-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="664cc-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
