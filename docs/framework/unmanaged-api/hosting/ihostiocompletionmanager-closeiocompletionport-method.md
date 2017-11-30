---
title: "IHostIoCompletionManager::CloseIoCompletionPort – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostIoCompletionManager.CloseIoCompletionPort
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 066d51c821cf86522ffaca4c15db360ce96ed773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="0ac82-102">IHostIoCompletionManager::CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="0ac82-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="0ac82-103">Požadavky, že hostitel zavřete port, který se otevírá prostřednictvím starší volání [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="0ac82-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ac82-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ac82-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0ac82-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0ac82-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="0ac82-106">[v] Popisovač portu zavřete.</span><span class="sxs-lookup"><span data-stu-id="0ac82-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ac82-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="0ac82-107">Return Value</span></span>  
  
|<span data-ttu-id="0ac82-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0ac82-108">HRESULT</span></span>|<span data-ttu-id="0ac82-109">Popis</span><span class="sxs-lookup"><span data-stu-id="0ac82-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0ac82-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0ac82-110">S_OK</span></span>|<span data-ttu-id="0ac82-111">`CloseIoCompletionPort`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="0ac82-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="0ac82-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0ac82-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0ac82-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="0ac82-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0ac82-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0ac82-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0ac82-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="0ac82-115">The call timed out.</span></span>|  
|<span data-ttu-id="0ac82-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0ac82-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0ac82-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="0ac82-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0ac82-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0ac82-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0ac82-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="0ac82-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0ac82-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0ac82-120">E_FAIL</span></span>|<span data-ttu-id="0ac82-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="0ac82-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0ac82-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="0ac82-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0ac82-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0ac82-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0ac82-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="0ac82-124">E_INVALIDARG</span></span>|<span data-ttu-id="0ac82-125">Byl předán neplatný popisovač portu.</span><span class="sxs-lookup"><span data-stu-id="0ac82-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ac82-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ac82-126">Remarks</span></span>  
 <span data-ttu-id="0ac82-127">`hPort`musí být popisovač pro port, který byl vytvořen starší volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="0ac82-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ac82-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ac82-128">Requirements</span></span>  
 <span data-ttu-id="0ac82-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ac82-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ac82-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0ac82-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0ac82-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0ac82-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0ac82-132">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ac82-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ac82-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ac82-133">See Also</span></span>  
 [<span data-ttu-id="0ac82-134">Iclriocompletionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ac82-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="0ac82-135">Ihostiocompletionmanager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0ac82-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
