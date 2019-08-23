---
title: ICorDebugTypeEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugTypeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugTypeEnum
helpviewer_keywords:
- ICorDebugTypeEnum interface [.NET Framework debugging]
ms.assetid: 159ccfcf-b37c-4ad9-8e0d-a9a443262472
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b81230ee901510b2859b45de76c6dcfa6cb28e58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968187"
---
# <a name="icordebugtypeenum-interface"></a><span data-ttu-id="8d434-102">ICorDebugTypeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="8d434-102">ICorDebugTypeEnum Interface</span></span>
<span data-ttu-id="8d434-103">Implementuje metody "ICorDebugEnum" a vytvoří výčet polí "ICorDebugType".</span><span class="sxs-lookup"><span data-stu-id="8d434-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugType" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8d434-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8d434-104">Methods</span></span>  
  
|<span data-ttu-id="8d434-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8d434-105">Method</span></span>|<span data-ttu-id="8d434-106">Popis</span><span class="sxs-lookup"><span data-stu-id="8d434-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8d434-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="8d434-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-next-method.md)|<span data-ttu-id="8d434-108">Získá zadaný počet `ICorDebugType` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="8d434-108">Gets the specified number of `ICorDebugType` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d434-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d434-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8d434-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="8d434-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d434-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d434-111">Requirements</span></span>  
 <span data-ttu-id="8d434-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d434-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d434-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8d434-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d434-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d434-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d434-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d434-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d434-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d434-116">See also</span></span>

- [<span data-ttu-id="8d434-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="8d434-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
