---
title: "IHostIoCompletionManager::Bind – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a34de8c04e248d2973e9b27c10da9313db5077ff
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="22652-102">IHostIoCompletionManager::Bind – metoda</span><span class="sxs-lookup"><span data-stu-id="22652-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="22652-103">Zadanému popisovači váže k portu dokončení vstupně-výstupních operací, vytvořený starší voláním [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="22652-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22652-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22652-104">Syntax</span></span>  
  
```  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="22652-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22652-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="22652-106">[v] Portu dokončení vstupně-výstupních operací, do které chcete vytvořit vazbu `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="22652-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="22652-107">Pokud hodnota `hPort` má hodnotu null, `hHandle` je vázána výchozí port dokončení vstupně-výstupní operace.</span><span class="sxs-lookup"><span data-stu-id="22652-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="22652-108">[v] Popisovač operačního systému vytvořit vazbu na `hPort`.</span><span class="sxs-lookup"><span data-stu-id="22652-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22652-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22652-109">Return Value</span></span>  
  
|<span data-ttu-id="22652-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="22652-110">HRESULT</span></span>|<span data-ttu-id="22652-111">Popis</span><span class="sxs-lookup"><span data-stu-id="22652-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22652-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="22652-112">S_OK</span></span>|<span data-ttu-id="22652-113">`Bind`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="22652-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="22652-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="22652-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="22652-115">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="22652-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="22652-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="22652-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="22652-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="22652-117">The call timed out.</span></span>|  
|<span data-ttu-id="22652-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="22652-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="22652-119">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="22652-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="22652-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="22652-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="22652-121">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="22652-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="22652-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="22652-122">E_FAIL</span></span>|<span data-ttu-id="22652-123">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="22652-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="22652-124">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="22652-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="22652-125">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="22652-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22652-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22652-126">Remarks</span></span>  
 <span data-ttu-id="22652-127">K dokončení portu vstupně-výstupních operací je vytvořená pomocí volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="22652-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="22652-128">Volání CLR `Bind` pro vazbu popisovač k tomuto portu.</span><span class="sxs-lookup"><span data-stu-id="22652-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22652-129">Po dokončení požadavek vstupně-výstupních operací, musí volat hostitele [iclriocompletionmanager::onComplete –](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="22652-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22652-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22652-130">Requirements</span></span>  
 <span data-ttu-id="22652-131">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22652-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22652-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="22652-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="22652-133">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="22652-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="22652-134">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22652-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22652-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="22652-135">See Also</span></span>  
 [<span data-ttu-id="22652-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22652-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
