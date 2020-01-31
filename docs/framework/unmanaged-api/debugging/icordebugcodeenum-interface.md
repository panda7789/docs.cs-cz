---
title: ICorDebugCodeEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum
helpviewer_keywords:
- ICorDebugCodeEnum interface [.NET Framework debugging]
ms.assetid: b5589171-a4a0-4c00-bbdc-6e0a42233b75
topic_type:
- apiref
ms.openlocfilehash: 127022fb8e9f9559ccb0f0c877d25db67eea3037
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784016"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="35fad-102">ICorDebugCodeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="35fad-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="35fad-103">Implementuje metody "ICorDebugEnum" a vytvoří výčet polí "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="35fad-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35fad-104">Metody</span><span class="sxs-lookup"><span data-stu-id="35fad-104">Methods</span></span>  
  
|<span data-ttu-id="35fad-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="35fad-105">Method</span></span>|<span data-ttu-id="35fad-106">Popis</span><span class="sxs-lookup"><span data-stu-id="35fad-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35fad-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="35fad-107">Next Method</span></span>](icordebugcodeenum-next-method.md)|<span data-ttu-id="35fad-108">Získá zadaný počet instancí `ICorDebugCode` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="35fad-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35fad-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35fad-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="35fad-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="35fad-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35fad-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35fad-111">Requirements</span></span>  
 <span data-ttu-id="35fad-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35fad-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35fad-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35fad-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35fad-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="35fad-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35fad-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35fad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35fad-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35fad-116">See also</span></span>

- [<span data-ttu-id="35fad-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="35fad-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
