---
title: ICorDebugBreakpoint – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a68e061c6def61746ee65f8a25818f8dbcd785b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159728"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="81bec-102">ICorDebugBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81bec-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="81bec-103">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="81bec-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="81bec-104">Metody</span><span class="sxs-lookup"><span data-stu-id="81bec-104">Methods</span></span>  
  
|<span data-ttu-id="81bec-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="81bec-105">Method</span></span>|<span data-ttu-id="81bec-106">Popis</span><span class="sxs-lookup"><span data-stu-id="81bec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="81bec-107">Activate – metoda</span><span class="sxs-lookup"><span data-stu-id="81bec-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="81bec-108">Nastaví aktivní stav `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="81bec-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="81bec-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="81bec-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="81bec-110">Získá hodnotu, která určuje, jestli to `ICorDebugBreakpoint` je aktivní.</span><span class="sxs-lookup"><span data-stu-id="81bec-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81bec-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81bec-111">Remarks</span></span>  
 <span data-ttu-id="81bec-112">Zarážky přímo nepodporuje podmíněné výrazy.</span><span class="sxs-lookup"><span data-stu-id="81bec-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="81bec-113">Pokud se tato funkce požaduje, ladicí program musí implementovat ji nad `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="81bec-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="81bec-114">Icordebugfunctionbreakpoint – rozhraní rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="81bec-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81bec-115">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="81bec-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81bec-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81bec-116">Requirements</span></span>  
 <span data-ttu-id="81bec-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81bec-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81bec-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="81bec-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81bec-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81bec-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81bec-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81bec-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81bec-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="81bec-121">See also</span></span>

- [<span data-ttu-id="81bec-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="81bec-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
