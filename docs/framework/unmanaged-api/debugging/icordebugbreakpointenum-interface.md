---
title: ICorDebugBreakpointEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: 5fb4a8a508cde4455bbee8c08432d3549e3fac43
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122760"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="a3dd4-102">ICorDebugBreakpointEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a3dd4-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="a3dd4-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="a3dd4-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3dd4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a3dd4-104">Methods</span></span>  
  
|<span data-ttu-id="a3dd4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a3dd4-105">Method</span></span>|<span data-ttu-id="a3dd4-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a3dd4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3dd4-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a3dd4-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="a3dd4-108">Získá zadaný počet instancí `ICorDebugBreakpoint` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="a3dd4-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3dd4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3dd4-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3dd4-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a3dd4-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3dd4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3dd4-111">Requirements</span></span>  
 <span data-ttu-id="a3dd4-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3dd4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3dd4-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a3dd4-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3dd4-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a3dd4-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3dd4-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3dd4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3dd4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3dd4-116">See also</span></span>

- [<span data-ttu-id="a3dd4-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a3dd4-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
