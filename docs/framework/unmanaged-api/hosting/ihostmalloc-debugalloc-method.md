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
ms.openlocfilehash: 8447f6fa2771128c1bdf424cb9aac141b2dfd486
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33439723"
---
# <a name="ihostmallocdebugalloc-method"></a><span data-ttu-id="7c9f3-102">IHostMAlloc::DebugAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="7c9f3-102">IHostMAlloc::DebugAlloc Method</span></span>
<span data-ttu-id="7c9f3-103">Požadavky, přidělit zadaného množství paměti z haldy hostitel a dále sledovat, kdy byl přidělen paměť.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-103">Requests that the host allocate the specified amount of memory from the heap, and additionally track where the memory was allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c9f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c9f3-104">Syntax</span></span>  
  
```  
HRESULT DebugAlloc (  
    [in]  SIZE_T  cbSize,   
    [in]  EMemoryCriticalLevel dwCriticalLevel,   
    [in]  char*   pszFileName,   
    [in]  int     iLineNo,   
    [out] void**  ppMem  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c9f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c9f3-105">Parameters</span></span>  
 `cbSize`  
 <span data-ttu-id="7c9f3-106">[v] Velikost v bajtech aktuální požadavek na přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-106">[in] The size, in bytes, of the current memory allocation request.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="7c9f3-107">[v] Jeden z [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnoty, která určuje dopad došlo k chybě přidělení.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-107">[in] One of the [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) values, indicating the impact of an allocation failure.</span></span>  
  
 `pszFileName`  
 <span data-ttu-id="7c9f3-108">[v] K souboru kódu laděné spustitelného souboru.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-108">[in] The code file of the executable being debugged.</span></span>  
  
 `iLineNo`  
 <span data-ttu-id="7c9f3-109">[v] Číslo řádku v `pszFileName` kde obdržel požadavek přidělení.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-109">[in] The line number in `pszFileName` where the allocation was requested.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="7c9f3-110">[out] Ukazatel na přidělené paměti, nebo hodnota null, pokud požadavek nebylo možné dokončit.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-110">[out] A pointer to the allocated memory, or null if the request could not be completed.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7c9f3-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7c9f3-111">Return Value</span></span>  
  
|<span data-ttu-id="7c9f3-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7c9f3-112">HRESULT</span></span>|<span data-ttu-id="7c9f3-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7c9f3-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c9f3-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="7c9f3-114">S_OK</span></span>|<span data-ttu-id="7c9f3-115">`DebugAlloc` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-115">`DebugAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="7c9f3-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7c9f3-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7c9f3-117">Modul CLR nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7c9f3-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7c9f3-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7c9f3-119">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-119">The call timed out.</span></span>|  
|<span data-ttu-id="7c9f3-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7c9f3-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7c9f3-121">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7c9f3-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7c9f3-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7c9f3-123">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7c9f3-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7c9f3-124">E_FAIL</span></span>|<span data-ttu-id="7c9f3-125">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7c9f3-126">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7c9f3-127">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7c9f3-128">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="7c9f3-128">E_OUTOFMEMORY</span></span>|<span data-ttu-id="7c9f3-129">Nedostatek paměti nebylo k dispozici k dokončení požadavek na přidělení.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-129">Not enough memory was available to complete the allocation request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c9f3-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7c9f3-130">Remarks</span></span>  
 <span data-ttu-id="7c9f3-131">Modul CLR získá ukazatele rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance voláním [ihostmemorymanager::createmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-131">The CLR gets an interface pointer to an [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance by calling the [IHostMemoryManager::CreateMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md) method.</span></span> <span data-ttu-id="7c9f3-132">`DebugAlloc` umožňuje získat informace o souboru kódu pro použití během ladění modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="7c9f3-132">`DebugAlloc` allows the runtime to get code file information for use during debugging.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c9f3-133">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c9f3-133">Requirements</span></span>  
 <span data-ttu-id="7c9f3-134">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c9f3-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c9f3-135">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7c9f3-135">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7c9f3-136">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c9f3-136">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7c9f3-137">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c9f3-137">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c9f3-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c9f3-138">See Also</span></span>  
 [<span data-ttu-id="7c9f3-139">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c9f3-139">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="7c9f3-140">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7c9f3-140">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
