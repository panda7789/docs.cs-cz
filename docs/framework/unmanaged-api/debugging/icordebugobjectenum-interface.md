---
title: ICorDebugObjectEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectEnum
helpviewer_keywords:
- ICorDebugObjectEnum interface [.NET Framework debugging]
ms.assetid: 9ffb4498-7719-49d3-8890-df2c22248a0c
topic_type:
- apiref
ms.openlocfilehash: b77d5859986c90d6ef61c02547014d0bec354106
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096144"
---
# <a name="icordebugobjectenum-interface"></a><span data-ttu-id="4c728-102">ICorDebugObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4c728-102">ICorDebugObjectEnum Interface</span></span>

<span data-ttu-id="4c728-103">Implementuje metody ICorDebugEnum a vytváří výčet polí objektů podle jejich relativních virtuálních adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="4c728-103">Implements ICorDebugEnum methods, and enumerates arrays of objects by their relative virtual addresses (RVAs).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c728-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4c728-104">Methods</span></span>  
  
|<span data-ttu-id="4c728-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4c728-105">Method</span></span>|<span data-ttu-id="4c728-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4c728-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c728-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="4c728-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-next-method.md)|<span data-ttu-id="4c728-108">Získá RVA zadaného počtu objektů z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="4c728-108">Gets the RVAs of the specified number of objects from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c728-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c728-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4c728-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4c728-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c728-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4c728-111">Requirements</span></span>  
 <span data-ttu-id="4c728-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c728-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c728-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4c728-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4c728-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4c728-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c728-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c728-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c728-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c728-116">See also</span></span>

- [<span data-ttu-id="4c728-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4c728-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
