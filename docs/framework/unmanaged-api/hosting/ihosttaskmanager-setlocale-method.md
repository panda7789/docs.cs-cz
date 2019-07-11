---
title: IHostTaskManager::SetLocale – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f388a52c320c3f0d5f4ad7e073e1e8960d7947dc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749362"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="f8536-102">IHostTaskManager::SetLocale – metoda</span><span class="sxs-lookup"><span data-stu-id="f8536-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="f8536-103">Upozorňuje hostitele, modul CLR (CLR) se změnila národního prostředí nebo jazykovou verzi na právě prováděnou úlohu.</span><span class="sxs-lookup"><span data-stu-id="f8536-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8536-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8536-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8536-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8536-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="f8536-106">[in] Hodnota identifikátor národního prostředí, která se mapuje na nově přiřazená zeměpisné jazykovou verzi a jazyk.</span><span class="sxs-lookup"><span data-stu-id="f8536-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8536-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f8536-107">Return Value</span></span>  
  
|<span data-ttu-id="f8536-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f8536-108">HRESULT</span></span>|<span data-ttu-id="f8536-109">Popis</span><span class="sxs-lookup"><span data-stu-id="f8536-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f8536-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f8536-110">S_OK</span></span>|<span data-ttu-id="f8536-111">`SetLocale` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="f8536-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="f8536-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f8536-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f8536-113">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f8536-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f8536-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f8536-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f8536-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f8536-115">The call timed out.</span></span>|  
|<span data-ttu-id="f8536-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f8536-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f8536-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="f8536-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f8536-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f8536-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f8536-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="f8536-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f8536-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f8536-120">E_FAIL</span></span>|<span data-ttu-id="f8536-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="f8536-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f8536-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="f8536-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f8536-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f8536-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f8536-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f8536-124">E_NOTIMPL</span></span>|<span data-ttu-id="f8536-125">Hostitel neumožňuje spravované uživatelský kód upravit národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="f8536-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8536-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8536-126">Remarks</span></span>  
 <span data-ttu-id="f8536-127">Modul runtime zavolá `SetLocale` při hodnotu <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> při změně vlastnosti spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f8536-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="f8536-128">Tato metoda poskytuje možnost pro hostitele, chcete-li spustit některý z mechanismů, které může mít pro synchronizaci národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="f8536-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="f8536-129">Pokud hostitel neumožňuje národní prostředí pro změnit ze spravovaného kódu nebo neimplementuje mechanismus pro synchronizaci národní prostředí, měla by vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="f8536-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8536-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8536-130">Requirements</span></span>  
 <span data-ttu-id="f8536-131">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8536-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8536-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f8536-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f8536-133">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f8536-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8536-134">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8536-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8536-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8536-135">See also</span></span>

- [<span data-ttu-id="f8536-136">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8536-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="f8536-137">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8536-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="f8536-138">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8536-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="f8536-139">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f8536-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="f8536-140">SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="f8536-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
