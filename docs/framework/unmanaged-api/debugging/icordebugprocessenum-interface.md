---
title: ICorDebugProcessEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum
helpviewer_keywords:
- ICorDebugProcessEnum interface [.NET Framework debugging]
ms.assetid: b63a507a-ca97-4be0-8e4f-401cce2125f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81653c69353b60d7287240505f53b26552c21774
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960981"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="f7623-102">ICorDebugProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7623-102">ICorDebugProcessEnum Interface</span></span>
<span data-ttu-id="f7623-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="f7623-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7623-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f7623-104">Methods</span></span>  
  
|<span data-ttu-id="f7623-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f7623-105">Method</span></span>|<span data-ttu-id="f7623-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f7623-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7623-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f7623-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-next-method.md)|<span data-ttu-id="f7623-108">Získá zadaný počet `ICorDebugProcess` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="f7623-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7623-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7623-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7623-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f7623-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7623-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7623-111">Requirements</span></span>  
 <span data-ttu-id="f7623-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7623-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7623-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7623-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7623-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7623-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7623-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7623-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7623-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7623-116">See also</span></span>

- [<span data-ttu-id="f7623-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7623-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
