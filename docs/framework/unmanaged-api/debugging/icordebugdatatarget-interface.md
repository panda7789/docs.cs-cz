---
title: "ICorDebugDataTarget – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget
helpviewer_keywords: ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5d3a3b190cfa606bd4239e24c5defdaff9f4257
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="c1a01-102">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c1a01-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="c1a01-103">Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="c1a01-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c1a01-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c1a01-104">Methods</span></span>  
  
|<span data-ttu-id="c1a01-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c1a01-105">Method</span></span>|<span data-ttu-id="c1a01-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c1a01-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c1a01-107">GetPlatform – metoda</span><span class="sxs-lookup"><span data-stu-id="c1a01-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="c1a01-108">Poskytuje informace o platformě, včetně architekturu procesoru a operačního systému, na kterém je tento cílový proces běží.</span><span class="sxs-lookup"><span data-stu-id="c1a01-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="c1a01-109">ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="c1a01-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="c1a01-110">Získá blok souvislé paměti začínající na zadanou adresu a vrátí ji v poskytnutá vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="c1a01-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="c1a01-111">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="c1a01-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="c1a01-112">Požádá o aktuálním kontextu vláken pro zadaný vlákno.</span><span class="sxs-lookup"><span data-stu-id="c1a01-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1a01-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1a01-113">Remarks</span></span>  
 <span data-ttu-id="c1a01-114">`ICorDebugDataTarget`a její metody mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="c1a01-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
-   <span data-ttu-id="c1a01-115">Ladění služeb volat metody pro toto rozhraní pro přístup k paměti a další data v tento cílový proces.</span><span class="sxs-lookup"><span data-stu-id="c1a01-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
-   <span data-ttu-id="c1a01-116">Ladicí program klienta musí implementovat toto rozhraní podle potřeby pro konkrétní cíl (například za provozu procesu nebo výpis stavu paměti).</span><span class="sxs-lookup"><span data-stu-id="c1a01-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
-   <span data-ttu-id="c1a01-117">`ICorDebugDataTarget` Metody lze uplatnit pouze z v rámci metody implementované v jiných `ICorDebug*` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c1a01-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="c1a01-118">Tím se zajistí, aby ladicí program klienta má kontrolu nad přes které vlákno vyvolání na a kdy.</span><span class="sxs-lookup"><span data-stu-id="c1a01-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
-   <span data-ttu-id="c1a01-119">`ICorDebugDataTarget` Implementace musí vracet vždy aktuální informace o cíli.</span><span class="sxs-lookup"><span data-stu-id="c1a01-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="c1a01-120">Tento Cílový proces by měl být zastaven a nebyl změněn. žádným způsobem při `ICorDebug*` rozhraní (a proto `ICorDebugDataTarget` metody) jsou volána.</span><span class="sxs-lookup"><span data-stu-id="c1a01-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="c1a01-121">Pokud je cílový proces za provozu a její změny stavu [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) metoda má být volána znovu k zadejte instanci ICorDebugProcess nahrazení.</span><span class="sxs-lookup"><span data-stu-id="c1a01-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c1a01-122">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c1a01-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a01-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c1a01-123">Requirements</span></span>  
 <span data-ttu-id="c1a01-124">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1a01-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1a01-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c1a01-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c1a01-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c1a01-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1a01-127">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1a01-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a01-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1a01-128">See Also</span></span>  
 [<span data-ttu-id="c1a01-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c1a01-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c1a01-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="c1a01-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
