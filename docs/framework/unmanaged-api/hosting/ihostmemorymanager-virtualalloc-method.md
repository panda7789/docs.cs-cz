---
title: IHostMemoryManager::VirtualAlloc – metoda
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.VirtualAlloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::VirtualAlloc
helpviewer_keywords:
- VirtualAlloc method [.NET Framework hosting]
- IHostMemoryManager::VirtualAlloc method [.NET Framework hosting]
ms.assetid: 4dff3646-a050-4bd9-ac31-fe307e8637ec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e5ce46e1cf034e6b86d738d8ec69332df1ff9fc
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486257"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="2ec5d-102">IHostMemoryManager::VirtualAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="2ec5d-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="2ec5d-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="2ec5d-104">Implementace Win32 `VirtualAlloc` rezervuje nebo potvrdí změny v oblasti stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ec5d-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ec5d-105">Syntax</span></span>  
  
```  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2ec5d-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2ec5d-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="2ec5d-107">[in] Ukazatel na počáteční adresu oblasti, kterou chcete přidělit.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="2ec5d-108">[in] Velikost v bajtech, oblasti.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="2ec5d-109">[in] Typ přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="2ec5d-110">[in] Ochrana paměti pro oblasti stránek, které mají být přiděleny.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="2ec5d-111">[in] [Ememorycriticallevel –](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnotu, která určuje dopad selhání přidělení.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="2ec5d-112">[out] Ukazatel na počáteční adresu přidělené paměti nebo hodnota null, pokud požadavek se nepodařilo vyřídit.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2ec5d-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2ec5d-113">Return Value</span></span>  
  
|<span data-ttu-id="2ec5d-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2ec5d-114">HRESULT</span></span>|<span data-ttu-id="2ec5d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="2ec5d-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2ec5d-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="2ec5d-116">S_OK</span></span>|<span data-ttu-id="2ec5d-117">`VirtualAlloc` bylo úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="2ec5d-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2ec5d-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2ec5d-119">Modul CLR (CLR) se nenačetl do procesu nebo modul CLR je ve stavu, ve kterém nelze spouštět spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2ec5d-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2ec5d-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2ec5d-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-121">The call timed out.</span></span>|  
|<span data-ttu-id="2ec5d-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2ec5d-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2ec5d-123">Volající není vlastníkem zámku.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2ec5d-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2ec5d-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2ec5d-125">Událost byla zrušena při zablokování vlákna nebo vlákénka čekal na něj.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2ec5d-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2ec5d-126">E_FAIL</span></span>|<span data-ttu-id="2ec5d-127">Došlo k neznámé katastrofických selhání.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2ec5d-128">Po návratu metody E_FAIL, modul CLR už nejsou použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2ec5d-129">Následující volání metody hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2ec5d-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="2ec5d-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="2ec5d-131">Nedostatek paměti nebyl k dispozici k dokončení žádosti o přidělení</span><span class="sxs-lookup"><span data-stu-id="2ec5d-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ec5d-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ec5d-132">Remarks</span></span>  
 <span data-ttu-id="2ec5d-133">Rezervovat oblast v adresním prostoru procesu voláním `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="2ec5d-134">`pAddress` Parametr obsahuje počáteční adresu bloku paměti, který chcete.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="2ec5d-135">Tento parametr je obvykle nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-135">This parameter is typically set to null.</span></span> <span data-ttu-id="2ec5d-136">Operační systém se zaznamenávají rozsahy adres zdarma, které jsou k dispozici pro váš proces.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="2ec5d-137">A `pAddress` hodnotu null nastaví systém pro rezervaci oblast, bez ohledu na to považuje za vhodné.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="2ec5d-138">Alternativně můžete zadat konkrétní počáteční adresu bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="2ec5d-139">V obou případech se výstupní parametr `ppMem` se vrátí jako ukazatel do přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="2ec5d-140">Samotné funkce vrací hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="2ec5d-141">Win32 `VirtualAlloc` funkce nemá `ppMem` parametr a místo toho vrátí ukazatel do přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="2ec5d-142">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="2ec5d-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ec5d-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2ec5d-143">Requirements</span></span>  
 <span data-ttu-id="2ec5d-144">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ec5d-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ec5d-145">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2ec5d-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2ec5d-146">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2ec5d-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2ec5d-147">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ec5d-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ec5d-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ec5d-148">See also</span></span>
- [<span data-ttu-id="2ec5d-149">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2ec5d-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
