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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f34ed1796f6fa411d31fca83baeff693f85d70
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137349"
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="6c871-102">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c871-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="6c871-103">Poskytuje metody, které umožňují common language runtime (CLR) k podání žádostí o virtuální paměti prostřednictvím hostitele, namísto použití standardních funkcí virtuální paměti systému Win32.</span><span class="sxs-lookup"><span data-stu-id="6c871-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6c871-104">Metody</span><span class="sxs-lookup"><span data-stu-id="6c871-104">Methods</span></span>  
  
|<span data-ttu-id="6c871-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-105">Method</span></span>|<span data-ttu-id="6c871-106">Popis</span><span class="sxs-lookup"><span data-stu-id="6c871-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6c871-107">AcquiredVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="6c871-108">Upozorňuje hostitele, že modul CLR (CLR) získal zadaná paměťová z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="6c871-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="6c871-109">CreateMAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="6c871-110">Získá ukazatel rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instanci, která slouží k vyžádání přidělení paměti z haldy vytvořené hostitele.</span><span class="sxs-lookup"><span data-stu-id="6c871-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="6c871-111">GetMemoryLoad – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="6c871-112">Získá velikost fyzické paměti, která je aktuálně používán; podle hostitele.</span><span class="sxs-lookup"><span data-stu-id="6c871-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="6c871-113">NeedsVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="6c871-114">Upozorňuje hostitele, že modul CLR bude pokus o použití zadaná paměťová.</span><span class="sxs-lookup"><span data-stu-id="6c871-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="6c871-115">RegisterMemoryNotificationCallback – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="6c871-116">Zaregistruje ukazatel na funkci zpětného volání, která volá hostitele oznámit CLR aktuálního zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="6c871-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="6c871-117">ReleasedVirtualAddressSpace – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="6c871-118">Upozorňuje hostitele, že pomocí zadané paměti modulu CLR byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="6c871-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="6c871-119">VirtualAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="6c871-120">Slouží jako logické obálku pro odpovídající funkci Win32, který rezervuje nebo potvrdí změny v oblasti stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="6c871-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6c871-121">VirtualFree – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="6c871-122">Slouží jako logické obálku pro odpovídající funkci Win32, který uvolní, rozváže, nebo uvolní a rozváže oblast stránky v rámci virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="6c871-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6c871-123">VirtualProtect – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="6c871-124">Slouží jako logické obálku pro odpovídající funkci Win32, která změní ochrany v oblasti potvrzené stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="6c871-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="6c871-125">VirtualQuery – metoda</span><span class="sxs-lookup"><span data-stu-id="6c871-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="6c871-126">Slouží jako logické obálku pro odpovídající funkci Win32, který načte informace o rozsahu stránek v virtuálního adresového prostoru volajícího procesu.</span><span class="sxs-lookup"><span data-stu-id="6c871-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c871-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c871-127">Remarks</span></span>  
 <span data-ttu-id="6c871-128">`IHostMemoryManager` také poskytuje metody pro CLR získat ukazatel, pomocí kterého k podání žádostí o paměti v haldě a úroveň zatížení paměti v procesu, jak je hlásí hostitele.</span><span class="sxs-lookup"><span data-stu-id="6c871-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c871-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c871-129">Requirements</span></span>  
 <span data-ttu-id="6c871-130">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c871-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c871-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6c871-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6c871-132">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6c871-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6c871-133">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c871-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c871-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c871-134">See also</span></span>

- [<span data-ttu-id="6c871-135">IHostMalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c871-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)
- [<span data-ttu-id="6c871-136">Rozhraní pro hostování</span><span class="sxs-lookup"><span data-stu-id="6c871-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
