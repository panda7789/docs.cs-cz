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
ms.openlocfilehash: e110f1f5ea326c232c7c96bb05913080e950083d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158896"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="dbc2e-102">IHostTaskManager::SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="dbc2e-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="dbc2e-103">Upozorňuje hostitele, modul CLR (CLR) se změnila národní prostředí uživatelského rozhraní (UI) nebo jazykovou verzi na právě prováděnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbc2e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dbc2e-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbc2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dbc2e-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="dbc2e-106">[in] Hodnota identifikátor národního prostředí, která se mapuje na nově přiřazená zeměpisné jazykovou verzi a jazyk.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dbc2e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dbc2e-107">Return Value</span></span>  
  
|<span data-ttu-id="dbc2e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dbc2e-108">HRESULT</span></span>|<span data-ttu-id="dbc2e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="dbc2e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbc2e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="dbc2e-110">S_OK</span></span>|`SetUILocale` <span data-ttu-id="dbc2e-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-111">returned successfully.</span></span>|  
|<span data-ttu-id="dbc2e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dbc2e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dbc2e-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dbc2e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dbc2e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dbc2e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-115">The call timed out.</span></span>|  
|<span data-ttu-id="dbc2e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dbc2e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dbc2e-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dbc2e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dbc2e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dbc2e-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dbc2e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dbc2e-120">E_FAIL</span></span>|<span data-ttu-id="dbc2e-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dbc2e-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dbc2e-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dbc2e-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="dbc2e-124">E_NOTIMPL</span></span>|<span data-ttu-id="dbc2e-125">Hostitel neumožňuje spravované uživatelský kód, chcete-li změnit jazykové verze uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbc2e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbc2e-126">Remarks</span></span>  
 <span data-ttu-id="dbc2e-127">Modul runtime zavolá `SetUILocale` při hodnotu <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> při změně vlastnosti spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="dbc2e-128">Tato metoda poskytuje možnost pro hostitele, chcete-li spustit některý z mechanismů, které může mít pro synchronizaci národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="dbc2e-129">Pokud hostiteli neumožňuje změnit ze spravovaného kódu národní prostředí uživatelského rozhraní nebo neimplementuje mechanismus pro synchronizaci národní prostředí, měla by vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="dbc2e-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbc2e-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dbc2e-130">Requirements</span></span>  
 <span data-ttu-id="dbc2e-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbc2e-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbc2e-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbc2e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbc2e-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbc2e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="dbc2e-134">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="dbc2e-134">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dbc2e-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbc2e-135">See also</span></span>

- [<span data-ttu-id="dbc2e-136">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbc2e-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="dbc2e-137">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbc2e-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="dbc2e-138">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbc2e-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="dbc2e-139">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dbc2e-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="dbc2e-140">SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="dbc2e-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
