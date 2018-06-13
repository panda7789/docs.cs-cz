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
ms.openlocfilehash: f4082c4204b85aba97651419db15ba8eb4c3d54e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415159"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="2e6ff-102">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e6ff-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="2e6ff-103">Poskytuje informace o interní rámce, včetně adres zásobníku a pozice ve vztahu k ICorDebugFrame objekty.</span><span class="sxs-lookup"><span data-stu-id="2e6ff-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2e6ff-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2e6ff-104">Methods</span></span>  
  
|<span data-ttu-id="2e6ff-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2e6ff-105">Method</span></span>|<span data-ttu-id="2e6ff-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2e6ff-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2e6ff-107">GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="2e6ff-107">GetFrameAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="2e6ff-108">Vrátí adresu zásobníku vnitřní rámečku.</span><span class="sxs-lookup"><span data-stu-id="2e6ff-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="2e6ff-109">IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="2e6ff-109">IsCloserToLeaf Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="2e6ff-110">Kontroluje, zda `this` interní rámečku je blíž ke listu než zadaný objekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="2e6ff-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2e6ff-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2e6ff-111">Remarks</span></span>  
 <span data-ttu-id="2e6ff-112">Toto rozhraní rozšiřuje icordebuginternalframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2e6ff-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e6ff-113">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="2e6ff-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e6ff-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e6ff-114">Requirements</span></span>  
 <span data-ttu-id="2e6ff-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e6ff-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e6ff-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2e6ff-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2e6ff-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2e6ff-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2e6ff-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e6ff-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e6ff-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e6ff-119">See Also</span></span>  
 [<span data-ttu-id="2e6ff-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="2e6ff-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="2e6ff-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="2e6ff-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
