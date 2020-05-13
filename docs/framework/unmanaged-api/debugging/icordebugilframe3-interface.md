---
title: ICorDebugILFrame3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
ms.openlocfilehash: 59221b09cc1c5d2d01c1007b649a4bb01de57f04
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213761"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="3cc5c-102">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cc5c-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="3cc5c-103">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="3cc5c-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="3cc5c-104">`ICorDebugILFrame3`je logickým rozšířením rozhraní ICorDebugILFrame a ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="3cc5c-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3cc5c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3cc5c-105">Methods</span></span>  
  
|<span data-ttu-id="3cc5c-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3cc5c-106">Method</span></span>|<span data-ttu-id="3cc5c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3cc5c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3cc5c-108">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="3cc5c-108">GetReturnValueForILOffset Method</span></span>](icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="3cc5c-109">Získá objekt ICorDebugValue, který zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="3cc5c-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3cc5c-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3cc5c-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cc5c-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="3cc5c-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc5c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3cc5c-112">Requirements</span></span>  
 <span data-ttu-id="3cc5c-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cc5c-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc5c-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3cc5c-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3cc5c-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3cc5c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cc5c-116">**Verze .NET Framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc5c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc5c-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="3cc5c-117">See also</span></span>

- [<span data-ttu-id="3cc5c-118">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cc5c-118">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="3cc5c-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3cc5c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
