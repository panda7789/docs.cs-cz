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
ms.openlocfilehash: fe54aed47d240be37ab9dbc5381235c4e962f1f8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440311"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="119f9-102">IHostMemoryManager::VirtualAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="119f9-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="119f9-103">Slouží jako logické obálku pro odpovídající funkci Win32.</span><span class="sxs-lookup"><span data-stu-id="119f9-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="119f9-104">Implementace Win32 `VirtualAlloc` si vyhrazuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru procesu volání.</span><span class="sxs-lookup"><span data-stu-id="119f9-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="119f9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="119f9-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="119f9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="119f9-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="119f9-107">[v] Ukazatel na počáteční adresa oblasti přidělit.</span><span class="sxs-lookup"><span data-stu-id="119f9-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="119f9-108">[v] Velikost v bajtech, oblasti.</span><span class="sxs-lookup"><span data-stu-id="119f9-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="119f9-109">[v] Typ přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="119f9-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="119f9-110">[v] Ochrana paměti pro oblast stránek má být přidělen.</span><span class="sxs-lookup"><span data-stu-id="119f9-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="119f9-111">[v] [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) hodnotu, která určuje dopad došlo k chybě přidělení.</span><span class="sxs-lookup"><span data-stu-id="119f9-111">[in] An [EMemoryCriticalLevel](../../../../docs/framework/unmanaged-api/hosting/ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="119f9-112">[out] Ukazatel na počáteční adresa přidělené paměti, nebo hodnota null, pokud požadavek nelze uspokojit.</span><span class="sxs-lookup"><span data-stu-id="119f9-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="119f9-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="119f9-113">Return Value</span></span>  
  
|<span data-ttu-id="119f9-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="119f9-114">HRESULT</span></span>|<span data-ttu-id="119f9-115">Popis</span><span class="sxs-lookup"><span data-stu-id="119f9-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="119f9-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="119f9-116">S_OK</span></span>|<span data-ttu-id="119f9-117">`VirtualAlloc` úspěšně vrácena.</span><span class="sxs-lookup"><span data-stu-id="119f9-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="119f9-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="119f9-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="119f9-119">Modul CLR (CLR) nebyla načtena do procesu nebo CLR je ve stavu, ve kterém nemůže běžet spravovaného kódu nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="119f9-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="119f9-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="119f9-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="119f9-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="119f9-121">The call timed out.</span></span>|  
|<span data-ttu-id="119f9-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="119f9-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="119f9-123">Volající není vlastníkem zámek.</span><span class="sxs-lookup"><span data-stu-id="119f9-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="119f9-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="119f9-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="119f9-125">Událost byla zrušena při blokované vlákna nebo fiber čekal na něm.</span><span class="sxs-lookup"><span data-stu-id="119f9-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="119f9-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="119f9-126">E_FAIL</span></span>|<span data-ttu-id="119f9-127">Došlo k neznámému závažné selhání.</span><span class="sxs-lookup"><span data-stu-id="119f9-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="119f9-128">Po návratu metody E_FAIL modulu CLR již není použitelné v rámci procesu.</span><span class="sxs-lookup"><span data-stu-id="119f9-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="119f9-129">Následující volání hostování metody vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="119f9-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="119f9-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="119f9-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="119f9-131">Není dostatek paměti k dispozici bylo možné dokončit požadavek na přidělení</span><span class="sxs-lookup"><span data-stu-id="119f9-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="119f9-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="119f9-132">Remarks</span></span>  
 <span data-ttu-id="119f9-133">Rezervovat oblast v adresním prostoru procesu voláním `VirtualAlloc`.</span><span class="sxs-lookup"><span data-stu-id="119f9-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="119f9-134">`pAddress` Parametr obsahuje počáteční adresa paměti bloku chcete.</span><span class="sxs-lookup"><span data-stu-id="119f9-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="119f9-135">Tento parametr je obvykle nastaven na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="119f9-135">This parameter is typically set to null.</span></span> <span data-ttu-id="119f9-136">Operační systém obsahuje záznamy o volnou adresu rozsahy, které jsou k dispozici pro váš proces.</span><span class="sxs-lookup"><span data-stu-id="119f9-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="119f9-137">A `pAddress` systému tak, aby vyhradil oblast, bez ohledu na považuje za vhodné dá pokyn, hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="119f9-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="119f9-138">Alternativně můžete zadat konkrétní počáteční adresa bloku paměti.</span><span class="sxs-lookup"><span data-stu-id="119f9-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="119f9-139">V obou případech výstupního parametru `ppMem` se vrátí jako ukazatel přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="119f9-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="119f9-140">Samotná funkce vrátí hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="119f9-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="119f9-141">Win32 `VirtualAlloc` funkce nemá `ppMem` parametr a vrátí ukazatele do paměti přidělené místo.</span><span class="sxs-lookup"><span data-stu-id="119f9-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="119f9-142">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="119f9-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="119f9-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="119f9-143">Requirements</span></span>  
 <span data-ttu-id="119f9-144">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="119f9-144">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="119f9-145">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="119f9-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="119f9-146">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="119f9-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="119f9-147">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="119f9-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="119f9-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="119f9-148">See Also</span></span>  
 [<span data-ttu-id="119f9-149">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="119f9-149">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
