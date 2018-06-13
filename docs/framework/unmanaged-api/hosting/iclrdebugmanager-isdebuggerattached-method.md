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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa085d9883f2a94a623f7800278c74a88e6a69a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432905"
---
# <a name="iclrdebugmanagerisdebuggerattached-method"></a><span data-ttu-id="36c08-102">ICLRDebugManager::IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="36c08-102">ICLRDebugManager::IsDebuggerAttached Method</span></span>
<span data-ttu-id="36c08-103">Získá hodnotu, která určuje, zda je pro proces připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="36c08-103">Gets a value that indicates whether a debugger is attached to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36c08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36c08-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="36c08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36c08-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="36c08-106">[out] `true` Pokud ladicí program je připojené k procesu, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="36c08-106">[out] `true` if a debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36c08-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="36c08-107">Return Value</span></span>  
  
|<span data-ttu-id="36c08-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36c08-108">HRESULT</span></span>|<span data-ttu-id="36c08-109">Popis</span><span class="sxs-lookup"><span data-stu-id="36c08-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36c08-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="36c08-110">S_OK</span></span>|<span data-ttu-id="36c08-111">`IsDebuggerAttached` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="36c08-111">`IsDebuggerAttached` returned successfully.</span></span>|  
|<span data-ttu-id="36c08-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36c08-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36c08-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="36c08-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="36c08-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="36c08-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="36c08-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="36c08-115">The call timed out.</span></span>|  
|<span data-ttu-id="36c08-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="36c08-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="36c08-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="36c08-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="36c08-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="36c08-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="36c08-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="36c08-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="36c08-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="36c08-120">E_FAIL</span></span>|<span data-ttu-id="36c08-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="36c08-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="36c08-122">Po návratu metoda E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="36c08-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="36c08-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="36c08-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36c08-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36c08-124">Remarks</span></span>  
 <span data-ttu-id="36c08-125">`IsDebuggerAttached` umožňuje hostiteli, aby dotaz CLR k určení, zda je pro proces připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="36c08-125">`IsDebuggerAttached` allows the host to query the CLR to determine whether a debugger is attached to the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36c08-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36c08-126">Requirements</span></span>  
 <span data-ttu-id="36c08-127">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36c08-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36c08-128">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="36c08-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36c08-129">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="36c08-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36c08-130">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36c08-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36c08-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="36c08-131">See Also</span></span>  
 [<span data-ttu-id="36c08-132">ICLRControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36c08-132">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="36c08-133">ICLRDebugManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36c08-133">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 [<span data-ttu-id="36c08-134">IHostControl – rozhraní</span><span class="sxs-lookup"><span data-stu-id="36c08-134">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
