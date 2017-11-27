---
title: "ICorDebugInternalFrame2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame2
helpviewer_keywords: ICorDebugInternalFrame2 interface [.NET Framework debugging]
ms.assetid: d4755569-85b8-4ff4-bf50-0e608e76429f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b612cb2fb8b2a84555ccf36a8537ebecff673d47
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="13188-102">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="13188-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="13188-103">Poskytuje informace o interní rámce, včetně adres zásobníku a pozice ve vztahu k ICorDebugFrame objekty.</span><span class="sxs-lookup"><span data-stu-id="13188-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="13188-104">Metody</span><span class="sxs-lookup"><span data-stu-id="13188-104">Methods</span></span>  
  
|<span data-ttu-id="13188-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="13188-105">Method</span></span>|<span data-ttu-id="13188-106">Popis</span><span class="sxs-lookup"><span data-stu-id="13188-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="13188-107">Getframeaddress – metoda</span><span class="sxs-lookup"><span data-stu-id="13188-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="13188-108">Vrátí adresu zásobníku vnitřní rámečku.</span><span class="sxs-lookup"><span data-stu-id="13188-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="13188-109">Isclosertoleaf – metoda</span><span class="sxs-lookup"><span data-stu-id="13188-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="13188-110">Kontroluje, zda `this` interní rámečku je blíž ke listu než zadaný objekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="13188-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13188-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="13188-111">Remarks</span></span>  
 <span data-ttu-id="13188-112">Toto rozhraní rozšiřuje icordebuginternalframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="13188-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13188-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="13188-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13188-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="13188-114">Requirements</span></span>  
 <span data-ttu-id="13188-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13188-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13188-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13188-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13188-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13188-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="13188-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13188-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13188-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="13188-119">See Also</span></span>  
 [<span data-ttu-id="13188-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="13188-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="13188-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="13188-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
