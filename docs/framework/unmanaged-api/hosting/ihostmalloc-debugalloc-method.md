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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e089d133374f112dea13e91f9bd571bd2b5af07
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132922"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="dfa08-102">IHostMAlloc::DebugAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="dfa08-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="dfa08-103">Požadavky, že hostitel přidělit zadaného množství paměti z haldy a také sledovat, kde byla přidělena paměť.</span><span class="sxs-lookup"><span data-stu-id="dfa08-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa08-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dfa08-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfa08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dfa08-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="dfa08-106">[in] Velikost v bajtech, aktuální požadavek na přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="dfa08-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="dfa08-107">[in] Jeden z [ememorycriticallevel –](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnoty určující dopad selhání přidělení.</span><span class="sxs-lookup"><span data-stu-id="dfa08-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="dfa08-108">[in] Soubor kódu laděnému spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="dfa08-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="dfa08-109">[in] Číslo řádku v `pszFileName` kde byl vyžádán přidělení.</span><span class="sxs-lookup"><span data-stu-id="dfa08-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="dfa08-110">[out] Ukazatel do přidělené paměti nebo hodnota null, pokud požadavek nešlo dokončit.</span><span class="sxs-lookup"><span data-stu-id="dfa08-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dfa08-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dfa08-111">Return Value</span></span>  
  
|<span data-ttu-id="dfa08-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfa08-112">HRESULT</span></span>|<span data-ttu-id="dfa08-113">Popis</span><span class="sxs-lookup"><span data-stu-id="dfa08-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfa08-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfa08-114">S_OK</span></span>|`DebugAlloc` <span data-ttu-id="dfa08-115">bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="dfa08-115">returned successfully.</span></span>|  
|<span data-ttu-id="dfa08-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dfa08-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dfa08-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="dfa08-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dfa08-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dfa08-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dfa08-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="dfa08-119">The call timed out.</span></span>|  
|<span data-ttu-id="dfa08-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dfa08-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dfa08-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="dfa08-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dfa08-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dfa08-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dfa08-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="dfa08-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dfa08-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dfa08-124">E_FAIL</span></span>|<span data-ttu-id="dfa08-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="dfa08-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dfa08-126">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="dfa08-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dfa08-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dfa08-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="dfa08-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="dfa08-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="dfa08-129">Nedostatek paměti nebyly k dispozici k dokončení požadavek na přidělení.</span><span class="sxs-lookup"><span data-stu-id="dfa08-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfa08-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dfa08-130">Remarks</span></span>  
 <span data-ttu-id="dfa08-131">Modul CLR načte ukazatel rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="dfa08-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> `DebugAlloc` <span data-ttu-id="dfa08-132">umožňuje načíst informace o souboru kódu pro použití během ladění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="dfa08-132">allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa08-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dfa08-133">Requirements</span></span>  
 <span data-ttu-id="dfa08-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa08-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa08-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dfa08-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfa08-136">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dfa08-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="dfa08-137">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="dfa08-137">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="dfa08-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfa08-138">See also</span></span>

- [<span data-ttu-id="dfa08-139">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dfa08-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="dfa08-140">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dfa08-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
