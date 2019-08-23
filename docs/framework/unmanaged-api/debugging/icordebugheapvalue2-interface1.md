---
title: ICorDebugHeapValue2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2
helpviewer_keywords:
- ICorDebugHeapValue2 interface [.NET Framework debugging]
ms.assetid: 87360a52-90b1-4ada-80c0-589a556116d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fa872453ed72a3095c135aa25e81284610ad2436
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910209"
---
# <a name="icordebugheapvalue2-interface"></a><span data-ttu-id="cd836-102">ICorDebugHeapValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cd836-102">ICorDebugHeapValue2 Interface</span></span>

<span data-ttu-id="cd836-103">Rozšíření ICorDebugHeapValue, které poskytuje podporu pro obslužné rutiny modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="cd836-103">An extension of ICorDebugHeapValue that provides support for common language runtime (CLR) handles.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cd836-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cd836-104">Methods</span></span>  
  
|<span data-ttu-id="cd836-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cd836-105">Method</span></span>|<span data-ttu-id="cd836-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cd836-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cd836-107">CreateHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="cd836-107">CreateHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-createhandle-method.md)|<span data-ttu-id="cd836-108">Vytvoří popisovač zadaného typu pro tento `ICorDebugHeapValue2` objekt.</span><span class="sxs-lookup"><span data-stu-id="cd836-108">Creates a handle of the specified type for this `ICorDebugHeapValue2` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd836-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd836-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cd836-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="cd836-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd836-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd836-111">Requirements</span></span>  
 <span data-ttu-id="cd836-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd836-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd836-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cd836-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd836-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd836-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd836-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd836-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd836-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd836-116">See also</span></span>

- [<span data-ttu-id="cd836-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cd836-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
