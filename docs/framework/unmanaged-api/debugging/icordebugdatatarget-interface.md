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
ms.openlocfilehash: 0c6a8ee1bcc65e640ef871e57acdeef21acd7896
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930821"
---
# <a name="icordebugdatatarget-interface"></a><span data-ttu-id="24af8-102">ICorDebugDataTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24af8-102">ICorDebugDataTarget Interface</span></span>
<span data-ttu-id="24af8-103">Poskytuje rozhraní zpětného volání, které poskytuje přístup ke konkrétnímu cílovému procesu.</span><span class="sxs-lookup"><span data-stu-id="24af8-103">Provides a callback interface that provides access to a particular target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="24af8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="24af8-104">Methods</span></span>  
  
|<span data-ttu-id="24af8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="24af8-105">Method</span></span>|<span data-ttu-id="24af8-106">Popis</span><span class="sxs-lookup"><span data-stu-id="24af8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="24af8-107">GetPlatform – metoda</span><span class="sxs-lookup"><span data-stu-id="24af8-107">GetPlatform Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)|<span data-ttu-id="24af8-108">Obsahuje informace o platformě, včetně architektury procesoru a operačního systému, na kterých je spuštěn cílový proces.</span><span class="sxs-lookup"><span data-stu-id="24af8-108">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>|  
|[<span data-ttu-id="24af8-109">ReadVirtual – metoda</span><span class="sxs-lookup"><span data-stu-id="24af8-109">ReadVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-readvirtual-method.md)|<span data-ttu-id="24af8-110">Načte blok souvislé paměti začínající na zadané adrese a vrátí ji do zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="24af8-110">Gets a block of contiguous memory starting at the specified address, and returns it in the supplied buffer.</span></span>|  
|[<span data-ttu-id="24af8-111">GetThreadContext – metoda</span><span class="sxs-lookup"><span data-stu-id="24af8-111">GetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getthreadcontext-method.md)|<span data-ttu-id="24af8-112">Vyžádá aktuální kontext vlákna pro zadané vlákno.</span><span class="sxs-lookup"><span data-stu-id="24af8-112">Requests the current thread context for the specified thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24af8-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24af8-113">Remarks</span></span>  
 <span data-ttu-id="24af8-114">`ICorDebugDataTarget`a jeho metody mají následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="24af8-114">`ICorDebugDataTarget` and its methods have the following characteristics:</span></span>  
  
- <span data-ttu-id="24af8-115">Metody volání služby ladění v tomto rozhraní pro přístup k paměti a dalším datům v cílovém procesu.</span><span class="sxs-lookup"><span data-stu-id="24af8-115">The debugging services call methods on this interface to access memory and other data in the target process.</span></span>  
  
- <span data-ttu-id="24af8-116">Klient ladicího programu musí implementovat toto rozhraní v závislosti na konkrétním cíli (například při živém procesu nebo výpisu paměti).</span><span class="sxs-lookup"><span data-stu-id="24af8-116">The debugger client must implement this interface as appropriate for the particular target (for example, a live process or a memory dump).</span></span>  
  
- <span data-ttu-id="24af8-117">Metody lze vyvolat pouze v rámci metod implementovaných v jiných `ICorDebug*` rozhraních. `ICorDebugDataTarget`</span><span class="sxs-lookup"><span data-stu-id="24af8-117">The `ICorDebugDataTarget` methods can be invoked only from within methods implemented in other `ICorDebug*` interfaces.</span></span> <span data-ttu-id="24af8-118">Tím je zajištěno, že klient ladicího programu má kontrolu nad tím, ve kterém vlákně je vyvoláno, a kdy.</span><span class="sxs-lookup"><span data-stu-id="24af8-118">This ensures that the debugger client has control over which thread it is invoked on, and when.</span></span>  
  
- <span data-ttu-id="24af8-119">`ICorDebugDataTarget` Implementace musí vždycky vracet aktuální informace o cíli.</span><span class="sxs-lookup"><span data-stu-id="24af8-119">The `ICorDebugDataTarget` implementation must always return up-to-date information about the target.</span></span>  
  
 <span data-ttu-id="24af8-120">Při `ICorDebug*` volání rozhraní (a tudíž `ICorDebugDataTarget` metod) by se měl cílový proces zastavit a nijak beze změny.</span><span class="sxs-lookup"><span data-stu-id="24af8-120">The target process should be stopped and not changed in any way while `ICorDebug*` interfaces (and therefore `ICorDebugDataTarget` methods) are being called.</span></span> <span data-ttu-id="24af8-121">Pokud je cílem živý proces a jeho změny stavu, metoda [ICLRDebugging:: OpenVirtualProcess –](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) musí být znovu volána, aby poskytovala náhradní instanci ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="24af8-121">If the target is a live process and its state changes, the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method has to be called again to provide a replacement ICorDebugProcess instance.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24af8-122">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="24af8-122">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24af8-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24af8-123">Requirements</span></span>  
 <span data-ttu-id="24af8-124">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24af8-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24af8-125">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="24af8-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="24af8-126">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24af8-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24af8-127">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24af8-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24af8-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24af8-128">See also</span></span>

- [<span data-ttu-id="24af8-129">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="24af8-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="24af8-130">Ladění</span><span class="sxs-lookup"><span data-stu-id="24af8-130">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
