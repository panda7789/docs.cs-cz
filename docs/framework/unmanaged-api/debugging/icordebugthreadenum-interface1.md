---
title: ICorDebugThreadEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
ms.openlocfilehash: 6969c23bcf3ea19bf6e404996d477f669f0eee5b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122408"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="1dd3d-102">ICorDebugThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1dd3d-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="1dd3d-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1dd3d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1dd3d-104">Methods</span></span>  
  
|<span data-ttu-id="1dd3d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1dd3d-105">Method</span></span>|<span data-ttu-id="1dd3d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1dd3d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1dd3d-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="1dd3d-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="1dd3d-108">Získá zadaný počet instancí `ICorDebugThread` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1dd3d-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1dd3d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1dd3d-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="1dd3d-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd3d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1dd3d-111">Requirements</span></span>  
 <span data-ttu-id="1dd3d-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd3d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd3d-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1dd3d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1dd3d-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1dd3d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dd3d-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd3d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd3d-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1dd3d-116">See also</span></span>

- [<span data-ttu-id="1dd3d-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1dd3d-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
