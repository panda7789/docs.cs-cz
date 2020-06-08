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
ms.openlocfilehash: 644b31ae8e8f0c51c08bcad57220a028406cfd3a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504070"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="4ec61-102">ICLRRuntimeHost::SetHostControl – metoda</span><span class="sxs-lookup"><span data-stu-id="4ec61-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="4ec61-103">Nastaví ukazatel rozhraní, který modul CLR (Common Language Runtime) může použít k získání implementace [rozhraní IHostControl](ihostcontrol-interface.md)hostitele.</span><span class="sxs-lookup"><span data-stu-id="4ec61-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ec61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4ec61-104">Syntax</span></span>  
  
```cpp  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ec61-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4ec61-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="4ec61-106">pro Ukazatel rozhraní na implementaci [rozhraní IHostControl](ihostcontrol-interface.md)hostitele.</span><span class="sxs-lookup"><span data-stu-id="4ec61-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ec61-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="4ec61-107">Return Value</span></span>  
  
|<span data-ttu-id="4ec61-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4ec61-108">HRESULT</span></span>|<span data-ttu-id="4ec61-109">Description</span><span class="sxs-lookup"><span data-stu-id="4ec61-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4ec61-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4ec61-110">S_OK</span></span>|<span data-ttu-id="4ec61-111">`SetHostControl`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="4ec61-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="4ec61-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4ec61-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4ec61-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="4ec61-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4ec61-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4ec61-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4ec61-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="4ec61-115">The call timed out.</span></span>|  
|<span data-ttu-id="4ec61-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4ec61-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4ec61-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="4ec61-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4ec61-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4ec61-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4ec61-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="4ec61-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4ec61-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4ec61-120">E_FAIL</span></span>|<span data-ttu-id="4ec61-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="4ec61-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4ec61-122">Pokud metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="4ec61-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4ec61-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4ec61-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4ec61-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="4ec61-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="4ec61-125">Modul CLR již byl inicializován.</span><span class="sxs-lookup"><span data-stu-id="4ec61-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ec61-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4ec61-126">Remarks</span></span>  
 <span data-ttu-id="4ec61-127">Je nutné volat `SetHostControl` před inicializací modulu CLR, tedy před voláním [metody Start](iclrruntimehost-start-method.md) nebo použitím libovolného [rozhraní metadat](../metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="4ec61-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="4ec61-128">Doporučuje se volat `SetHostControl` hned po volání [funkce CorBindToCurrentRuntime –](corbindtocurrentruntime-function.md) nebo [funkce CorBindToRuntimeEx –](corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="4ec61-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ec61-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4ec61-129">Requirements</span></span>  
 <span data-ttu-id="4ec61-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ec61-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ec61-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4ec61-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4ec61-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4ec61-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4ec61-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ec61-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec61-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ec61-134">See also</span></span>

- [<span data-ttu-id="4ec61-135">ICLRRuntimeHost – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ec61-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="4ec61-136">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4ec61-136">IHostControl Interface</span></span>](ihostcontrol-interface.md)
