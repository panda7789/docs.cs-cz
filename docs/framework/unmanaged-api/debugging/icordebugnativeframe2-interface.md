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
ms.openlocfilehash: dd8f1adee6bbcb3b57b87a2d6c85c01c624da9ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421227"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="5d601-102">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d601-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="5d601-103">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="5d601-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d601-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5d601-104">Methods</span></span>  
  
|<span data-ttu-id="5d601-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d601-105">Method</span></span>|<span data-ttu-id="5d601-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5d601-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d601-107">IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="5d601-107">IsChild Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="5d601-108">Určuje, zda je aktuální snímek podřízeného rámce.</span><span class="sxs-lookup"><span data-stu-id="5d601-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="5d601-109">IsMatchingParentFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="5d601-109">IsMatchingParentFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="5d601-110">Určuje, zda je zadaný rámečku nadřazeného aktuální snímek.</span><span class="sxs-lookup"><span data-stu-id="5d601-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="5d601-111">GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="5d601-111">GetStackParameterSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="5d601-112">Vrátí celková velikost všech parametrů v zásobníku na x86 operační systémy.</span><span class="sxs-lookup"><span data-stu-id="5d601-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d601-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d601-113">Remarks</span></span>  
 <span data-ttu-id="5d601-114">Toto rozhraní logicky rozšiřuje rozhraní "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="5d601-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d601-115">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="5d601-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d601-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d601-116">Requirements</span></span>  
 <span data-ttu-id="5d601-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d601-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d601-118">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d601-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d601-119">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d601-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d601-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d601-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d601-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d601-121">See Also</span></span>  
    
 [<span data-ttu-id="5d601-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="5d601-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="5d601-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="5d601-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
