---
title: "ICorDebugBlockingObjectEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d35d4ee2ce3c1b7b0f54d78dba8b8639c522d509
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="9e801-102">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e801-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="9e801-103">Poskytuje enumerátor pro seznam [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="9e801-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="9e801-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="9e801-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e801-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9e801-105">Methods</span></span>  
  
|<span data-ttu-id="9e801-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9e801-106">Method</span></span>|<span data-ttu-id="9e801-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9e801-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e801-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="9e801-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="9e801-109">Vytvoří výčet prostřednictvím seznam [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="9e801-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9e801-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9e801-110">Remarks</span></span>  
 <span data-ttu-id="9e801-111">Každý `CorDebugBlockingObject` struktura představuje objekt, který je blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="9e801-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9e801-112">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="9e801-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e801-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e801-113">Requirements</span></span>  
 <span data-ttu-id="9e801-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e801-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e801-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9e801-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9e801-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e801-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e801-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e801-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e801-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e801-118">See Also</span></span>  
 [<span data-ttu-id="9e801-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9e801-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="9e801-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="9e801-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
