---
title: IHostCrst::Leave – metoda
ms.date: 03/30/2017
api_name:
- IHostCrst.Leave
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::Leave
helpviewer_keywords:
- IHostCrst::Leave method [.NET Framework hosting]
- Leave method [.NET Framework hosting]
ms.assetid: dfc51d9e-b36d-4dba-9ea1-4f63fa0601ae
topic_type:
- apiref
ms.openlocfilehash: 050af068579d84b984ed83377d0c201e281bd154
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130536"
---
# <a name="ihostcrstleave-method"></a><span data-ttu-id="f5bfe-102">IHostCrst::Leave – metoda</span><span class="sxs-lookup"><span data-stu-id="f5bfe-102">IHostCrst::Leave Method</span></span>
<span data-ttu-id="f5bfe-103">Ponechá kritickou část, která je reprezentovaná aktuální instancí [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfe-103">Leaves the critical section that is represented by the current instance of [IHostCrst](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5bfe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f5bfe-104">Syntax</span></span>  
  
```cpp  
HRESULT Leave ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="f5bfe-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f5bfe-105">Return Value</span></span>  
  
|<span data-ttu-id="f5bfe-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5bfe-106">HRESULT</span></span>|<span data-ttu-id="f5bfe-107">Popis</span><span class="sxs-lookup"><span data-stu-id="f5bfe-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5bfe-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5bfe-108">S_OK</span></span>|<span data-ttu-id="f5bfe-109">`Leave` byla úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-109">`Leave` returned successfully.</span></span>|  
|<span data-ttu-id="f5bfe-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f5bfe-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f5bfe-111">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f5bfe-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f5bfe-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f5bfe-113">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-113">The call timed out.</span></span>|  
|<span data-ttu-id="f5bfe-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f5bfe-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f5bfe-115">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f5bfe-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f5bfe-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f5bfe-117">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f5bfe-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f5bfe-118">E_FAIL</span></span>|<span data-ttu-id="f5bfe-119">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f5bfe-120">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f5bfe-121">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5bfe-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f5bfe-122">Remarks</span></span>  
 <span data-ttu-id="f5bfe-123">`Leave` umožňuje, aby CLR přímo komunikoval s implementací vlákna hostitele namísto použití odpovídající funkce Win32 `LeaveCriticalSection`.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-123">`Leave` allows the CLR to communicate directly with the host's threading implementation, rather than using the corresponding Win32 `LeaveCriticalSection` function.</span></span> <span data-ttu-id="f5bfe-124">Vlákno, které přebírá vlastnictví kritické části reprezentované aktuální instancí `IHostCrst`, musí volat `Leave` jednou pro pokaždé, když vstoupí v tomto kritickém oddílu.</span><span class="sxs-lookup"><span data-stu-id="f5bfe-124">A thread that takes ownership of the critical section represented by the current `IHostCrst` instance must call `Leave` once for each time it enters that critical section.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5bfe-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f5bfe-125">Requirements</span></span>  
 <span data-ttu-id="f5bfe-126">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5bfe-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5bfe-127">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f5bfe-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5bfe-128">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f5bfe-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5bfe-129">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5bfe-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5bfe-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f5bfe-130">See also</span></span>

- [<span data-ttu-id="f5bfe-131">ICLRSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5bfe-131">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="f5bfe-132">IHostCrst – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5bfe-132">IHostCrst Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)
- [<span data-ttu-id="f5bfe-133">IHostSyncManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f5bfe-133">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
