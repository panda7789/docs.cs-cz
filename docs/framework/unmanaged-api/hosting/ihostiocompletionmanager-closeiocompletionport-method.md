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
ms.openlocfilehash: 254254af705f93793b030882e0ac79d0372ca55f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133895"
---
# <a name="ihostiocompletionmanagercloseiocompletionport-method"></a><span data-ttu-id="b1a64-102">IHostIoCompletionManager::CloseIoCompletionPort – metoda</span><span class="sxs-lookup"><span data-stu-id="b1a64-102">IHostIoCompletionManager::CloseIoCompletionPort Method</span></span>
<span data-ttu-id="b1a64-103">Požaduje, aby hostitel zavřel port, který byl otevřen prostřednictvím dřívějšího volání [CreateIoCompletionPort –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="b1a64-103">Requests that the host close a port that was opened through an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a64-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1a64-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseIoCompletionPort (  
    [in] HANDLE hPort  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1a64-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1a64-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="b1a64-106">pro Popisovač portu, který má být zavřen.</span><span class="sxs-lookup"><span data-stu-id="b1a64-106">[in] The handle of the port to close.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b1a64-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b1a64-107">Return Value</span></span>  
  
|<span data-ttu-id="b1a64-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b1a64-108">HRESULT</span></span>|<span data-ttu-id="b1a64-109">Popis</span><span class="sxs-lookup"><span data-stu-id="b1a64-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b1a64-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="b1a64-110">S_OK</span></span>|<span data-ttu-id="b1a64-111">`CloseIoCompletionPort` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="b1a64-111">`CloseIoCompletionPort` returned successfully.</span></span>|  
|<span data-ttu-id="b1a64-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b1a64-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b1a64-113">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="b1a64-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="b1a64-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="b1a64-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="b1a64-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="b1a64-115">The call timed out.</span></span>|  
|<span data-ttu-id="b1a64-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="b1a64-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="b1a64-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="b1a64-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="b1a64-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="b1a64-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="b1a64-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="b1a64-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="b1a64-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b1a64-120">E_FAIL</span></span>|<span data-ttu-id="b1a64-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="b1a64-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="b1a64-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="b1a64-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="b1a64-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="b1a64-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b1a64-124">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="b1a64-124">E_INVALIDARG</span></span>|<span data-ttu-id="b1a64-125">Byl předán neplatný popisovač portu.</span><span class="sxs-lookup"><span data-stu-id="b1a64-125">An invalid port handle was passed.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1a64-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1a64-126">Remarks</span></span>  
 <span data-ttu-id="b1a64-127">`hPort` musí být popisovačem portu, který byl vytvořen starším voláním metody `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="b1a64-127">`hPort` must be a handle to a port that was created by an earlier call to `CreateIoCompletionPort`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1a64-128">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1a64-128">Requirements</span></span>  
 <span data-ttu-id="b1a64-129">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1a64-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1a64-130">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b1a64-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1a64-131">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b1a64-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1a64-132">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1a64-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a64-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1a64-133">See also</span></span>

- [<span data-ttu-id="b1a64-134">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1a64-134">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
- [<span data-ttu-id="b1a64-135">IHostIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b1a64-135">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
