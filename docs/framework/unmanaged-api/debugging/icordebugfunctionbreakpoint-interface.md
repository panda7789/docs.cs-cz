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
ms.openlocfilehash: 6a378e3579ab9ea8d9534a408d0e456373616cad
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213134"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="76cf2-102">ICorDebugFunctionBreakpoint – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76cf2-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="76cf2-103">Rozšiřuje rozhraní ICorDebugBreakpoint pro podporu zarážek v rámci funkcí.</span><span class="sxs-lookup"><span data-stu-id="76cf2-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="76cf2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="76cf2-104">Methods</span></span>  
  
|<span data-ttu-id="76cf2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="76cf2-105">Method</span></span>|<span data-ttu-id="76cf2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="76cf2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="76cf2-107">GetFunction – metoda</span><span class="sxs-lookup"><span data-stu-id="76cf2-107">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="76cf2-108">Získá ukazatel rozhraní na objekt ICorDebugFunction, který odkazuje na funkci, ve které je zarážka nastavena.</span><span class="sxs-lookup"><span data-stu-id="76cf2-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="76cf2-109">GetOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="76cf2-109">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="76cf2-110">Získá posunutí zarážky ve funkci.</span><span class="sxs-lookup"><span data-stu-id="76cf2-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="76cf2-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="76cf2-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76cf2-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="76cf2-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76cf2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76cf2-113">Requirements</span></span>  
 <span data-ttu-id="76cf2-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76cf2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76cf2-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="76cf2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="76cf2-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="76cf2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76cf2-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76cf2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76cf2-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="76cf2-118">See also</span></span>

- [<span data-ttu-id="76cf2-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="76cf2-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
