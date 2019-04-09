---
title: ICorDebugDataTarget – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget
helpviewer_keywords:
- ICorDebugDataTarget interface [.NET Framework debugging]
ms.assetid: df5f05be-bed7-4f3c-bc89-dbb435d79a0b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 480fc27bd41f7ca559ceee379b7f6f81c94da0ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188705"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="d52af-102">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d52af-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="d52af-103">Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="d52af-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d52af-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d52af-104">Methods</span></span>  
  
|<span data-ttu-id="d52af-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d52af-105">Method</span></span>|<span data-ttu-id="d52af-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d52af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d52af-107">GetPlatform – metoda</span><span class="sxs-lookup"><span data-stu-id="d52af-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="d52af-108">Poskytuje informace o platformě, včetně architektury procesoru a operačního systému, na kterém je spuštěný Cílový proces.</span><span class="sxs-lookup"><span data-stu-id="d52af-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="d52af-109">ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="d52af-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="d52af-110">Získá blok souvislé paměti začínající na zadané adrese a vrátí jej v poskytnutá vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="d52af-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="d52af-111">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="d52af-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="d52af-112">Požádá o kontext aktuálního vlákna pro zadaný podproces.</span><span class="sxs-lookup"><span data-stu-id="d52af-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d52af-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d52af-113">Remarks</span></span>  
 `ICorDebugDataTarget` <span data-ttu-id="d52af-114">a její metody mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d52af-114">and its methods have the following characteristics:</span></span>  
  
-   <span data-ttu-id="d52af-115">Ladění služby volají metody na tomto rozhraní pro přístup k paměti a další data v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="d52af-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
-   <span data-ttu-id="d52af-116">Klient ladicího programu musí implementovat toto rozhraní podle potřeby pro konkrétní cíl (například živý proces nebo výpis stavu paměti).</span><span class="sxs-lookup"><span data-stu-id="d52af-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
-   <span data-ttu-id="d52af-117">`ICorDebugDataTarget` Metody lze volat pouze z v rámci metody implementované v ostatních `ICorDebug*` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d52af-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="d52af-118">Tím se zajistí, že klient ladicího programu má řídit, přes které vlákno je vyvolána na a kdy.</span><span class="sxs-lookup"><span data-stu-id="d52af-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
-   <span data-ttu-id="d52af-119">`ICorDebugDataTarget` Implementace musí vracet vždycky aktuální informace o cíli.</span><span class="sxs-lookup"><span data-stu-id="d52af-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="d52af-120">Cílový proces by měl být zastaven a nebyl změněn. žádným způsobem při `ICorDebug*` rozhraní (a tedy `ICorDebugDataTarget` metody) jsou volány.</span><span class="sxs-lookup"><span data-stu-id="d52af-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="d52af-121">Pokud je cílem živý proces a jeho změn stavu [iclrdebugging::openvirtualprocess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) musí být znovu volána k poskytnutí instance ICorDebugProcess nahrazení.</span><span class="sxs-lookup"><span data-stu-id="d52af-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d52af-122">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="d52af-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d52af-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d52af-123">Requirements</span></span>  
 <span data-ttu-id="d52af-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d52af-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d52af-125">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d52af-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d52af-126">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d52af-126">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d52af-127">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d52af-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d52af-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d52af-128">See also</span></span>

- [<span data-ttu-id="d52af-129">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d52af-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d52af-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="d52af-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
