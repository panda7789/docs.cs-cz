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
ms.openlocfilehash: a7876cd932558ad95dab7adac3c91a6f23ca647c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134658"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="bccb3-102">ICorDebugFunctionBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bccb3-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="bccb3-103">Rozšiřuje rozhraní ICorDebugBreakpoint pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="bccb3-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bccb3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bccb3-104">Methods</span></span>  
  
|<span data-ttu-id="bccb3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bccb3-105">Method</span></span>|<span data-ttu-id="bccb3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bccb3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bccb3-107">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="bccb3-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="bccb3-108">Získá ukazatel rozhraní na objekt ICorDebugFunction, který odkazuje na funkci, ve které je zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="bccb3-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="bccb3-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="bccb3-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="bccb3-110">Získá posunutí zarážky ve funkci.</span><span class="sxs-lookup"><span data-stu-id="bccb3-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bccb3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bccb3-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bccb3-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="bccb3-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bccb3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bccb3-113">Requirements</span></span>  
 <span data-ttu-id="bccb3-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bccb3-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bccb3-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bccb3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bccb3-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bccb3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bccb3-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bccb3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bccb3-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bccb3-118">See also</span></span>

- [<span data-ttu-id="bccb3-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bccb3-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
