---
title: ICorDebugValueEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum
helpviewer_keywords:
- ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: 88989482-a09f-4bd0-9adb-16f47b0291fd
topic_type:
- apiref
ms.openlocfilehash: 4cc9849ee8cd160a33ae9c769f7b98a87eafb8dd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134603"
---
# <a name="icordebugvalueenum-interface"></a><span data-ttu-id="b262e-102">ICorDebugValueEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b262e-102">ICorDebugValueEnum Interface</span></span>
<span data-ttu-id="b262e-103">Implementuje metody "ICorDebugEnum" a vytvoří výčet polí "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="b262e-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugValue" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b262e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b262e-104">Methods</span></span>  
  
|<span data-ttu-id="b262e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b262e-105">Method</span></span>|<span data-ttu-id="b262e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b262e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b262e-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b262e-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-next-method.md)|<span data-ttu-id="b262e-108">Získá zadaný počet instancí `ICorDebugValue` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="b262e-108">Gets the specified number of `ICorDebugValue` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b262e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b262e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b262e-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b262e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b262e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b262e-111">Requirements</span></span>  
 <span data-ttu-id="b262e-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b262e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b262e-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b262e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b262e-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b262e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b262e-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b262e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b262e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b262e-116">See also</span></span>

- [<span data-ttu-id="b262e-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b262e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
