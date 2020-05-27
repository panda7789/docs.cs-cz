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
ms.openlocfilehash: 0e030a33a0a3368f35c82fad33f1ea2ce32446af
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841825"
---
# <a name="ihosttaskmanagersetclrtaskmanager-method"></a><span data-ttu-id="06b5d-102">IHostTaskManager::SetCLRTaskManager – metoda</span><span class="sxs-lookup"><span data-stu-id="06b5d-102">IHostTaskManager::SetCLRTaskManager Method</span></span>
<span data-ttu-id="06b5d-103">Poskytuje hostitele s ukazatelem rozhraní [ICLRTaskManager](iclrtaskmanager-interface.md) instance implementované modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="06b5d-103">Provides the host with an interface pointer to an [ICLRTaskManager](iclrtaskmanager-interface.md) instance implemented by the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06b5d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="06b5d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRTaskManager (  
    [in] ICLRTaskManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06b5d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06b5d-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="06b5d-106">pro Ukazatel na instanci implementovanou modulem CLR ( `ICLRTaskManager` Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="06b5d-106">[in] A pointer to an `ICLRTaskManager` instance implemented by the common language runtime.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="06b5d-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="06b5d-107">Return Value</span></span>  
  
|<span data-ttu-id="06b5d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="06b5d-108">HRESULT</span></span>|<span data-ttu-id="06b5d-109">Popis</span><span class="sxs-lookup"><span data-stu-id="06b5d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="06b5d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="06b5d-110">S_OK</span></span>|<span data-ttu-id="06b5d-111">`SetCLRTaskManager`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="06b5d-111">`SetCLRTaskManager` returned successfully.</span></span>|  
|<span data-ttu-id="06b5d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="06b5d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="06b5d-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="06b5d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="06b5d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="06b5d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="06b5d-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="06b5d-115">The call timed out.</span></span>|  
|<span data-ttu-id="06b5d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="06b5d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="06b5d-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="06b5d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="06b5d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="06b5d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="06b5d-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="06b5d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="06b5d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="06b5d-120">E_FAIL</span></span>|<span data-ttu-id="06b5d-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="06b5d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="06b5d-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="06b5d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="06b5d-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="06b5d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06b5d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="06b5d-124">Remarks</span></span>  
 <span data-ttu-id="06b5d-125">Běhové volání `SetCLRTaskManager` pro poskytnutí hostitele s ukazatelem rozhraní na `ICLRTaskManager` instanci.</span><span class="sxs-lookup"><span data-stu-id="06b5d-125">The runtime calls `SetCLRTaskManager` to provide the host with an interface pointer to an `ICLRTaskManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06b5d-126">Požadavky</span><span class="sxs-lookup"><span data-stu-id="06b5d-126">Requirements</span></span>  
 <span data-ttu-id="06b5d-127">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06b5d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06b5d-128">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="06b5d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="06b5d-129">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="06b5d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="06b5d-130">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06b5d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06b5d-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="06b5d-131">See also</span></span>

- [<span data-ttu-id="06b5d-132">ICLRTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06b5d-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="06b5d-133">ICLRTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06b5d-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="06b5d-134">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06b5d-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="06b5d-135">IHostTaskManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="06b5d-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
