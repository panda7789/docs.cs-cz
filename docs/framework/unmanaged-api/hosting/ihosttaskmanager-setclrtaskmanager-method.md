---
title: IHostTaskManager::SetCLRTaskManager – metoda
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetCLRTaskManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetCLRTaskManager
helpviewer_keywords:
- IHostTaskManager::SetCLRTaskManager method [.NET Framework hosting]
- SetCLRTaskManager method [.NET Framework hosting]
ms.assetid: ec90ee83-bd4b-408b-9274-62a923ab86a1
topic_type:
- apiref
ms.openlocfilehash: c674cc43065bf8ea102bec1c5134757380454913
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141239"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="504ca-102">IHostTaskManager::SetCLRTaskManager – metoda</span><span class="sxs-lookup"><span data-stu-id="504ca-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="504ca-103">Poskytuje hostitele s ukazatelem rozhraní [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implementované modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="504ca-103">Provides the host with an interface pointer to an [ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="504ca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="504ca-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="504ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="504ca-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="504ca-106">pro Ukazatel na instanci `ICLRTaskManager` implementovaný modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="504ca-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="504ca-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="504ca-107">Return Value</span></span>  
  
|<span data-ttu-id="504ca-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="504ca-108">HRESULT</span></span>|<span data-ttu-id="504ca-109">Popis</span><span class="sxs-lookup"><span data-stu-id="504ca-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="504ca-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="504ca-110">S_OK</span></span>|<span data-ttu-id="504ca-111">`SetCLRTaskManager` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="504ca-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="504ca-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="504ca-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="504ca-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="504ca-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="504ca-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="504ca-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="504ca-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="504ca-115">The call timed out.</span></span>|  
|<span data-ttu-id="504ca-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="504ca-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="504ca-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="504ca-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="504ca-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="504ca-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="504ca-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="504ca-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="504ca-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="504ca-120">E_FAIL</span></span>|<span data-ttu-id="504ca-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="504ca-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="504ca-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="504ca-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="504ca-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="504ca-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="504ca-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="504ca-124">Remarks</span></span>  
 <span data-ttu-id="504ca-125">Běhové volání `SetCLRTaskManager` k poskytnutí hostitele s ukazatelem rozhraní na instanci `ICLRTaskManager`.</span><span class="sxs-lookup"><span data-stu-id="504ca-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="504ca-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="504ca-126">Requirements</span></span>  
 <span data-ttu-id="504ca-127">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="504ca-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="504ca-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="504ca-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="504ca-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="504ca-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="504ca-130">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="504ca-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="504ca-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="504ca-131">See also</span></span>

- [<span data-ttu-id="504ca-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="504ca-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="504ca-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="504ca-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="504ca-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="504ca-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="504ca-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="504ca-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
