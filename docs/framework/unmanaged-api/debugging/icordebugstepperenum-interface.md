---
title: ICorDebugStepperEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugStepperEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepperEnum
helpviewer_keywords:
- ICorDebugStepperEnum interface [.NET Framework debugging]
ms.assetid: 988718c1-1a4a-40f2-a04c-7d67e5cfe1e2
topic_type:
- apiref
ms.openlocfilehash: feaf5bd25e276bb93c076f200912965c612af453
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139001"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="f3ff1-102">ICorDebugStepperEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3ff1-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="f3ff1-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugStepper.</span><span class="sxs-lookup"><span data-stu-id="f3ff1-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f3ff1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f3ff1-104">Methods</span></span>  
  
|<span data-ttu-id="f3ff1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f3ff1-105">Method</span></span>|<span data-ttu-id="f3ff1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f3ff1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f3ff1-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f3ff1-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-next-method.md)|<span data-ttu-id="f3ff1-108">Získá zadaný počet instancí `ICorDebugStepper` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="f3ff1-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3ff1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3ff1-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f3ff1-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f3ff1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3ff1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3ff1-111">Requirements</span></span>  
 <span data-ttu-id="f3ff1-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3ff1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3ff1-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f3ff1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3ff1-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f3ff1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3ff1-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3ff1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3ff1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3ff1-116">See also</span></span>

- [<span data-ttu-id="f3ff1-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f3ff1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
