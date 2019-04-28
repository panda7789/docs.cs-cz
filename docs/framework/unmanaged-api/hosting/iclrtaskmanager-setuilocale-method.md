---
title: ICLRTaskManager::SetUILocale – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetUILocale
helpviewer_keywords:
- ICLRTaskManager::SetUILocale method [.NET Framework hosting]
- SetUILocale method, ICLRTaskManager interface [.NET Framework hosting]
ms.assetid: 03adaa9a-2beb-49b3-b2c4-6b4fc3f10715
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03c5c9d04567832951062fe1512a292f9b32a94b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763331"
---
# <a name="iclrtaskmanagersetuilocale-method"></a><span data-ttu-id="d338e-102">ICLRTaskManager::SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="d338e-102">ICLRTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="d338e-103">Modul CLR (CLR), hostitele změnil národní prostředí uživatelského rozhraní (UI) nebo jazykovou verzi, upozorní na právě prováděnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="d338e-103">Notifies the common language runtime (CLR) that the host has modified the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d338e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d338e-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d338e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d338e-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="d338e-106">[in] Hodnota identifikátor národního prostředí, která mapuje pro nově přiřazenou zeměpisné jazykovou verzi a jazyk uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d338e-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language for the user interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d338e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d338e-107">Return Value</span></span>  
  
|<span data-ttu-id="d338e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d338e-108">HRESULT</span></span>|<span data-ttu-id="d338e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="d338e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d338e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d338e-110">S_OK</span></span>|<span data-ttu-id="d338e-111">`SetUILocale` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="d338e-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="d338e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d338e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d338e-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="d338e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d338e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d338e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d338e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="d338e-115">The call timed out.</span></span>|  
|<span data-ttu-id="d338e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d338e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d338e-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="d338e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d338e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d338e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d338e-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="d338e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d338e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d338e-120">E_FAIL</span></span>|<span data-ttu-id="d338e-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="d338e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d338e-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="d338e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d338e-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="d338e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d338e-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d338e-124">Remarks</span></span>  
 <span data-ttu-id="d338e-125">`SetUILocale` nabízí příležitosti pro hostitele, chcete-li spustit některý z mechanismů, které může mít pro synchronizaci národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="d338e-125">`SetUILocale` provides an opportunity for the host to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d338e-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d338e-126">Requirements</span></span>  
 <span data-ttu-id="d338e-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d338e-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d338e-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d338e-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d338e-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d338e-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d338e-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d338e-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d338e-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d338e-131">See also</span></span>

- [<span data-ttu-id="d338e-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d338e-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="d338e-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d338e-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="d338e-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d338e-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="d338e-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d338e-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
