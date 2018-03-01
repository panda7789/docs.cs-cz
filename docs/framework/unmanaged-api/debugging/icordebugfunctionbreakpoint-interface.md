---
title: ICorDebugFunctionBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 019a94243773fcb1751f419d8e38a6759fa1d3bd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="f7df9-102">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="f7df9-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="f7df9-103">Rozšiřuje rozhraní ICorDebugBreakpoint pro podporu zarážky v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="f7df9-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7df9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f7df9-104">Methods</span></span>  
  
|<span data-ttu-id="f7df9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f7df9-105">Method</span></span>|<span data-ttu-id="f7df9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f7df9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7df9-107">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="f7df9-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="f7df9-108">Získá ukazatele rozhraní umožňuje ICorDebugFunction, který odkazuje na funkci, ve kterém je nastaven breakpoint.</span><span class="sxs-lookup"><span data-stu-id="f7df9-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="f7df9-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f7df9-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="f7df9-110">Získá posun zarážek v rámci funkce.</span><span class="sxs-lookup"><span data-stu-id="f7df9-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7df9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7df9-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f7df9-112">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f7df9-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7df9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7df9-113">Requirements</span></span>  
 <span data-ttu-id="f7df9-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7df9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7df9-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7df9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7df9-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7df9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7df9-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7df9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7df9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7df9-118">See Also</span></span>  
 [<span data-ttu-id="f7df9-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7df9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
