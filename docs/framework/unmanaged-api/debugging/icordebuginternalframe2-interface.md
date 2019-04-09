---
title: ICorDebugInternalFrame2 – rozhraní
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cf75de6a71cfbe25cbde281f837060b88e93753
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087232"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="a5eb3-102">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5eb3-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="a5eb3-103">Poskytuje informace o vnitřních rámcích, včetně adresy zásobníku a pozice ve vztahu k ICorDebugFrame objekty.</span><span class="sxs-lookup"><span data-stu-id="a5eb3-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a5eb3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a5eb3-104">Methods</span></span>  
  
|<span data-ttu-id="a5eb3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a5eb3-105">Method</span></span>|<span data-ttu-id="a5eb3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a5eb3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a5eb3-107">GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="a5eb3-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="a5eb3-108">Vrátí adresu vnitřní rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="a5eb3-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="a5eb3-109">IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="a5eb3-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="a5eb3-110">Kontroluje, zda `this` vnitřní rámec je blíže než zadaný objekt ICorDebugFrame listu.</span><span class="sxs-lookup"><span data-stu-id="a5eb3-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a5eb3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a5eb3-111">Remarks</span></span>  
 <span data-ttu-id="a5eb3-112">Toto rozhraní rozšiřuje icordebuginternalframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a5eb3-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a5eb3-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="a5eb3-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5eb3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5eb3-114">Requirements</span></span>  
 <span data-ttu-id="a5eb3-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5eb3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5eb3-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a5eb3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5eb3-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5eb3-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a5eb3-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a5eb3-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a5eb3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5eb3-119">See also</span></span>

- [<span data-ttu-id="a5eb3-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a5eb3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a5eb3-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="a5eb3-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
