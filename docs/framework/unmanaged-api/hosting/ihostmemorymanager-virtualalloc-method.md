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
ms.openlocfilehash: de41b5e0aaf835ee2d4e4f32696fe104d5830b57
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804453"
---
# <a name="ihostmemorymanagervirtualalloc-method"></a><span data-ttu-id="89539-102">IHostMemoryManager::VirtualAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="89539-102">IHostMemoryManager::VirtualAlloc Method</span></span>
<span data-ttu-id="89539-103">Slouží jako logická obálka odpovídající funkce Win32.</span><span class="sxs-lookup"><span data-stu-id="89539-103">Serves as a logical wrapper for the corresponding Win32 function.</span></span> <span data-ttu-id="89539-104">Implementace v systému Win32 `VirtualAlloc` rezervuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="89539-104">The Win32 implementation of `VirtualAlloc` reserves or commits a region of pages in the virtual address space of the calling process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89539-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89539-105">Syntax</span></span>  
  
```cpp  
HRESULT VirtualAlloc (  
    [in]  void*   pAddress,  
    [in]  SIZE_T  dwSize,  
    [in]  DWORD   flAllocationType,  
    [in]  DWORD   flProtect,  
    [in]  EMemoryCriticalLevel dwCriticalLevel,  
    [out] void**  ppMem  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="89539-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="89539-106">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="89539-107">pro Ukazatel na počáteční adresu oblasti, která se má přidělit</span><span class="sxs-lookup"><span data-stu-id="89539-107">[in] A pointer to the starting address of the region to allocate.</span></span>  
  
 `dwSize`  
 <span data-ttu-id="89539-108">pro Velikost oblasti v bajtech</span><span class="sxs-lookup"><span data-stu-id="89539-108">[in] The size, in bytes, of the region.</span></span>  
  
 `flAllocationType`  
 <span data-ttu-id="89539-109">pro Typ přidělení paměti.</span><span class="sxs-lookup"><span data-stu-id="89539-109">[in] The type of memory allocation.</span></span>  
  
 `flProtect`  
 <span data-ttu-id="89539-110">pro Ochrana paměti pro oblast stránek, která se má přidělit</span><span class="sxs-lookup"><span data-stu-id="89539-110">[in] Memory protection for the region of pages to be allocated.</span></span>  
  
 `dwCriticalLevel`  
 <span data-ttu-id="89539-111">pro Hodnota [EMemoryCriticalLevel –](ememorycriticallevel-enumeration.md) , která označuje dopad selhání přidělení.</span><span class="sxs-lookup"><span data-stu-id="89539-111">[in] An [EMemoryCriticalLevel](ememorycriticallevel-enumeration.md) value that indicates the impact of an allocation failure.</span></span>  
  
 `ppMem`  
 <span data-ttu-id="89539-112">mimo Ukazatel na počáteční adresu přidělené paměti nebo hodnotu null, pokud požadavek nebylo možné splnit.</span><span class="sxs-lookup"><span data-stu-id="89539-112">[out] Pointer to the starting address of the allocated memory, or null if the request could not be satisfied.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="89539-113">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="89539-113">Return Value</span></span>  
  
|<span data-ttu-id="89539-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="89539-114">HRESULT</span></span>|<span data-ttu-id="89539-115">Popis</span><span class="sxs-lookup"><span data-stu-id="89539-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="89539-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="89539-116">S_OK</span></span>|<span data-ttu-id="89539-117">`VirtualAlloc`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="89539-117">`VirtualAlloc` returned successfully.</span></span>|  
|<span data-ttu-id="89539-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="89539-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="89539-119">Modul CLR (Common Language Runtime) nebyl načten do procesu, nebo je modul CLR ve stavu, ve kterém nemůže spustit spravovaný kód nebo úspěšně zpracovat volání.</span><span class="sxs-lookup"><span data-stu-id="89539-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="89539-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="89539-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="89539-121">Vypršel časový limit volání.</span><span class="sxs-lookup"><span data-stu-id="89539-121">The call timed out.</span></span>|  
|<span data-ttu-id="89539-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="89539-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="89539-123">Volající nevlastní zámek.</span><span class="sxs-lookup"><span data-stu-id="89539-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="89539-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="89539-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="89539-125">Událost byla zrušena při čekání na blokované vlákno nebo vlákna.</span><span class="sxs-lookup"><span data-stu-id="89539-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="89539-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="89539-126">E_FAIL</span></span>|<span data-ttu-id="89539-127">Došlo k neznámé chybě závažnosti.</span><span class="sxs-lookup"><span data-stu-id="89539-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="89539-128">Když metoda vrátí E_FAIL, CLR již není v rámci procesu použitelný.</span><span class="sxs-lookup"><span data-stu-id="89539-128">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="89539-129">Následná volání metod hostování vrací HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="89539-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="89539-130">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="89539-130">E_OUTOFMEMORY</span></span>|<span data-ttu-id="89539-131">K dokončení žádosti o přidělení není k dispozici dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="89539-131">Not enough memory was available to complete the allocation request</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89539-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89539-132">Remarks</span></span>  
 <span data-ttu-id="89539-133">Oblast se vyhrazuje v adresním prostoru procesu voláním `VirtualAlloc` .</span><span class="sxs-lookup"><span data-stu-id="89539-133">You reserve a region in the address space of your process by calling `VirtualAlloc`.</span></span> <span data-ttu-id="89539-134">`pAddress`Parametr obsahuje počáteční adresu bloku paměti, kterou chcete.</span><span class="sxs-lookup"><span data-stu-id="89539-134">The `pAddress` parameter contains the beginning address of the memory block you want.</span></span> <span data-ttu-id="89539-135">Tento parametr je obvykle nastaven na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="89539-135">This parameter is typically set to null.</span></span> <span data-ttu-id="89539-136">Operační systém uchovává záznam bezplatných rozsahů adres pro váš proces.</span><span class="sxs-lookup"><span data-stu-id="89539-136">The operating system keeps a record of free address ranges available to your process.</span></span> <span data-ttu-id="89539-137">`pAddress`Hodnota null dává systému pokyn, aby vyhradí oblast všude, kde se bude přizpůsobená.</span><span class="sxs-lookup"><span data-stu-id="89539-137">A `pAddress` value of null instructs the system to reserve the region wherever it sees fit.</span></span> <span data-ttu-id="89539-138">Alternativně můžete zadat konkrétní počáteční adresu pro blok paměti.</span><span class="sxs-lookup"><span data-stu-id="89539-138">Alternatively, you can provide a specific starting address for the memory block.</span></span> <span data-ttu-id="89539-139">V obou případech se výstupní parametr `ppMem` vrátí jako ukazatel na přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="89539-139">In both cases, the output parameter `ppMem` is returned as a pointer to the allocated memory.</span></span> <span data-ttu-id="89539-140">Funkce sama vrací hodnotu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="89539-140">The function itself returns an HRESULT value.</span></span>  
  
 <span data-ttu-id="89539-141">Funkce Win32 neobsahuje `VirtualAlloc` `ppMem` parametr a místo toho vrátí ukazatel na přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="89539-141">The Win32 `VirtualAlloc` function does not have a `ppMem` parameter, and returns the pointer to the allocated memory instead.</span></span> <span data-ttu-id="89539-142">Další informace najdete v dokumentaci k platformě Windows.</span><span class="sxs-lookup"><span data-stu-id="89539-142">For more information, see the Windows Platform documentation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89539-143">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89539-143">Requirements</span></span>  
 <span data-ttu-id="89539-144">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89539-144">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89539-145">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="89539-145">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89539-146">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="89539-146">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89539-147">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89539-147">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89539-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="89539-148">See also</span></span>

- [<span data-ttu-id="89539-149">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89539-149">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
