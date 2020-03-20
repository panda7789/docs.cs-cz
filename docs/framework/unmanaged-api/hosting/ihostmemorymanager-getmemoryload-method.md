---
title: IHostMemoryManager::GetMemoryLoad – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 88acd50c83eb1ff4d59aa50d677db2383912659a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176276"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="c6037-102">IHostMemoryManager::GetMemoryLoad – metoda</span><span class="sxs-lookup"><span data-stu-id="c6037-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="c6037-103">Získá množství fyzické paměti, která je aktuálně používána a proto není k dispozici, jak je uvedeno hostitelem.</span><span class="sxs-lookup"><span data-stu-id="c6037-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6037-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6037-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6037-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6037-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="c6037-106">[out] Ukazatel na přibližné procento celkové fyzické paměti, která je aktuálně používána.</span><span class="sxs-lookup"><span data-stu-id="c6037-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="c6037-107">[out] Ukazatel na počet bajtů, které jsou k dispozici pro běžný jazyk runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c6037-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6037-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c6037-108">Return Value</span></span>  
  
|<span data-ttu-id="c6037-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c6037-109">HRESULT</span></span>|<span data-ttu-id="c6037-110">Popis</span><span class="sxs-lookup"><span data-stu-id="c6037-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c6037-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c6037-111">S_OK</span></span>|<span data-ttu-id="c6037-112">`GetMemoryLoad`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="c6037-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="c6037-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c6037-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c6037-114">CLR nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="c6037-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c6037-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c6037-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c6037-116">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="c6037-116">The call timed out.</span></span>|  
|<span data-ttu-id="c6037-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c6037-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c6037-118">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="c6037-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c6037-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c6037-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c6037-120">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="c6037-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c6037-121">E_fail</span><span class="sxs-lookup"><span data-stu-id="c6037-121">E_FAIL</span></span>|<span data-ttu-id="c6037-122">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="c6037-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c6037-123">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="c6037-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c6037-124">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="c6037-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6037-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6037-125">Remarks</span></span>  
 <span data-ttu-id="c6037-126">`GetMemoryLoad`zabalí funkci Win32. `GlobalMemoryStatus`</span><span class="sxs-lookup"><span data-stu-id="c6037-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="c6037-127">Hodnota `pMemoryLoad` je ekvivalentem pole `dwMemoryLoad` ve `MEMORYSTATUS` struktuře `GlobalMemoryStatus`vrácené z .</span><span class="sxs-lookup"><span data-stu-id="c6037-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="c6037-128">Runtime používá vrácenou hodnotu jako heuristickou pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c6037-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="c6037-129">Například pokud hostitel hlásí, že většina paměti je používán, systém uvolňování paměti může zvolit shromažďovat z více generací zvýšit množství paměti, které mohou potenciálně k dispozici.</span><span class="sxs-lookup"><span data-stu-id="c6037-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6037-130">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6037-130">Requirements</span></span>  
 <span data-ttu-id="c6037-131">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6037-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6037-132">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c6037-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c6037-133">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c6037-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c6037-134">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6037-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6037-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6037-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="c6037-136">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c6037-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
