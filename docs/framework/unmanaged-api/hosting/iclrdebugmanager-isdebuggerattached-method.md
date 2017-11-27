---
title: "ICLRDebugManager::IsDebuggerAttached – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.IsDebuggerAttached
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::IsDebuggerAttached
helpviewer_keywords:
- IsDebuggerAttached method, ICLRDebugManager interface [.NET Framework hosting]
- ICLRDebugManager::IsDebuggerAttached method [.NET Framework hosting]
ms.assetid: 2f105fe0-f52d-49c5-bda5-583fb27e3aa6
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 986c9ab7853324d1a2f0fc104399141068ae9a09
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="72ac4-102">ICLRDebugManager::IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="72ac4-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="72ac4-103">Získá hodnotu, která určuje, zda je pro proces připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="72ac4-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72ac4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72ac4-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="72ac4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="72ac4-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="72ac4-106">[out] `true` Pokud ladicí program je připojené k procesu, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="72ac4-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72ac4-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="72ac4-107">Return Value</span></span>  
  
|<span data-ttu-id="72ac4-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72ac4-108">HRESULT</span></span>|<span data-ttu-id="72ac4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="72ac4-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72ac4-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="72ac4-110">S_OK</span></span>|<span data-ttu-id="72ac4-111">`IsDebuggerAttached`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="72ac4-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="72ac4-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72ac4-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72ac4-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="72ac4-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="72ac4-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="72ac4-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="72ac4-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="72ac4-115">The call timed out.</span></span>|  
|<span data-ttu-id="72ac4-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="72ac4-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="72ac4-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="72ac4-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="72ac4-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="72ac4-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="72ac4-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="72ac4-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="72ac4-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72ac4-120">E_FAIL</span></span>|<span data-ttu-id="72ac4-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="72ac4-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="72ac4-122">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="72ac4-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="72ac4-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="72ac4-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72ac4-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72ac4-124">Remarks</span></span>  
 <span data-ttu-id="72ac4-125">`IsDebuggerAttached`umožňuje hostiteli, aby dotaz CLR k určení, zda je pro proces připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="72ac4-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72ac4-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72ac4-126">Requirements</span></span>  
 <span data-ttu-id="72ac4-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72ac4-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72ac4-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="72ac4-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72ac4-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="72ac4-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72ac4-130">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72ac4-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72ac4-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="72ac4-131">See Also</span></span>  
 [<span data-ttu-id="72ac4-132">Iclrcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72ac4-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="72ac4-133">Iclrdebugmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72ac4-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="72ac4-134">Ihostcontrol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72ac4-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
