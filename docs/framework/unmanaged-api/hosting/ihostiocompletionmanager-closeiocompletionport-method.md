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
ms.openlocfilehash: 32a7c8b1c1c61eddb18ade1e77af5ea973fbaadc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107559"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="7d55b-102">IHostIoCompletionManager::CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="7d55b-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="7d55b-103">Požadavky, že hostitel zavřít port, který byl otevřen prostřednictvím dřívějším volání [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="7d55b-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d55b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d55b-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d55b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d55b-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="7d55b-106">[in] Popisovač port zavřete.</span><span class="sxs-lookup"><span data-stu-id="7d55b-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d55b-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7d55b-107">Return Value</span></span>  
  
|<span data-ttu-id="7d55b-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7d55b-108">HRESULT</span></span>|<span data-ttu-id="7d55b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7d55b-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7d55b-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7d55b-110">S_OK</span></span>|`CloseIoCompletionPort` <span data-ttu-id="7d55b-111">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="7d55b-111">returned successfully.</span></span>|  
|<span data-ttu-id="7d55b-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7d55b-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7d55b-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7d55b-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7d55b-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7d55b-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7d55b-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7d55b-115">The call timed out.</span></span>|  
|<span data-ttu-id="7d55b-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7d55b-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7d55b-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="7d55b-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7d55b-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7d55b-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7d55b-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="7d55b-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7d55b-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7d55b-120">E_FAIL</span></span>|<span data-ttu-id="7d55b-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="7d55b-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7d55b-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7d55b-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7d55b-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7d55b-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7d55b-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7d55b-124">E_INVALIDARG</span></span>|<span data-ttu-id="7d55b-125">Byl předán neplatný popisovač portu.</span><span class="sxs-lookup"><span data-stu-id="7d55b-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d55b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d55b-126">Remarks</span></span>  
 `hPort` <span data-ttu-id="7d55b-127">musí být popisovačem na port, který byl vytvořen v dřívějším volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="7d55b-127">must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d55b-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7d55b-128">Requirements</span></span>  
 <span data-ttu-id="7d55b-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d55b-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d55b-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d55b-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d55b-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7d55b-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7d55b-132">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7d55b-132">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7d55b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d55b-133">See also</span></span>

- [<span data-ttu-id="7d55b-134">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d55b-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="7d55b-135">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7d55b-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
