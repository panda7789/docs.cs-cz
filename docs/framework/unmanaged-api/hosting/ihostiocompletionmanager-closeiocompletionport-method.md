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
ms.openlocfilehash: cceced01b34f10cf38b41cfcb2a17059650f9ad9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736537"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="65c63-102">IHostIoCompletionManager::CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="65c63-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="65c63-103">Požadavky, že hostitel zavřít port, který byl otevřen prostřednictvím dřívějším volání [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="65c63-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65c63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65c63-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65c63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65c63-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="65c63-106">[in] Popisovač port zavřete.</span><span class="sxs-lookup"><span data-stu-id="65c63-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="65c63-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="65c63-107">Return Value</span></span>  
  
|<span data-ttu-id="65c63-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="65c63-108">HRESULT</span></span>|<span data-ttu-id="65c63-109">Popis</span><span class="sxs-lookup"><span data-stu-id="65c63-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="65c63-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="65c63-110">S_OK</span></span>|<span data-ttu-id="65c63-111">`CloseIoCompletionPort` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="65c63-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="65c63-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="65c63-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="65c63-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="65c63-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="65c63-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="65c63-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="65c63-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="65c63-115">The call timed out.</span></span>|  
|<span data-ttu-id="65c63-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="65c63-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="65c63-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="65c63-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="65c63-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="65c63-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="65c63-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="65c63-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="65c63-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="65c63-120">E_FAIL</span></span>|<span data-ttu-id="65c63-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="65c63-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="65c63-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="65c63-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="65c63-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="65c63-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="65c63-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="65c63-124">E_INVALIDARG</span></span>|<span data-ttu-id="65c63-125">Byl předán neplatný popisovač portu.</span><span class="sxs-lookup"><span data-stu-id="65c63-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="65c63-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65c63-126">Remarks</span></span>  
 <span data-ttu-id="65c63-127">`hPort` musí být popisovačem na port, který byl vytvořen v dřívějším volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="65c63-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65c63-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65c63-128">Requirements</span></span>  
 <span data-ttu-id="65c63-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65c63-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65c63-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="65c63-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="65c63-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65c63-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="65c63-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65c63-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65c63-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65c63-133">See also</span></span>

- [<span data-ttu-id="65c63-134">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65c63-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="65c63-135">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65c63-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
