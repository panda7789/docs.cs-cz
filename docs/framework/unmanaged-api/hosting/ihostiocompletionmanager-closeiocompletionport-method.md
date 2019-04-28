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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760126"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="10efc-102">IHostIoCompletionManager::CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="10efc-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="10efc-103">Požadavky, že hostitel zavřít port, který byl otevřen prostřednictvím dřívějším volání [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="10efc-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10efc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="10efc-104">Syntax</span></span>  
  
```  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="10efc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="10efc-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="10efc-106">[in] Popisovač port zavřete.</span><span class="sxs-lookup"><span data-stu-id="10efc-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="10efc-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="10efc-107">Return Value</span></span>  
  
|<span data-ttu-id="10efc-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="10efc-108">HRESULT</span></span>|<span data-ttu-id="10efc-109">Popis</span><span class="sxs-lookup"><span data-stu-id="10efc-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="10efc-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="10efc-110">S_OK</span></span>|<span data-ttu-id="10efc-111">`CloseIoCompletionPort` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="10efc-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="10efc-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="10efc-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="10efc-113">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="10efc-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="10efc-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="10efc-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="10efc-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="10efc-115">The call timed out.</span></span>|  
|<span data-ttu-id="10efc-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="10efc-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="10efc-117">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="10efc-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="10efc-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="10efc-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="10efc-119">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="10efc-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="10efc-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="10efc-120">E_FAIL</span></span>|<span data-ttu-id="10efc-121">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="10efc-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="10efc-122">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="10efc-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="10efc-123">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="10efc-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="10efc-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="10efc-124">E_INVALIDARG</span></span>|<span data-ttu-id="10efc-125">Byl předán neplatný popisovač portu.</span><span class="sxs-lookup"><span data-stu-id="10efc-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10efc-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="10efc-126">Remarks</span></span>  
 <span data-ttu-id="10efc-127">`hPort` musí být popisovačem na port, který byl vytvořen v dřívějším volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="10efc-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10efc-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="10efc-128">Requirements</span></span>  
 <span data-ttu-id="10efc-129">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="10efc-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10efc-130">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="10efc-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="10efc-131">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="10efc-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="10efc-132">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10efc-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10efc-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10efc-133">See also</span></span>

- [<span data-ttu-id="10efc-134">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10efc-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="10efc-135">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="10efc-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
