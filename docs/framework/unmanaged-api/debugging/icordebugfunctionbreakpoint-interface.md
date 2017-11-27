---
title: ICorDebugFunctionBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunctionBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunctionBreakpoint
helpviewer_keywords: ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 910317bea8af3a80ee66544651de2372808734bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="9cb6f-102">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="9cb6f-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="9cb6f-103">Rozšiřuje rozhraní ICorDebugBreakpoint pro podporu zarážky v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="9cb6f-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9cb6f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9cb6f-104">Methods</span></span>  
  
|<span data-ttu-id="9cb6f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9cb6f-105">Method</span></span>|<span data-ttu-id="9cb6f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9cb6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9cb6f-107">Getfunction – metoda</span><span class="sxs-lookup"><span data-stu-id="9cb6f-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="9cb6f-108">Získá ukazatele rozhraní umožňuje ICorDebugFunction, který odkazuje na funkci, ve kterém je nastaven breakpoint.</span><span class="sxs-lookup"><span data-stu-id="9cb6f-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="9cb6f-109">Getoffset – metoda</span><span class="sxs-lookup"><span data-stu-id="9cb6f-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="9cb6f-110">Získá posun zarážek v rámci funkce.</span><span class="sxs-lookup"><span data-stu-id="9cb6f-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cb6f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9cb6f-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9cb6f-112">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="9cb6f-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb6f-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9cb6f-113">Requirements</span></span>  
 <span data-ttu-id="9cb6f-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cb6f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb6f-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cb6f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cb6f-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cb6f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cb6f-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb6f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb6f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9cb6f-118">See Also</span></span>  
 [<span data-ttu-id="9cb6f-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="9cb6f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
