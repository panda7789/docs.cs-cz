---
title: "ICorDebugBlockingObjectEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBlockingObjectEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBlockingObjectEnum
helpviewer_keywords: ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b62da4047029881ddffff5faee9f06072407bfc6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="7b1b6-102">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b1b6-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="7b1b6-103">Poskytuje enumerátor pro seznam [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="7b1b6-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="7b1b6-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="7b1b6-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b1b6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7b1b6-105">Methods</span></span>  
  
|<span data-ttu-id="7b1b6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="7b1b6-106">Method</span></span>|<span data-ttu-id="7b1b6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7b1b6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b1b6-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7b1b6-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="7b1b6-109">Vytvoří výčet prostřednictvím seznam [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="7b1b6-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b1b6-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b1b6-110">Remarks</span></span>  
 <span data-ttu-id="7b1b6-111">Každý `CorDebugBlockingObject` struktura představuje objekt, který je blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="7b1b6-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b1b6-112">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="7b1b6-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b1b6-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b1b6-113">Requirements</span></span>  
 <span data-ttu-id="7b1b6-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b1b6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b1b6-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b1b6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b1b6-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b1b6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b1b6-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b1b6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b1b6-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="7b1b6-118">See Also</span></span>  
 [<span data-ttu-id="7b1b6-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b1b6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7b1b6-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="7b1b6-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
