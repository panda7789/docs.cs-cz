---
title: "ICorDebugNativeFrame2 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugNativeFrame2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugNativeFrame2
helpviewer_keywords: ICorDebugNativeFrame2 interface [.NET Framework debugging]
ms.assetid: 52a80838-af36-4399-bc97-d8a4c6d76df2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f501d49f007e22c6f7db0e759ee19b40f87b4b33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="78ec3-102">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78ec3-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="78ec3-103">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="78ec3-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78ec3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="78ec3-104">Methods</span></span>  
  
|<span data-ttu-id="78ec3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="78ec3-105">Method</span></span>|<span data-ttu-id="78ec3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="78ec3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78ec3-107">IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="78ec3-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="78ec3-108">Určuje, zda je aktuální snímek podřízeného rámce.</span><span class="sxs-lookup"><span data-stu-id="78ec3-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="78ec3-109">IsMatchingParentFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="78ec3-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="78ec3-110">Určuje, zda je zadaný rámečku nadřazeného aktuální snímek.</span><span class="sxs-lookup"><span data-stu-id="78ec3-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="78ec3-111">GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="78ec3-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="78ec3-112">Vrátí celková velikost všech parametrů v zásobníku na x86 operační systémy.</span><span class="sxs-lookup"><span data-stu-id="78ec3-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78ec3-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78ec3-113">Remarks</span></span>  
 <span data-ttu-id="78ec3-114">Toto rozhraní logicky rozšiřuje rozhraní "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="78ec3-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="78ec3-115">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="78ec3-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78ec3-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78ec3-116">Requirements</span></span>  
 <span data-ttu-id="78ec3-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78ec3-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78ec3-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78ec3-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78ec3-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78ec3-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78ec3-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78ec3-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ec3-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="78ec3-121">See Also</span></span>  
    
 [<span data-ttu-id="78ec3-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="78ec3-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="78ec3-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="78ec3-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
