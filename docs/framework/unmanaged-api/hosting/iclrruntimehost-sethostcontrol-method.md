---
title: "ICLRRuntimeHost::SetHostControl – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.SetHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9727144e9504a5a3ad7ae2529286440d07633b2a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="4dc9a-102">ICLRRuntimeHost::SetHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="4dc9a-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="4dc9a-103">Nastaví ukazatele rozhraní, modul CLR (CLR) můžete získat implementace hostitele [ihostcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4dc9a-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dc9a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dc9a-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4dc9a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4dc9a-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="4dc9a-106">[v] Ukazatele rozhraní k implementaci hostitele [ihostcontrol – rozhraní](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4dc9a-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4dc9a-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4dc9a-107">Return Value</span></span>  
  
|<span data-ttu-id="4dc9a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4dc9a-108">HRESULT</span></span>|<span data-ttu-id="4dc9a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="4dc9a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4dc9a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4dc9a-110">S_OK</span></span>|<span data-ttu-id="4dc9a-111">`SetHostControl`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="4dc9a-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="4dc9a-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4dc9a-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4dc9a-113">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4dc9a-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4dc9a-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4dc9a-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4dc9a-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4dc9a-115">The call timed out.</span></span>|  
|<span data-ttu-id="4dc9a-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4dc9a-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4dc9a-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="4dc9a-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4dc9a-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4dc9a-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4dc9a-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="4dc9a-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4dc9a-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4dc9a-120">E_FAIL</span></span>|<span data-ttu-id="4dc9a-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="4dc9a-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4dc9a-122">Pokud metoda vrátí E_FAIL, modul CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="4dc9a-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4dc9a-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4dc9a-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4dc9a-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="4dc9a-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="4dc9a-125">Modul CLR již byl inicializován.</span><span class="sxs-lookup"><span data-stu-id="4dc9a-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dc9a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4dc9a-126">Remarks</span></span>  
 <span data-ttu-id="4dc9a-127">Je třeba volat `SetHostControl` před modulu CLR inicializací, který je před voláním [metoda Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) nebo použít některou z [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="4dc9a-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="4dc9a-128">Doporučuje se, že zavoláte `SetHostControl` ihned po volání [corbindtocurrentruntime – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) nebo [CorBindToRuntimeEx – funkce](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="4dc9a-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dc9a-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4dc9a-129">Requirements</span></span>  
 <span data-ttu-id="4dc9a-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dc9a-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dc9a-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4dc9a-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4dc9a-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4dc9a-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4dc9a-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dc9a-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dc9a-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="4dc9a-134">See Also</span></span>  
 [<span data-ttu-id="4dc9a-135">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4dc9a-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="4dc9a-136">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4dc9a-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
