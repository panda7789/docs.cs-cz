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
ms.openlocfilehash: 5e3804335bacefad61c4f521ea1ef1444b7b1fed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777711"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="e8651-102">ICorDebugFunctionBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8651-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="e8651-103">Rozšiřuje rozhraní ICorDebugBreakpoint pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="e8651-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8651-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e8651-104">Methods</span></span>  
  
|<span data-ttu-id="e8651-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e8651-105">Method</span></span>|<span data-ttu-id="e8651-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e8651-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8651-107">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="e8651-107">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="e8651-108">Získá ukazatel rozhraní na objekt ICorDebugFunction, který odkazuje na funkci, ve které je zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="e8651-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="e8651-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e8651-109">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="e8651-110">Získá posunutí zarážky ve funkci.</span><span class="sxs-lookup"><span data-stu-id="e8651-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8651-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8651-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8651-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e8651-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8651-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8651-113">Requirements</span></span>  
 <span data-ttu-id="e8651-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8651-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8651-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e8651-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8651-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e8651-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8651-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8651-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8651-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8651-118">See also</span></span>

- [<span data-ttu-id="e8651-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e8651-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
