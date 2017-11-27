---
title: "IHostMemoryManager – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IHostMemoryManager
api_location: mscoree.dll
api_type: COM
f1_keywords: IHostMemoryManager
helpviewer_keywords: IHostMemoryManager interface [.NET Framework hosting]
ms.assetid: a945d439-3b34-4aa4-b575-8413dd7806ce
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 415539be0dbed8e0cf3f9d6e5c79bf4cfac09fe2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ihostmemorymanager-interface"></a><span data-ttu-id="3e59d-102">IHostMemoryManager – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e59d-102">IHostMemoryManager Interface</span></span>
<span data-ttu-id="3e59d-103">Poskytuje metody, které povolit modul CLR (CLR) provádět požadavky na virtuální paměti prostřednictvím hostitele, místo použití standardní funkce Win32 virtuální paměti.</span><span class="sxs-lookup"><span data-stu-id="3e59d-103">Provides methods that allow the common language runtime (CLR) to make virtual memory requests through the host, instead of using the standard Win32 virtual memory functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3e59d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3e59d-104">Methods</span></span>  
  
|<span data-ttu-id="3e59d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-105">Method</span></span>|<span data-ttu-id="3e59d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3e59d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3e59d-107">Acquiredvirtualaddressspace – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-107">AcquiredVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-acquiredvirtualaddressspace-method.md)|<span data-ttu-id="3e59d-108">Upozorní hostitele, modul CLR (CLR) má získat zadaná paměťová z operačního systému.</span><span class="sxs-lookup"><span data-stu-id="3e59d-108">Notifies the host that the common language runtime (CLR) has acquired the specified memory from the operating system.</span></span>|  
|[<span data-ttu-id="3e59d-109">Createmalloc – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-109">CreateMAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-createmalloc-method.md)|<span data-ttu-id="3e59d-110">Získá ukazatele rozhraní k [ihostmalloc –](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instanci, která se používá k požadavku na přidělení paměti ze haldy vytvořené hostitele.</span><span class="sxs-lookup"><span data-stu-id="3e59d-110">Gets an interface pointer to an [IHostMAlloc](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md) instance that is used to request memory allocations from a heap created by the host.</span></span>|  
|[<span data-ttu-id="3e59d-111">Getmemoryload – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-111">GetMemoryLoad Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-getmemoryload-method.md)|<span data-ttu-id="3e59d-112">Získá množství fyzické paměti, který je aktuálně používá, jsou uvedeny pro hostitele.</span><span class="sxs-lookup"><span data-stu-id="3e59d-112">Gets the amount of physical memory that is currently being used, as reported by the host.</span></span>|  
|[<span data-ttu-id="3e59d-113">Needsvirtualaddressspace – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-113">NeedsVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-needsvirtualaddressspace-method.md)|<span data-ttu-id="3e59d-114">Aby modul CLR bude pokus o použití zadaná paměťová upozorní hostitele.</span><span class="sxs-lookup"><span data-stu-id="3e59d-114">Notifies the host that the CLR is going to attempt to use the specified memory.</span></span>|  
|[<span data-ttu-id="3e59d-115">Registermemorynotificationcallback – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-115">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)|<span data-ttu-id="3e59d-116">Zaregistruje ukazatel na funkci zpětného volání, která volá hostitele oznámit CLR aktuální zatížení paměti v počítači.</span><span class="sxs-lookup"><span data-stu-id="3e59d-116">Registers a pointer to a callback function that the host invokes to notify the CLR of the current memory load on the computer.</span></span>|  
|[<span data-ttu-id="3e59d-117">Releasedvirtualaddressspace – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-117">ReleasedVirtualAddressSpace Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-releasedvirtualaddressspace-method.md)|<span data-ttu-id="3e59d-118">Upozorní hostitele, že pomocí zadaná paměťová modulu CLR byla dokončena.</span><span class="sxs-lookup"><span data-stu-id="3e59d-118">Notifies the host that the CLR has finished using the specified memory.</span></span>|  
|[<span data-ttu-id="3e59d-119">VirtualAlloc – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-119">VirtualAlloc Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualalloc-method.md)|<span data-ttu-id="3e59d-120">Slouží jako logické obálku pro odpovídající funkci, Win32, která si vyhrazuje nebo potvrdí oblast stránek ve virtuálním adresním prostoru procesu volání.</span><span class="sxs-lookup"><span data-stu-id="3e59d-120">Serves as a logical wrapper for the corresponding Win32 function, which reserves or commits a region of pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="3e59d-121">Virtualfree – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-121">VirtualFree Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualfree-method.md)|<span data-ttu-id="3e59d-122">Slouží jako logické obálku pro odpovídající funkci Win32, což uvolní, decommits, nebo uvolní a decommits oblast stránek ve virtuálním adresním prostoru procesu volání.</span><span class="sxs-lookup"><span data-stu-id="3e59d-122">Serves as a logical wrapper for the corresponding Win32 function, which releases, decommits, or releases and decommits a region of pages within the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="3e59d-123">VirtualProtect – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-123">VirtualProtect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualprotect-method.md)|<span data-ttu-id="3e59d-124">Slouží jako logické obálku pro odpovídající funkci Win32, které změní ochrany v oblasti potvrdit stránek ve virtuálním adresním prostoru procesu volání.</span><span class="sxs-lookup"><span data-stu-id="3e59d-124">Serves as a logical wrapper for the corresponding Win32 function, which changes the protection on a region of committed pages in the virtual address space of the calling process.</span></span>|  
|[<span data-ttu-id="3e59d-125">VirtualQuery – metoda</span><span class="sxs-lookup"><span data-stu-id="3e59d-125">VirtualQuery Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-virtualquery-method.md)|<span data-ttu-id="3e59d-126">Slouží jako logické obálku pro odpovídající funkci, Win32, která načte informace o rozsahu stránek ve virtuálním adresním prostoru procesu volání.</span><span class="sxs-lookup"><span data-stu-id="3e59d-126">Serves as a logical wrapper for the corresponding Win32 function, which retrieves information about a range of pages in the virtual address space of the calling process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e59d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3e59d-127">Remarks</span></span>  
 <span data-ttu-id="3e59d-128">`IHostMemoryManager`také poskytuje metody pro CLR získat ukazatel přes který provádět požadavky na paměť v haldě a získat úroveň přetížení paměti v procesu vykazované hostitele.</span><span class="sxs-lookup"><span data-stu-id="3e59d-128">`IHostMemoryManager` also provides methods for the CLR to obtain a pointer through which to make memory requests on the heap and to get the level of memory pressure in the process, as reported by the host.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e59d-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3e59d-129">Requirements</span></span>  
 <span data-ttu-id="3e59d-130">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e59d-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e59d-131">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3e59d-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3e59d-132">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3e59d-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3e59d-133">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e59d-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e59d-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="3e59d-134">See Also</span></span>  
 [<span data-ttu-id="3e59d-135">Ihostmalloc – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3e59d-135">IHostMalloc Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 [<span data-ttu-id="3e59d-136">Rozhraní hostování</span><span class="sxs-lookup"><span data-stu-id="3e59d-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
