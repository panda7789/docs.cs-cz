---
title: ICorDebugBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint
helpviewer_keywords: ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cd2c4245b5e3dcc4f7b989a3ca9add8d568467cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="67ee3-102">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="67ee3-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="67ee3-103">Představuje zarážka v funkci nebo bod sledovat na hodnotě.</span><span class="sxs-lookup"><span data-stu-id="67ee3-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="67ee3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="67ee3-104">Methods</span></span>  
  
|<span data-ttu-id="67ee3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="67ee3-105">Method</span></span>|<span data-ttu-id="67ee3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="67ee3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="67ee3-107">Activate – metoda</span><span class="sxs-lookup"><span data-stu-id="67ee3-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="67ee3-108">Nastaví aktivní stav tohoto `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="67ee3-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="67ee3-109">IsActive – metoda</span><span class="sxs-lookup"><span data-stu-id="67ee3-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="67ee3-110">Získá hodnotu, která určuje, jestli to `ICorDebugBreakpoint` je aktivní.</span><span class="sxs-lookup"><span data-stu-id="67ee3-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="67ee3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="67ee3-111">Remarks</span></span>  
 <span data-ttu-id="67ee3-112">Zarážky přímo nepodporují podmíněné výrazy.</span><span class="sxs-lookup"><span data-stu-id="67ee3-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="67ee3-113">V případě potřeby tyto funkce ladicí program musí implementovat ho na `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="67ee3-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="67ee3-114">Rozšiřuje rozhraní ICorDebugFunctionBreakpoint `ICorDebugBreakpoint` pro podporu zarážky v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="67ee3-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="67ee3-115">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="67ee3-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67ee3-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="67ee3-116">Requirements</span></span>  
 <span data-ttu-id="67ee3-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="67ee3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="67ee3-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="67ee3-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="67ee3-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="67ee3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="67ee3-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67ee3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ee3-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="67ee3-121">See Also</span></span>  
 [<span data-ttu-id="67ee3-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="67ee3-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
