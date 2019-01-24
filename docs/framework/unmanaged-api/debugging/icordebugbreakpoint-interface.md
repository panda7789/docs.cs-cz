---
title: ICorDebugBreakpoint – rozhraní 1
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
ms.openlocfilehash: a222f578daed0ab81e2136e00d6f9b032acd95fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54744931"
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="c0da9-102">ICorDebugBreakpoint – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="c0da9-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="c0da9-103">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="c0da9-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c0da9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c0da9-104">Methods</span></span>  
  
|<span data-ttu-id="c0da9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c0da9-105">Method</span></span>|<span data-ttu-id="c0da9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c0da9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c0da9-107">Activate – metoda</span><span class="sxs-lookup"><span data-stu-id="c0da9-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="c0da9-108">Nastaví aktivní stav `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="c0da9-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="c0da9-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="c0da9-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="c0da9-110">Získá hodnotu, která určuje, jestli to `ICorDebugBreakpoint` je aktivní.</span><span class="sxs-lookup"><span data-stu-id="c0da9-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0da9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c0da9-111">Remarks</span></span>  
 <span data-ttu-id="c0da9-112">Zarážky přímo nepodporuje podmíněné výrazy.</span><span class="sxs-lookup"><span data-stu-id="c0da9-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="c0da9-113">Pokud se tato funkce požaduje, ladicí program musí implementovat ji nad `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="c0da9-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="c0da9-114">Icordebugfunctionbreakpoint – rozhraní rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="c0da9-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c0da9-115">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="c0da9-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0da9-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c0da9-116">Requirements</span></span>  
 <span data-ttu-id="c0da9-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0da9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0da9-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0da9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0da9-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0da9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0da9-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0da9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0da9-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0da9-121">See also</span></span>
- [<span data-ttu-id="c0da9-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c0da9-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
