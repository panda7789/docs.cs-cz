---
title: ICorDebugBlockingObjectEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11693416d0a3e0afe80c2356ff0a12ecea0d8d15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959315"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="6e1c6-102">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e1c6-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="6e1c6-103">Poskytuje enumerátor pro seznam struktur [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="6e1c6-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="6e1c6-104">Toto rozhraní je podtřídou rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="6e1c6-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6e1c6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6e1c6-105">Methods</span></span>  
  
|<span data-ttu-id="6e1c6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c6-106">Method</span></span>|<span data-ttu-id="6e1c6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6e1c6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6e1c6-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="6e1c6-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="6e1c6-109">Provede výčet ze seznamu [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktur.</span><span class="sxs-lookup"><span data-stu-id="6e1c6-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6e1c6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6e1c6-110">Remarks</span></span>  
 <span data-ttu-id="6e1c6-111">Každá `CorDebugBlockingObject` struktura představuje objekt, který blokuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="6e1c6-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6e1c6-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="6e1c6-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e1c6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e1c6-113">Requirements</span></span>  
 <span data-ttu-id="6e1c6-114">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e1c6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e1c6-115">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6e1c6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e1c6-116">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e1c6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e1c6-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e1c6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e1c6-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e1c6-118">See also</span></span>

- [<span data-ttu-id="6e1c6-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="6e1c6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6e1c6-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="6e1c6-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
