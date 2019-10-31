---
title: ICLRRuntimeHost::SetHostControl – metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
ms.openlocfilehash: 68b06a2840de277bdaed1dc9ce0b51e6b363c897
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120455"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="3439e-102">ICLRRuntimeHost::SetHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="3439e-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="3439e-103">Nastaví ukazatel rozhraní, který modul CLR (Common Language Runtime) může použít k získání implementace [rozhraní IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)hostitele.</span><span class="sxs-lookup"><span data-stu-id="3439e-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3439e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3439e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3439e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3439e-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="3439e-106">pro Ukazatel rozhraní na implementaci [rozhraní IHostControl](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)hostitele.</span><span class="sxs-lookup"><span data-stu-id="3439e-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3439e-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="3439e-107">Return Value</span></span>  
  
|<span data-ttu-id="3439e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3439e-108">HRESULT</span></span>|<span data-ttu-id="3439e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3439e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3439e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3439e-110">S_OK</span></span>|<span data-ttu-id="3439e-111">`SetHostControl` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="3439e-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="3439e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3439e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3439e-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="3439e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="3439e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="3439e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="3439e-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="3439e-115">The call timed out.</span></span>|  
|<span data-ttu-id="3439e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="3439e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="3439e-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="3439e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="3439e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="3439e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="3439e-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="3439e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="3439e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3439e-120">E_FAIL</span></span>|<span data-ttu-id="3439e-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="3439e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="3439e-122">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="3439e-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="3439e-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="3439e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3439e-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="3439e-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="3439e-125">Modul CLR již byl inicializován.</span><span class="sxs-lookup"><span data-stu-id="3439e-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3439e-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3439e-126">Remarks</span></span>  
 <span data-ttu-id="3439e-127">Musíte volat `SetHostControl` před inicializací CLR, tedy před voláním [metody Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) nebo použitím libovolného [rozhraní metadat](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="3439e-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="3439e-128">Doporučuje se volat `SetHostControl` hned po volání [funkce CorBindToCurrentRuntime –](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) nebo [funkce CorBindToRuntimeEx –](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="3439e-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3439e-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3439e-129">Requirements</span></span>  
 <span data-ttu-id="3439e-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3439e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3439e-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3439e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3439e-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3439e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3439e-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3439e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3439e-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3439e-134">See also</span></span>

- [<span data-ttu-id="3439e-135">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3439e-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="3439e-136">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3439e-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
