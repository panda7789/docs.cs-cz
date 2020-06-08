---
title: IHostSyncManager::SetCLRSyncManager – metoda
ms.date: 03/30/2017
api_name:
- IHostSyncManager.SetCLRSyncManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::SetCLRSyncManager
helpviewer_keywords:
- IHostSyncManager::SetCLRSyncManager method [.NET Framework hosting]
- SetCLRSyncManager method [.NET Framework hosting]
ms.assetid: 2b8bbe76-a45d-4989-bacb-11df42f8798c
topic_type:
- apiref
ms.openlocfilehash: 7f1832b22a1b80855f48eba6d39bff64da6fa5f9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501440"
---
# <a name="ihostsyncmanagersetclrsyncmanager-method"></a><span data-ttu-id="a4a25-102">IHostSyncManager::SetCLRSyncManager – metoda</span><span class="sxs-lookup"><span data-stu-id="a4a25-102">IHostSyncManager::SetCLRSyncManager Method</span></span>
<span data-ttu-id="a4a25-103">Nastaví instanci [ICLRSyncManager](iclrsyncmanager-interface.md) k přidružení k aktuální instanci [IHostSyncManager](ihostsyncmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a4a25-103">Sets the [ICLRSyncManager](iclrsyncmanager-interface.md) instance to associate with the current [IHostSyncManager](ihostsyncmanager-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a25-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4a25-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCLRSyncManager (  
    [in] ICLRSyncManager *pManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a4a25-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4a25-105">Parameters</span></span>  
 `pManager`  
 <span data-ttu-id="a4a25-106">pro Ukazatel na `ICLRSyncManager` instanci poskytnutou modulem CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="a4a25-106">[in] A pointer to an `ICLRSyncManager` instance supplied by the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4a25-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4a25-107">Return Value</span></span>  
  
|<span data-ttu-id="a4a25-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a4a25-108">HRESULT</span></span>|<span data-ttu-id="a4a25-109">Description</span><span class="sxs-lookup"><span data-stu-id="a4a25-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a4a25-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4a25-110">S_OK</span></span>|<span data-ttu-id="a4a25-111">`SetCLRSyncManager`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="a4a25-111">`SetCLRSyncManager` returned successfully.</span></span>|  
|<span data-ttu-id="a4a25-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a4a25-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a4a25-113">Modul CLR nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="a4a25-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a4a25-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a4a25-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a4a25-115">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="a4a25-115">The call timed out.</span></span>|  
|<span data-ttu-id="a4a25-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a4a25-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a4a25-117">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="a4a25-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a4a25-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a4a25-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a4a25-119">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="a4a25-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a4a25-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a4a25-120">E_FAIL</span></span>|<span data-ttu-id="a4a25-121">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="a4a25-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a4a25-122">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="a4a25-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a4a25-123">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a4a25-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4a25-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4a25-124">Remarks</span></span>  
 <span data-ttu-id="a4a25-125">Aby bylo možné zjednodušit komunikaci mezi hostitelem a modulem CLR, jsou rozhraní hostování obecně uvedena ve dvojicích.</span><span class="sxs-lookup"><span data-stu-id="a4a25-125">To facilitate communication between the host and the CLR, hosting interfaces generally come in pairs.</span></span> <span data-ttu-id="a4a25-126">Jeden člen dvojice je implementován hostitelem a druhý člen je implementován modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="a4a25-126">One member of the pair is implemented by the host, and the other member is implemented by the CLR.</span></span> <span data-ttu-id="a4a25-127">Jako implementace na straně hostitele `IHostSyncManager` odpovídá rozhraní `ICLRSyncManager` rozhraní implementovanému modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="a4a25-127">As a host-side implementation, the `IHostSyncManager` interface corresponds to the `ICLRSyncManager` interface implemented by the CLR.</span></span> <span data-ttu-id="a4a25-128">Modul CLR volá `SetCLRSyncManager` zadání `ICLRSyncManager` instance pro hostitele, který má být přidružen k aktuální `IHostSyncManager` instanci.</span><span class="sxs-lookup"><span data-stu-id="a4a25-128">The CLR calls `SetCLRSyncManager` to supply an `ICLRSyncManager` instance for the host to associate with the current `IHostSyncManager` instance.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4a25-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4a25-129">Requirements</span></span>  
 <span data-ttu-id="a4a25-130">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4a25-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4a25-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a4a25-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a4a25-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a4a25-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a4a25-133">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4a25-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a25-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4a25-134">See also</span></span>

- [<span data-ttu-id="a4a25-135">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4a25-135">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="a4a25-136">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4a25-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
