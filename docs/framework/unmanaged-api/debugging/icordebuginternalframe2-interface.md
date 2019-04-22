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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087232"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="0541b-102">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0541b-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="0541b-103">Poskytuje informace o vnitřních rámcích, včetně adresy zásobníku a pozice ve vztahu k ICorDebugFrame objekty.</span><span class="sxs-lookup"><span data-stu-id="0541b-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0541b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0541b-104">Methods</span></span>  
  
|<span data-ttu-id="0541b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0541b-105">Method</span></span>|<span data-ttu-id="0541b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0541b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0541b-107">GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="0541b-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="0541b-108">Vrátí adresu vnitřní rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0541b-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="0541b-109">IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="0541b-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="0541b-110">Kontroluje, zda `this` vnitřní rámec je blíže než zadaný objekt ICorDebugFrame listu.</span><span class="sxs-lookup"><span data-stu-id="0541b-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0541b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0541b-111">Remarks</span></span>  
 <span data-ttu-id="0541b-112">Toto rozhraní rozšiřuje icordebuginternalframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0541b-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0541b-113">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="0541b-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0541b-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0541b-114">Requirements</span></span>  
 <span data-ttu-id="0541b-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0541b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0541b-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0541b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0541b-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0541b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0541b-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0541b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0541b-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0541b-119">See also</span></span>

- [<span data-ttu-id="0541b-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0541b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0541b-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="0541b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
