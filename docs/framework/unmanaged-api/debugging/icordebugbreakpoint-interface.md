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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159728"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="969e1-102">ICorDebugBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="969e1-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="969e1-103">Představuje zarážku ve funkci nebo bod sledování na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="969e1-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="969e1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="969e1-104">Methods</span></span>  
  
|<span data-ttu-id="969e1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="969e1-105">Method</span></span>|<span data-ttu-id="969e1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="969e1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="969e1-107">Activate – metoda</span><span class="sxs-lookup"><span data-stu-id="969e1-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="969e1-108">Nastaví aktivní stav `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="969e1-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="969e1-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="969e1-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="969e1-110">Získá hodnotu, která určuje, jestli to `ICorDebugBreakpoint` je aktivní.</span><span class="sxs-lookup"><span data-stu-id="969e1-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="969e1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="969e1-111">Remarks</span></span>  
 <span data-ttu-id="969e1-112">Zarážky přímo nepodporuje podmíněné výrazy.</span><span class="sxs-lookup"><span data-stu-id="969e1-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="969e1-113">Pokud se tato funkce požaduje, ladicí program musí implementovat ji nad `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="969e1-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="969e1-114">Icordebugfunctionbreakpoint – rozhraní rozšiřuje `ICorDebugBreakpoint` pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="969e1-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="969e1-115">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="969e1-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="969e1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="969e1-116">Requirements</span></span>  
 <span data-ttu-id="969e1-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="969e1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="969e1-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="969e1-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="969e1-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="969e1-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="969e1-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="969e1-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="969e1-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="969e1-121">See also</span></span>

- [<span data-ttu-id="969e1-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="969e1-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
