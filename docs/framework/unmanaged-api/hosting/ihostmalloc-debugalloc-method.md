---
title: IHostMAlloc::DebugAlloc – metoda
ms.date: 03/30/2017
api_name:
- IHostMAlloc.DebugAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMAlloc::DebugAlloc
helpviewer_keywords:
- DebugAlloc method [.NET Framework hosting]
- IHostMAlloc::DebugAlloc method [.NET Framework hosting]
ms.assetid: 0bfbc527-bea2-43ce-b041-69186f4440dd
topic_type:
- apiref
ms.openlocfilehash: 20ad5485b8603cc7de1c27c00d53c8939871d525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178028"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="99bc2-102">IHostMAlloc::DebugAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="99bc2-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="99bc2-103">Požaduje, aby hostitel přidělit zadané množství paměti z haldy a navíc sledovat, kde byla přidělena paměť.</span><span class="sxs-lookup"><span data-stu-id="99bc2-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99bc2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99bc2-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,
    [in]  EMemoryCriticalLevel dwCriticalLevel,
    [in]  char*   pszFileName,
    [in]  int     iLineNo,
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99bc2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="99bc2-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="99bc2-106">[v] Velikost aktuálního požadavku na přidělení paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="99bc2-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="99bc2-107">[v] Jedna z hodnot [EMemoryCriticalLevel,](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) označující dopad selhání přidělení.</span><span class="sxs-lookup"><span data-stu-id="99bc2-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="99bc2-108">[v] Soubor kódu odladěného spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="99bc2-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="99bc2-109">[v] Číslo řádku, `pszFileName` ve kterém byla požadována alokace.</span><span class="sxs-lookup"><span data-stu-id="99bc2-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="99bc2-110">[out] Ukazatel na přidělenou paměť nebo hodnotu null, pokud požadavek nelze dokončit.</span><span class="sxs-lookup"><span data-stu-id="99bc2-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99bc2-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="99bc2-111">Return Value</span></span>  
  
|<span data-ttu-id="99bc2-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99bc2-112">HRESULT</span></span>|<span data-ttu-id="99bc2-113">Popis</span><span class="sxs-lookup"><span data-stu-id="99bc2-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99bc2-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="99bc2-114">S_OK</span></span>|<span data-ttu-id="99bc2-115">`DebugAlloc`úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="99bc2-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="99bc2-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99bc2-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99bc2-117">CLR nebyl načten do procesu nebo CLR je ve stavu, ve kterém nelze spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="99bc2-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="99bc2-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="99bc2-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="99bc2-119">Časový čas hovoru byl vypován.</span><span class="sxs-lookup"><span data-stu-id="99bc2-119">The call timed out.</span></span>|  
|<span data-ttu-id="99bc2-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="99bc2-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="99bc2-121">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="99bc2-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="99bc2-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="99bc2-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="99bc2-123">Událost byla zrušena, zatímco na ní čekalo blokované vlákno nebo vlákno.</span><span class="sxs-lookup"><span data-stu-id="99bc2-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="99bc2-124">E_fail</span><span class="sxs-lookup"><span data-stu-id="99bc2-124">E_FAIL</span></span>|<span data-ttu-id="99bc2-125">Došlo k neznámému katastrofickému selhání.</span><span class="sxs-lookup"><span data-stu-id="99bc2-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="99bc2-126">Když metoda vrátí E_FAIL CLR již není použitelný v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="99bc2-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="99bc2-127">Následná volání metod hostování vrátí HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="99bc2-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="99bc2-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="99bc2-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="99bc2-129">K dokončení požadavku na přidělení nebylo k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="99bc2-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99bc2-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99bc2-130">Remarks</span></span>  
 <span data-ttu-id="99bc2-131">CLR získá ukazatel rozhraní na instanci [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) voláním metody [IHostMemoryManager::CreateMalloc.](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)</span><span class="sxs-lookup"><span data-stu-id="99bc2-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="99bc2-132">`DebugAlloc`umožňuje runtime získat informace o souboru kódu pro použití při ladění.</span><span class="sxs-lookup"><span data-stu-id="99bc2-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99bc2-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99bc2-133">Requirements</span></span>  
 <span data-ttu-id="99bc2-134">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99bc2-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99bc2-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99bc2-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99bc2-136">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="99bc2-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99bc2-137">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99bc2-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99bc2-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="99bc2-138">See also</span></span>

- [<span data-ttu-id="99bc2-139">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99bc2-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="99bc2-140">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="99bc2-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
