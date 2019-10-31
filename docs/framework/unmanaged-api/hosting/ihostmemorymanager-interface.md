---
title: IHostMemoryManager – rozhraní
ms.date: 03/30/2017
api_name:
- IHostMemoryManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager
helpviewer_keywords:
- IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type:
- apiref
ms.openlocfilehash: bc05d76795f20d28d6d2899d61dc4674ebfdca8c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128651"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="92c76-102">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92c76-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="92c76-103">Poskytuje metody, které umožňují modulu CLR (Common Language Runtime) provádět požadavky na virtuální paměť prostřednictvím hostitele namísto použití standardních funkcí virtuální paměti Win32.</span><span class="sxs-lookup"><span data-stu-id="92c76-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92c76-104">Metody</span><span class="sxs-lookup"><span data-stu-id="92c76-104">Methods</span></span>  
  
|<span data-ttu-id="92c76-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-105">Method</span></span>|<span data-ttu-id="92c76-106">Popis</span><span class="sxs-lookup"><span data-stu-id="92c76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92c76-107">AcquiredVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="92c76-108">Upozorňuje hostitele, že modul CLR (Common Language Runtime) získal zadanou paměť z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="92c76-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="92c76-109">CreateMAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="92c76-110">Získá ukazatel rozhraní na instanci [IHostMalloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) , která se používá k vyžádání přidělení paměti z haldy vytvořené hostitelem.</span><span class="sxs-lookup"><span data-stu-id="92c76-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="92c76-111">GetMemoryLoad – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="92c76-112">Načte velikost fyzické paměti, která je aktuálně používána, jak je uvedeno v hostiteli.</span><span class="sxs-lookup"><span data-stu-id="92c76-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="92c76-113">NeedsVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="92c76-114">Upozorní hostitele, že se bude modul CLR pokoušet použít zadanou paměť.</span><span class="sxs-lookup"><span data-stu-id="92c76-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="92c76-115">RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="92c76-116">Registruje ukazatel na funkci zpětného volání, kterou hostitel vyvolá, aby upozornil CLR na aktuální zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="92c76-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="92c76-117">ReleasedVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="92c76-118">Upozorňuje hostitele, že modul CLR dokončil používání zadané paměti.</span><span class="sxs-lookup"><span data-stu-id="92c76-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="92c76-119">VirtualAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="92c76-120">Slouží jako logická obálka odpovídající funkce Win32, která rezervuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="92c76-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="92c76-121">VirtualFree – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="92c76-122">Slouží jako logická obálka odpovídající funkce Win32, která vydává, odváže nebo uvolňuje a odváže oblast stránek v rámci virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="92c76-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="92c76-123">VirtualProtect – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="92c76-124">Slouží jako logická obálka odpovídající funkce Win32, která mění ochranu v oblasti svěřené stránky ve virtuálním adresním prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="92c76-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="92c76-125">VirtualQuery – metoda</span><span class="sxs-lookup"><span data-stu-id="92c76-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="92c76-126">Slouží jako logická obálka odpovídající funkce Win32, která načte informace o rozsahu stránek ve virtuálním adresním prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="92c76-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92c76-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92c76-127">Remarks</span></span>  
 <span data-ttu-id="92c76-128">`IHostMemoryManager` také poskytuje metody pro CLR k získání ukazatele, pomocí kterého se vytvářejí požadavky na paměť na haldě, a k získání úrovně paměti v procesu, jak je uvedeno v hostiteli.</span><span class="sxs-lookup"><span data-stu-id="92c76-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c76-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92c76-129">Requirements</span></span>  
 <span data-ttu-id="92c76-130">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92c76-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c76-131">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92c76-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92c76-132">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="92c76-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92c76-133">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c76-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c76-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92c76-134">See also</span></span>

- [<span data-ttu-id="92c76-135">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92c76-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="92c76-136">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="92c76-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
