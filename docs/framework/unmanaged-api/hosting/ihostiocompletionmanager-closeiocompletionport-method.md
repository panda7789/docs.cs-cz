---
title: IHostIoCompletionManager::CloseIoCompletionPort – metoda
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.CloseIoCompletionPort
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort
helpviewer_keywords:
- IHostIoCompletionManager::CloseIoCompletionPort method [.NET Framework hosting]
- CloseIoCompletionPort method [.NET Framework hosting]
ms.assetid: e86ad7be-3758-498a-a972-5522d69dfbb3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 761e3b22014bdd628ffc6763615a285a16a86309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441766"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="415ed-102">IHostIoCompletionManager::CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="415ed-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="415ed-103">Požadavky, že hostitel zavřete port, který se otevírá prostřednictvím starší volání [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="415ed-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="415ed-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="415ed-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="415ed-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="415ed-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="415ed-106">[v] Popisovač portu zavřete.</span><span class="sxs-lookup"><span data-stu-id="415ed-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="415ed-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="415ed-107">Return Value</span></span>  
  
|<span data-ttu-id="415ed-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="415ed-108">HRESULT</span></span>|<span data-ttu-id="415ed-109">Popis</span><span class="sxs-lookup"><span data-stu-id="415ed-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="415ed-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="415ed-110">S_OK</span></span>|<span data-ttu-id="415ed-111">`CloseIoCompletionPort` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="415ed-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="415ed-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="415ed-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="415ed-113">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="415ed-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="415ed-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="415ed-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="415ed-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="415ed-115">The call timed out.</span></span>|  
|<span data-ttu-id="415ed-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="415ed-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="415ed-117">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="415ed-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="415ed-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="415ed-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="415ed-119">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="415ed-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="415ed-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="415ed-120">E_FAIL</span></span>|<span data-ttu-id="415ed-121">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="415ed-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="415ed-122">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="415ed-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="415ed-123">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="415ed-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="415ed-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="415ed-124">E_INVALIDARG</span></span>|<span data-ttu-id="415ed-125">Byl předán neplatný popisovač portu.</span><span class="sxs-lookup"><span data-stu-id="415ed-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="415ed-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="415ed-126">Remarks</span></span>  
 <span data-ttu-id="415ed-127">`hPort` musí být popisovač pro port, který byl vytvořen starší volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="415ed-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="415ed-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="415ed-128">Requirements</span></span>  
 <span data-ttu-id="415ed-129">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="415ed-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="415ed-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="415ed-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="415ed-131">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="415ed-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="415ed-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="415ed-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="415ed-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="415ed-133">See Also</span></span>  
 [<span data-ttu-id="415ed-134">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="415ed-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 [<span data-ttu-id="415ed-135">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="415ed-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
