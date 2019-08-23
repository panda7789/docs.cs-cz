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
ms.openlocfilehash: 2377773b471b387376f0284522ebe29d6b003ae3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910114"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="fc859-102">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fc859-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="fc859-103">Obsahuje informace o vnitřních rámečcích, včetně adresy zásobníku a pozice ve vztahu k ICorDebugFrame objektům.</span><span class="sxs-lookup"><span data-stu-id="fc859-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fc859-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fc859-104">Methods</span></span>  
  
|<span data-ttu-id="fc859-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fc859-105">Method</span></span>|<span data-ttu-id="fc859-106">Popis</span><span class="sxs-lookup"><span data-stu-id="fc859-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fc859-107">GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="fc859-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="fc859-108">Vrátí adresu zásobníku interního rámce.</span><span class="sxs-lookup"><span data-stu-id="fc859-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="fc859-109">IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="fc859-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="fc859-110">Kontroluje, zda `this` je interní rámec blíže k listu, než je zadaný objekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="fc859-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc859-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fc859-111">Remarks</span></span>  
 <span data-ttu-id="fc859-112">Toto rozhraní rozšiřuje rozhraní ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="fc859-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc859-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="fc859-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc859-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc859-114">Requirements</span></span>  
 <span data-ttu-id="fc859-115">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc859-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc859-116">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fc859-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc859-117">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc859-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc859-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc859-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc859-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fc859-119">See also</span></span>

- [<span data-ttu-id="fc859-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fc859-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="fc859-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="fc859-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
