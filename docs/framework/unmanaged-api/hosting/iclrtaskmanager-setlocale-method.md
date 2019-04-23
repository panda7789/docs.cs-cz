---
title: ICLRTaskManager::SetLocale – metoda
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae097320ad7cd6e7c840122bf3f315812e9b2acd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199203"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="61585-102">ICLRTaskManager::SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="61585-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="61585-103">Upozorní common language runtime (CLR), hostitele změnila hodnota identifikátor národního prostředí (který se mapuje na zeměpisné jazykovou verzi a jazyk) v současné době provádění úlohy.</span><span class="sxs-lookup"><span data-stu-id="61585-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61585-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61585-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61585-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61585-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="61585-106">[in] Hodnota identifikátor národního prostředí, která se mapuje na nově přiřazená zeměpisné jazykovou verzi a jazyk.</span><span class="sxs-lookup"><span data-stu-id="61585-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="61585-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="61585-107">Return Value</span></span>  
  
|<span data-ttu-id="61585-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="61585-108">HRESULT</span></span>|<span data-ttu-id="61585-109">Popis</span><span class="sxs-lookup"><span data-stu-id="61585-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="61585-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="61585-110">S_OK</span></span>|<span data-ttu-id="61585-111">Metoda vrátila úspěšně.</span><span class="sxs-lookup"><span data-stu-id="61585-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="61585-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="61585-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="61585-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="61585-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="61585-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="61585-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="61585-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="61585-115">The call timed out.</span></span>|  
|<span data-ttu-id="61585-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="61585-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="61585-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="61585-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="61585-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="61585-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="61585-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="61585-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="61585-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="61585-120">E_FAIL</span></span>|<span data-ttu-id="61585-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="61585-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="61585-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="61585-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="61585-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="61585-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61585-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="61585-124">Remarks</span></span>  
 <span data-ttu-id="61585-125">`SetLocale` poskytuje hostitele příležitost provést některý z mechanismů, které může mít pro synchronizaci národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="61585-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61585-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61585-126">Requirements</span></span>  
 <span data-ttu-id="61585-127">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61585-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61585-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="61585-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="61585-129">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="61585-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="61585-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61585-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61585-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="61585-131">See also</span></span>

- [<span data-ttu-id="61585-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61585-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="61585-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61585-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="61585-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61585-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="61585-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="61585-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
