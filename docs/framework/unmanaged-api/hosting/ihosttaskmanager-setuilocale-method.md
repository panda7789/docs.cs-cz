---
title: IHostTaskManager::SetUILocale – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a263410e898ee5805ce2a3dc9d534c25f6b9106
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496150"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="70563-102">IHostTaskManager::SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="70563-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="70563-103">Upozorňuje hostitele, modul CLR (CLR) se změnila národní prostředí uživatelského rozhraní (UI) nebo jazykovou verzi na právě prováděnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="70563-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70563-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70563-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="70563-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="70563-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="70563-106">[in] Hodnota identifikátor národního prostředí, která se mapuje na nově přiřazená zeměpisné jazykovou verzi a jazyk.</span><span class="sxs-lookup"><span data-stu-id="70563-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70563-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="70563-107">Return Value</span></span>  
  
|<span data-ttu-id="70563-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70563-108">HRESULT</span></span>|<span data-ttu-id="70563-109">Popis</span><span class="sxs-lookup"><span data-stu-id="70563-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70563-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="70563-110">S_OK</span></span>|<span data-ttu-id="70563-111">`SetUILocale` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="70563-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="70563-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="70563-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="70563-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="70563-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="70563-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="70563-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="70563-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="70563-115">The call timed out.</span></span>|  
|<span data-ttu-id="70563-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="70563-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="70563-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="70563-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="70563-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="70563-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="70563-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="70563-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="70563-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="70563-120">E_FAIL</span></span>|<span data-ttu-id="70563-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="70563-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="70563-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="70563-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="70563-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="70563-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="70563-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="70563-124">E_NOTIMPL</span></span>|<span data-ttu-id="70563-125">Hostitel neumožňuje spravované uživatelský kód, chcete-li změnit jazykové verze uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="70563-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70563-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70563-126">Remarks</span></span>  
 <span data-ttu-id="70563-127">Modul runtime zavolá `SetUILocale` při hodnotu <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> při změně vlastnosti spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="70563-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="70563-128">Tato metoda poskytuje možnost pro hostitele, chcete-li spustit některý z mechanismů, které může mít pro synchronizaci národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="70563-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="70563-129">Pokud hostiteli neumožňuje změnit ze spravovaného kódu národní prostředí uživatelského rozhraní nebo neimplementuje mechanismus pro synchronizaci národní prostředí, měla by vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="70563-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70563-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="70563-130">Requirements</span></span>  
 <span data-ttu-id="70563-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70563-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70563-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="70563-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70563-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70563-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70563-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70563-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70563-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70563-135">See also</span></span>
- [<span data-ttu-id="70563-136">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70563-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="70563-137">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70563-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="70563-138">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70563-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="70563-139">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="70563-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="70563-140">SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="70563-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
