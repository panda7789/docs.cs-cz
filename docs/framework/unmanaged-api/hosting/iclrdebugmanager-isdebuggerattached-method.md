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
ms.openlocfilehash: a21391f52a27e7f7a3abe533499c6b2581ec4a73
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615737"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="01186-102">ICLRDebugManager::IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="01186-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="01186-103">Získá hodnotu, která označuje, zda je k procesu připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="01186-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01186-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01186-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01186-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01186-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="01186-106">[out] `true` Pokud je ladicí program připojen k procesu; v opačném případě `false` .</span><span class="sxs-lookup"><span data-stu-id="01186-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01186-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="01186-107">Return Value</span></span>  
  
|<span data-ttu-id="01186-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01186-108">HRESULT</span></span>|<span data-ttu-id="01186-109">Popis</span><span class="sxs-lookup"><span data-stu-id="01186-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01186-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="01186-110">S_OK</span></span>|<span data-ttu-id="01186-111">`IsDebuggerAttached`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="01186-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="01186-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01186-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01186-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="01186-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01186-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01186-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01186-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="01186-115">The call timed out.</span></span>|  
|<span data-ttu-id="01186-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01186-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01186-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="01186-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01186-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01186-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01186-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="01186-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01186-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="01186-120">E_FAIL</span></span>|<span data-ttu-id="01186-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="01186-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01186-122">Poté, co metoda vrátí E_FAIL, CLR již není v rámci procesu možné použít.</span><span class="sxs-lookup"><span data-stu-id="01186-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01186-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="01186-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01186-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01186-124">Remarks</span></span>  
 <span data-ttu-id="01186-125">`IsDebuggerAttached`umožňuje hostiteli dotazovat se na CLR, aby zjistil, zda je k procesu připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="01186-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01186-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01186-126">Requirements</span></span>  
 <span data-ttu-id="01186-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01186-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01186-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="01186-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01186-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="01186-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01186-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01186-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01186-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="01186-131">See also</span></span>

- [<span data-ttu-id="01186-132">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01186-132">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="01186-133">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01186-133">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
- [<span data-ttu-id="01186-134">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="01186-134">IHostControl Interface</span></span>](ihostcontrol-interface.md)
