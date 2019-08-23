---
title: ICorDebugNativeFrame2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame2
helpviewer_keywords:
- ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 638ce7933ededf2ff7b03b1c5aed7f6bdbfebc6c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912793"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="12af3-102">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="12af3-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="12af3-103">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="12af3-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="12af3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="12af3-104">Methods</span></span>  
  
|<span data-ttu-id="12af3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="12af3-105">Method</span></span>|<span data-ttu-id="12af3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="12af3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="12af3-107">IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="12af3-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="12af3-108">Určuje, zda je aktuální rámec podřízeným rámcem.</span><span class="sxs-lookup"><span data-stu-id="12af3-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="12af3-109">IsMatchingParentFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="12af3-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="12af3-110">Určuje, zda je určený rámec nadřazeným prvkem aktuálního rámce.</span><span class="sxs-lookup"><span data-stu-id="12af3-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="12af3-111">GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="12af3-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="12af3-112">Vrátí kumulativní velikost parametrů v zásobníku v operačních systémech x86.</span><span class="sxs-lookup"><span data-stu-id="12af3-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12af3-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="12af3-113">Remarks</span></span>  
 <span data-ttu-id="12af3-114">Toto rozhraní logicky rozšiřuje rozhraní "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="12af3-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="12af3-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="12af3-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12af3-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12af3-116">Requirements</span></span>  
 <span data-ttu-id="12af3-117">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12af3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12af3-118">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="12af3-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12af3-119">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12af3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12af3-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12af3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12af3-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12af3-121">See also</span></span>

- [<span data-ttu-id="12af3-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="12af3-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="12af3-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="12af3-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
