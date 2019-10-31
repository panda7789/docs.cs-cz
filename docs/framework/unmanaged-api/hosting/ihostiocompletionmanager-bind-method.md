---
title: IHostIoCompletionManager::Bind – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 84fc99f6a5feb7ec73ee16942ba2794fc082dc89
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133904"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="bbd6d-102">IHostIoCompletionManager::Bind – metoda</span><span class="sxs-lookup"><span data-stu-id="bbd6d-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="bbd6d-103">Váže zadaný popisovač na port pro dokončení I/O, který byl vytvořen dřívějším voláním [CreateIoCompletionPort –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="bbd6d-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbd6d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bbd6d-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbd6d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bbd6d-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="bbd6d-106">pro Port pro dokončení I/O, ke kterému se má vytvořit vazba `hHandle`.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="bbd6d-107">Pokud je hodnota `hPort` null, `hHandle` je svázána s výchozím portem pro dokončení I/O.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="bbd6d-108">pro Popisovač operačního systému pro vytvoření vazby na `hPort`.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbd6d-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="bbd6d-109">Return Value</span></span>  
  
|<span data-ttu-id="bbd6d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bbd6d-110">HRESULT</span></span>|<span data-ttu-id="bbd6d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="bbd6d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bbd6d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="bbd6d-112">S_OK</span></span>|<span data-ttu-id="bbd6d-113">`Bind` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="bbd6d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bbd6d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bbd6d-115">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bbd6d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bbd6d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bbd6d-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-117">The call timed out.</span></span>|  
|<span data-ttu-id="bbd6d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bbd6d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bbd6d-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bbd6d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bbd6d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bbd6d-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bbd6d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bbd6d-122">E_FAIL</span></span>|<span data-ttu-id="bbd6d-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bbd6d-124">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bbd6d-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bbd6d-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bbd6d-126">Remarks</span></span>  
 <span data-ttu-id="bbd6d-127">Port pro dokončení I/O se vytvoří pomocí volání `CreateIoCompletionPort`.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="bbd6d-128">CLR volá `Bind`, aby navázala popisovač na tento port.</span><span class="sxs-lookup"><span data-stu-id="bbd6d-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bbd6d-129">Po dokončení vstupně-výstupních požadavků musí hostitel zavolat metodu [ICLRIoCompletionManager –:: doplněné](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) .</span><span class="sxs-lookup"><span data-stu-id="bbd6d-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbd6d-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bbd6d-130">Requirements</span></span>  
 <span data-ttu-id="bbd6d-131">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bbd6d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbd6d-132">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bbd6d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bbd6d-133">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="bbd6d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bbd6d-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbd6d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbd6d-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbd6d-135">See also</span></span>

- [<span data-ttu-id="bbd6d-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bbd6d-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
