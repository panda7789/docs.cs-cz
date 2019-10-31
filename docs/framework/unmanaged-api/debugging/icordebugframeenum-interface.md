---
title: ICorDebugFrameEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
ms.openlocfilehash: 3a33d25ee13e12a2612d0132da1dc84c24f2f95b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73090543"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="1be55-102">ICorDebugFrameEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1be55-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="1be55-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="1be55-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1be55-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1be55-104">Methods</span></span>  
  
|<span data-ttu-id="1be55-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1be55-105">Method</span></span>|<span data-ttu-id="1be55-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1be55-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1be55-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="1be55-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="1be55-108">Získá zadaný počet instancí `ICorDebugFrame` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="1be55-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1be55-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1be55-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1be55-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="1be55-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1be55-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1be55-111">Requirements</span></span>  
 <span data-ttu-id="1be55-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1be55-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1be55-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1be55-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1be55-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1be55-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1be55-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1be55-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1be55-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1be55-116">See also</span></span>

- [<span data-ttu-id="1be55-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1be55-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
