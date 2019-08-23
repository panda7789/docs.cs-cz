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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: de39de96cd7c7ba0be2dc1bea78f79cfe996575c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937570"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="2e005-102">IHostIoCompletionManager::Bind – metoda</span><span class="sxs-lookup"><span data-stu-id="2e005-102">IHostIoCompletionManager::Bind Method</span></span>
<span data-ttu-id="2e005-103">Váže zadaný popisovač na port pro dokončení I/O, který byl vytvořen dřívějším voláním [CreateIoCompletionPort –](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span><span class="sxs-lookup"><span data-stu-id="2e005-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e005-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e005-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e005-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e005-105">Parameters</span></span>  
 `hPort`  
 <span data-ttu-id="2e005-106">pro Port dokončení I/O, ke kterému se má `hHandle`vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="2e005-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="2e005-107">Pokud je hodnota `hPort` null, `hHandle` je svázána s výchozím portem pro dokončení I/O.</span><span class="sxs-lookup"><span data-stu-id="2e005-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="2e005-108">pro Popisovač operačního systému, k `hPort`němuž má být vytvořena vazba.</span><span class="sxs-lookup"><span data-stu-id="2e005-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2e005-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2e005-109">Return Value</span></span>  
  
|<span data-ttu-id="2e005-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e005-110">HRESULT</span></span>|<span data-ttu-id="2e005-111">Popis</span><span class="sxs-lookup"><span data-stu-id="2e005-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e005-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e005-112">S_OK</span></span>|<span data-ttu-id="2e005-113">`Bind`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2e005-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="2e005-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e005-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e005-115">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2e005-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e005-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e005-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e005-117">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2e005-117">The call timed out.</span></span>|  
|<span data-ttu-id="2e005-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e005-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e005-119">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="2e005-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e005-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e005-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e005-121">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="2e005-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e005-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e005-122">E_FAIL</span></span>|<span data-ttu-id="2e005-123">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="2e005-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e005-124">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="2e005-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e005-125">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2e005-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e005-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e005-126">Remarks</span></span>  
 <span data-ttu-id="2e005-127">Port pro `CreateIoCompletionPort`dokončení I/O se vytvoří pomocí volání.</span><span class="sxs-lookup"><span data-stu-id="2e005-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="2e005-128">CLR volá `Bind` k navázání popisovače na tento port.</span><span class="sxs-lookup"><span data-stu-id="2e005-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2e005-129">Po dokončení vstupně-výstupních požadavků musí hostitel zavolat metodu [ICLRIoCompletionManager –::](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) doplněné.</span><span class="sxs-lookup"><span data-stu-id="2e005-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e005-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e005-130">Requirements</span></span>  
 <span data-ttu-id="2e005-131">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e005-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e005-132">**Hlaviček** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e005-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e005-133">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e005-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e005-134">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e005-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e005-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e005-135">See also</span></span>

- [<span data-ttu-id="2e005-136">ICLRIoCompletionManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e005-136">ICLRIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)
