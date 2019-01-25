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
ms.openlocfilehash: e3ce303e8bcf33d192dbc7e2447ea6737577dcc5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554874"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="18add-102">IHostMAlloc::DebugAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="18add-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="18add-103">Požadavky, že hostitel přidělit zadaného množství paměti z haldy a také sledovat, kde byla přidělena paměť.</span><span class="sxs-lookup"><span data-stu-id="18add-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18add-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="18add-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="18add-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="18add-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="18add-106">[in] Velikost v bajtech, aktuální požadavek na přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="18add-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="18add-107">[in] Jeden z [ememorycriticallevel –](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnoty určující dopad selhání přidělení.</span><span class="sxs-lookup"><span data-stu-id="18add-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="18add-108">[in] Soubor kódu laděnému spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="18add-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="18add-109">[in] Číslo řádku v `pszFileName` kde byl vyžádán přidělení.</span><span class="sxs-lookup"><span data-stu-id="18add-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="18add-110">[out] Ukazatel do přidělené paměti nebo hodnota null, pokud požadavek nešlo dokončit.</span><span class="sxs-lookup"><span data-stu-id="18add-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18add-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="18add-111">Return Value</span></span>  
  
|<span data-ttu-id="18add-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="18add-112">HRESULT</span></span>|<span data-ttu-id="18add-113">Popis</span><span class="sxs-lookup"><span data-stu-id="18add-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="18add-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="18add-114">S_OK</span></span>|<span data-ttu-id="18add-115">`DebugAlloc` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="18add-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="18add-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="18add-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="18add-117">Modul CLR se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="18add-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="18add-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="18add-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="18add-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="18add-119">The call timed out.</span></span>|  
|<span data-ttu-id="18add-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="18add-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="18add-121">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="18add-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="18add-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="18add-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="18add-123">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="18add-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="18add-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="18add-124">E_FAIL</span></span>|<span data-ttu-id="18add-125">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="18add-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="18add-126">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="18add-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="18add-127">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="18add-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="18add-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="18add-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="18add-129">Nedostatek paměti nebyly k dispozici k dokončení požadavek na přidělení.</span><span class="sxs-lookup"><span data-stu-id="18add-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18add-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18add-130">Remarks</span></span>  
 <span data-ttu-id="18add-131">Modul CLR načte ukazatel rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="18add-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="18add-132">`DebugAlloc` umožňuje načíst informace o souboru kódu pro použití během ladění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="18add-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18add-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18add-133">Requirements</span></span>  
 <span data-ttu-id="18add-134">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18add-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18add-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="18add-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18add-136">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="18add-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18add-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18add-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18add-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="18add-138">See also</span></span>
- [<span data-ttu-id="18add-139">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18add-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="18add-140">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18add-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
