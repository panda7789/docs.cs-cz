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
ms.openlocfilehash: 22a3f39bc1f9b4e6cad1db4fd0a6480b7c04e8fa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792757"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="23d0f-102">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="23d0f-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="23d0f-103">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="23d0f-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="23d0f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="23d0f-104">Methods</span></span>  
  
|<span data-ttu-id="23d0f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="23d0f-105">Method</span></span>|<span data-ttu-id="23d0f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="23d0f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="23d0f-107">IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="23d0f-107">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="23d0f-108">Určuje, zda je aktuální rámec podřízeným rámcem.</span><span class="sxs-lookup"><span data-stu-id="23d0f-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="23d0f-109">IsMatchingParentFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="23d0f-109">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="23d0f-110">Určuje, zda je určený rámec nadřazeným prvkem aktuálního rámce.</span><span class="sxs-lookup"><span data-stu-id="23d0f-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="23d0f-111">GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="23d0f-111">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="23d0f-112">Vrátí kumulativní velikost parametrů v zásobníku v operačních systémech x86.</span><span class="sxs-lookup"><span data-stu-id="23d0f-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="23d0f-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="23d0f-113">Remarks</span></span>  
 <span data-ttu-id="23d0f-114">Toto rozhraní logicky rozšiřuje rozhraní "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="23d0f-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="23d0f-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="23d0f-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23d0f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="23d0f-116">Requirements</span></span>  
 <span data-ttu-id="23d0f-117">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23d0f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23d0f-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="23d0f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="23d0f-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="23d0f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="23d0f-120">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23d0f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23d0f-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23d0f-121">See also</span></span>

- [<span data-ttu-id="23d0f-122">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="23d0f-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="23d0f-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="23d0f-123">Debugging</span></span>](index.md)
