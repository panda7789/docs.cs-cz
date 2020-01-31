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
ms.openlocfilehash: aa0ff0ff7c8fe32f181fb86ee5b778ea618df3b2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791693"
---
# <a name="icordebugstepperenum-interface"></a><span data-ttu-id="e7779-102">ICorDebugStepperEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e7779-102">ICorDebugStepperEnum Interface</span></span>
<span data-ttu-id="e7779-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugStepper.</span><span class="sxs-lookup"><span data-stu-id="e7779-103">Implements ICorDebugEnum methods, and enumerates ICorDebugStepper arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e7779-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e7779-104">Methods</span></span>  
  
|<span data-ttu-id="e7779-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e7779-105">Method</span></span>|<span data-ttu-id="e7779-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e7779-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e7779-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="e7779-107">Next Method</span></span>](icordebugstepperenum-next-method.md)|<span data-ttu-id="e7779-108">Získá zadaný počet instancí `ICorDebugStepper` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="e7779-108">Gets the specified number of `ICorDebugStepper` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e7779-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e7779-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7779-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e7779-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7779-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7779-111">Requirements</span></span>  
 <span data-ttu-id="e7779-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7779-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7779-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e7779-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e7779-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e7779-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7779-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7779-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7779-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7779-116">See also</span></span>

- [<span data-ttu-id="e7779-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e7779-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
