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
ms.openlocfilehash: 9e333d71505a055cfe27df2c79a102c939bafc9d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788480"
---
# <a name="icordebuginternalframe2-interface"></a><span data-ttu-id="d0738-102">ICorDebugInternalFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0738-102">ICorDebugInternalFrame2 Interface</span></span>
<span data-ttu-id="d0738-103">Obsahuje informace o vnitřních rámečcích, včetně adresy zásobníku a pozice ve vztahu k ICorDebugFrame objektům.</span><span class="sxs-lookup"><span data-stu-id="d0738-103">Provides information about internal frames, including stack address and position in relation to ICorDebugFrame objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0738-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d0738-104">Methods</span></span>  
  
|<span data-ttu-id="d0738-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d0738-105">Method</span></span>|<span data-ttu-id="d0738-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d0738-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0738-107">GetFrameAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="d0738-107">GetFrameAddress Method</span></span>](icordebuginternalframe2-getframeaddress-method.md)|<span data-ttu-id="d0738-108">Vrátí adresu zásobníku interního rámce.</span><span class="sxs-lookup"><span data-stu-id="d0738-108">Returns the stack address of the internal frame.</span></span>|  
|[<span data-ttu-id="d0738-109">IsCloserToLeaf – metoda</span><span class="sxs-lookup"><span data-stu-id="d0738-109">IsCloserToLeaf Method</span></span>](icordebuginternalframe2-isclosertoleaf-method.md)|<span data-ttu-id="d0738-110">Kontroluje, zda je vnitřní rámec `this` blíž k listu, než je zadaný objekt ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="d0738-110">Checks whether the `this` internal frame is closer to the leaf than the specified ICorDebugFrame object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0738-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0738-111">Remarks</span></span>  
 <span data-ttu-id="d0738-112">Toto rozhraní rozšiřuje rozhraní ICorDebugInternalFrame.</span><span class="sxs-lookup"><span data-stu-id="d0738-112">This interface extends the ICorDebugInternalFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0738-113">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="d0738-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0738-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0738-114">Requirements</span></span>  
 <span data-ttu-id="d0738-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0738-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0738-116">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0738-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0738-117">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d0738-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0738-118">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0738-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0738-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0738-119">See also</span></span>

- [<span data-ttu-id="d0738-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d0738-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="d0738-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="d0738-121">Debugging</span></span>](index.md)
