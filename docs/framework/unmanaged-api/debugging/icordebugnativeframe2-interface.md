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
ms.openlocfilehash: cd2a2821128ad9265e8a831f7b02792e6453b1ee
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213787"
---
# <a name="icordebugnativeframe2-interface"></a><span data-ttu-id="b9b32-102">ICorDebugNativeFrame2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9b32-102">ICorDebugNativeFrame2 Interface</span></span>
<span data-ttu-id="b9b32-103">Poskytuje metody, které testují podřízené a nadřazené vztahy rámce.</span><span class="sxs-lookup"><span data-stu-id="b9b32-103">Provides methods that test for child and parent frame relationships.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9b32-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b9b32-104">Methods</span></span>  
  
|<span data-ttu-id="b9b32-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b9b32-105">Method</span></span>|<span data-ttu-id="b9b32-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b9b32-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9b32-107">IsChild – metoda</span><span class="sxs-lookup"><span data-stu-id="b9b32-107">IsChild Method</span></span>](icordebugnativeframe2-ischild-method.md)|<span data-ttu-id="b9b32-108">Určuje, zda je aktuální rámec podřízeným rámcem.</span><span class="sxs-lookup"><span data-stu-id="b9b32-108">Determines whether the current frame is a child frame.</span></span>|  
|[<span data-ttu-id="b9b32-109">IsMatchingParentFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="b9b32-109">IsMatchingParentFrame Method</span></span>](icordebugnativeframe2-ismatchingparentframe-method.md)|<span data-ttu-id="b9b32-110">Určuje, zda je určený rámec nadřazeným prvkem aktuálního rámce.</span><span class="sxs-lookup"><span data-stu-id="b9b32-110">Determines whether the specified frame is the parent of the current frame.</span></span>|  
|[<span data-ttu-id="b9b32-111">GetStackParameterSize – metoda</span><span class="sxs-lookup"><span data-stu-id="b9b32-111">GetStackParameterSize Method</span></span>](icordebugnativeframe2-getstackparametersize-method.md)|<span data-ttu-id="b9b32-112">Vrátí kumulativní velikost parametrů v zásobníku v operačních systémech x86.</span><span class="sxs-lookup"><span data-stu-id="b9b32-112">Returns the cumulative size of the parameters on the stack on x86 operating systems.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9b32-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b9b32-113">Remarks</span></span>  
 <span data-ttu-id="b9b32-114">Toto rozhraní logicky rozšiřuje rozhraní "ICorDebugNativeFrame".</span><span class="sxs-lookup"><span data-stu-id="b9b32-114">This interface logically extends the "ICorDebugNativeFrame" interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b9b32-115">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b9b32-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9b32-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9b32-116">Requirements</span></span>  
 <span data-ttu-id="b9b32-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9b32-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9b32-118">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b9b32-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9b32-119">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b9b32-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b9b32-120">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b9b32-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9b32-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9b32-121">See also</span></span>

- [<span data-ttu-id="b9b32-122">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9b32-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b9b32-123">Ladění</span><span class="sxs-lookup"><span data-stu-id="b9b32-123">Debugging</span></span>](index.md)
