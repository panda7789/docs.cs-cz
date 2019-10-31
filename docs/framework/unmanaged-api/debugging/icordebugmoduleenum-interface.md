---
title: ICorDebugModuleEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
ms.openlocfilehash: eaf00369cf77aaa1ba16879bae1b74aba2eb9eab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123531"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="0a2a6-102">ICorDebugModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0a2a6-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="0a2a6-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="0a2a6-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a2a6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0a2a6-104">Methods</span></span>  
  
|<span data-ttu-id="0a2a6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0a2a6-105">Method</span></span>|<span data-ttu-id="0a2a6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0a2a6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a2a6-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="0a2a6-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="0a2a6-108">Získá zadaný počet instancí `ICorDebugModule` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="0a2a6-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a2a6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a2a6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a2a6-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0a2a6-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a2a6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a2a6-111">Requirements</span></span>  
 <span data-ttu-id="0a2a6-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a2a6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a2a6-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0a2a6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a2a6-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0a2a6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a2a6-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a2a6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2a6-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a2a6-116">See also</span></span>

- [<span data-ttu-id="0a2a6-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0a2a6-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
