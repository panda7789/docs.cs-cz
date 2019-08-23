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
ms.openlocfilehash: ed09b4f9be71c7f85714b9ee26d45018410fda42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917068"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="e9cca-102">ICorDebugFunctionBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9cca-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="e9cca-103">Rozšiřuje rozhraní ICorDebugBreakpoint pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="e9cca-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e9cca-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e9cca-104">Methods</span></span>  
  
|<span data-ttu-id="e9cca-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e9cca-105">Method</span></span>|<span data-ttu-id="e9cca-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e9cca-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e9cca-107">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="e9cca-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="e9cca-108">Získá ukazatel rozhraní na objekt ICorDebugFunction, který odkazuje na funkci, ve které je zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="e9cca-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="e9cca-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="e9cca-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="e9cca-110">Získá posunutí zarážky ve funkci.</span><span class="sxs-lookup"><span data-stu-id="e9cca-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9cca-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e9cca-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9cca-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e9cca-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9cca-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9cca-113">Requirements</span></span>  
 <span data-ttu-id="e9cca-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9cca-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9cca-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e9cca-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9cca-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9cca-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9cca-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9cca-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9cca-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9cca-118">See also</span></span>

- [<span data-ttu-id="e9cca-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e9cca-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
