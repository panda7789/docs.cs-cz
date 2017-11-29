---
title: "IHostTaskManager::SetUILocale – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostTaskManager.SetUILocale
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3c29687d430187577ac25d8d2a007785632989ab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="a7534-102">IHostTaskManager::SetUILocale – metoda</span><span class="sxs-lookup"><span data-stu-id="a7534-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="a7534-103">Upozorní hostitele, že se změnila common language runtime (CLR), národní prostředí uživatelského rozhraní (UI) nebo jazykovou verzi na aktuálně spuštěné úlohy.</span><span class="sxs-lookup"><span data-stu-id="a7534-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7534-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7534-104">Syntax</span></span>  
  
```  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7534-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7534-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="a7534-106">[v] Hodnota identifikátoru národního prostředí, která se mapuje na nově přiřazené zeměpisné jazykovou verzi a jazyka.</span><span class="sxs-lookup"><span data-stu-id="a7534-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7534-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a7534-107">Return Value</span></span>  
  
|<span data-ttu-id="a7534-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a7534-108">HRESULT</span></span>|<span data-ttu-id="a7534-109">Popis</span><span class="sxs-lookup"><span data-stu-id="a7534-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a7534-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a7534-110">S_OK</span></span>|<span data-ttu-id="a7534-111">`SetUILocale`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="a7534-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="a7534-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a7534-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a7534-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a7534-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a7534-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a7534-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a7534-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a7534-115">The call timed out.</span></span>|  
|<span data-ttu-id="a7534-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a7534-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a7534-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="a7534-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a7534-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a7534-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a7534-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="a7534-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a7534-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a7534-120">E_FAIL</span></span>|<span data-ttu-id="a7534-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="a7534-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a7534-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="a7534-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a7534-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a7534-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="a7534-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="a7534-124">E_NOTIMPL</span></span>|<span data-ttu-id="a7534-125">Hostiteli neumožňuje spravované uživatelského kódu, chcete-li změnit jazyková verze uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a7534-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7534-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7534-126">Remarks</span></span>  
 <span data-ttu-id="a7534-127">Volání modulu runtime `SetUILocale` při hodnotu <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> vlastnost je změnit pomocí spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="a7534-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="a7534-128">Tato metoda poskytuje možnost pro hostitele k provedení nějaké mechanismy, které může mít pro synchronizaci národní prostředí.</span><span class="sxs-lookup"><span data-stu-id="a7534-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="a7534-129">Pokud hostitel neumožňuje národní prostředí uživatelského rozhraní se musí změnit ze spravovaného kódu nebo neimplementuje mechanismus k synchronizaci národní prostředí, měla by vrátit E_NOTIMPL z této metody.</span><span class="sxs-lookup"><span data-stu-id="a7534-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7534-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7534-130">Requirements</span></span>  
 <span data-ttu-id="a7534-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7534-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7534-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a7534-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a7534-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a7534-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a7534-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7534-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7534-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="a7534-135">See Also</span></span>  
 [<span data-ttu-id="a7534-136">Iclrtask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7534-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="a7534-137">Iclrtaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7534-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="a7534-138">Ihosttask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7534-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="a7534-139">Ihosttaskmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7534-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="a7534-140">Setlocale – metoda</span><span class="sxs-lookup"><span data-stu-id="a7534-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
