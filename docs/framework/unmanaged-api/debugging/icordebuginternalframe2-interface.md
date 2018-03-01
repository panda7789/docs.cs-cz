---
title: "ICorDebugInternalFrame2 – rozhraní"
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
- ICorDebugInternalFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame2
helpviewer_keywords:
- ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d87303fbe95804b458a42ed43b65f29233814977
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="0bcbf-102">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0bcbf-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="0bcbf-103">Poskytuje informace o interní rámce, včetně adres zásobníku a pozice ve vztahu k ICorDebugFrame objekty.</span><span class="sxs-lookup"><span data-stu-id="0bcbf-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0bcbf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0bcbf-104">Methods</span></span>  
  
|<span data-ttu-id="0bcbf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0bcbf-105">Method</span></span>|<span data-ttu-id="0bcbf-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0bcbf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0bcbf-107">GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="0bcbf-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="0bcbf-108">Vrátí adresu zásobníku vnitřní rámečku.</span><span class="sxs-lookup"><span data-stu-id="0bcbf-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="0bcbf-109">IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="0bcbf-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="0bcbf-110">Kontroluje, zda `this` interní rámečku je blíž ke listu než zadaný objekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="0bcbf-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0bcbf-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0bcbf-111">Remarks</span></span>  
 <span data-ttu-id="0bcbf-112">Toto rozhraní rozšiřuje icordebuginternalframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0bcbf-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0bcbf-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0bcbf-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bcbf-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0bcbf-114">Requirements</span></span>  
 <span data-ttu-id="0bcbf-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bcbf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bcbf-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0bcbf-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bcbf-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0bcbf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bcbf-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bcbf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bcbf-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bcbf-119">See Also</span></span>  
 [<span data-ttu-id="0bcbf-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0bcbf-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="0bcbf-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="0bcbf-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
