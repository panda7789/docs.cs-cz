---
title: ICLRDebugManager::IsDebuggerAttached – metoda
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type:
- apiref
ms.openlocfilehash: a58fcb6c1fa2aad96cdd29194a21eaf590536cdd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129396"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="9e525-102">ICLRDebugManager::IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="9e525-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="9e525-103">Získá hodnotu, která označuje, zda je k procesu připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="9e525-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e525-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e525-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e525-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e525-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="9e525-106">[out] `true`, zda je k procesu připojen ladicí program. v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="9e525-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9e525-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9e525-107">Return Value</span></span>  
  
|<span data-ttu-id="9e525-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9e525-108">HRESULT</span></span>|<span data-ttu-id="9e525-109">Popis</span><span class="sxs-lookup"><span data-stu-id="9e525-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9e525-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9e525-110">S_OK</span></span>|<span data-ttu-id="9e525-111">`IsDebuggerAttached` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="9e525-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="9e525-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9e525-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9e525-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="9e525-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9e525-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9e525-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9e525-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="9e525-115">The call timed out.</span></span>|  
|<span data-ttu-id="9e525-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9e525-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9e525-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="9e525-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9e525-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9e525-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9e525-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="9e525-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9e525-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9e525-120">E_FAIL</span></span>|<span data-ttu-id="9e525-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="9e525-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9e525-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="9e525-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9e525-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="9e525-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e525-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e525-124">Remarks</span></span>  
 <span data-ttu-id="9e525-125">`IsDebuggerAttached` umožňuje hostiteli dotazovat se na CLR, aby zjistil, zda je k procesu připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="9e525-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e525-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e525-126">Requirements</span></span>  
 <span data-ttu-id="9e525-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e525-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e525-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9e525-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9e525-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9e525-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9e525-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e525-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e525-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9e525-131">See also</span></span>

- [<span data-ttu-id="9e525-132">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e525-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="9e525-133">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e525-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [<span data-ttu-id="9e525-134">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e525-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
