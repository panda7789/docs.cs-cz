---
title: ICorDebugFunctionBreakpoint – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f15b9f5961699f905e765426576bdf6f3416793
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141151"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="f80d7-102">ICorDebugFunctionBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f80d7-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="f80d7-103">Rozšiřuje icordebugbreakpoint – rozhraní pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="f80d7-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f80d7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f80d7-104">Methods</span></span>  
  
|<span data-ttu-id="f80d7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f80d7-105">Method</span></span>|<span data-ttu-id="f80d7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f80d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f80d7-107">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="f80d7-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="f80d7-108">Získá ukazatel rozhraní ICorDebugFunction, který odkazuje na funkci, ve kterém je nastavena zarážka.</span><span class="sxs-lookup"><span data-stu-id="f80d7-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="f80d7-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="f80d7-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="f80d7-110">Získá posun zarážku v rámci této funkce.</span><span class="sxs-lookup"><span data-stu-id="f80d7-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f80d7-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f80d7-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f80d7-112">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="f80d7-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f80d7-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f80d7-113">Requirements</span></span>  
 <span data-ttu-id="f80d7-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f80d7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f80d7-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f80d7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f80d7-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f80d7-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f80d7-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f80d7-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f80d7-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f80d7-118">See also</span></span>

- [<span data-ttu-id="f80d7-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f80d7-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
