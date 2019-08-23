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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8d35e0f27968b2649a63b035759a6e72d53b2b94
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928184"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="b61ba-102">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b61ba-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="b61ba-103">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="b61ba-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="b61ba-104">`ICorDebugILFrame3`je logickým rozšířením rozhraní ICorDebugILFrame a ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="b61ba-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b61ba-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b61ba-105">Methods</span></span>  
  
|<span data-ttu-id="b61ba-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b61ba-106">Method</span></span>|<span data-ttu-id="b61ba-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b61ba-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b61ba-108">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="b61ba-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="b61ba-109">Získá objekt ICorDebugValue, který zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="b61ba-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b61ba-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b61ba-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b61ba-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="b61ba-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b61ba-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b61ba-112">Requirements</span></span>  
 <span data-ttu-id="b61ba-113">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b61ba-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b61ba-114">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b61ba-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b61ba-115">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b61ba-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b61ba-116">**Verze .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b61ba-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b61ba-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b61ba-117">See also</span></span>

- [<span data-ttu-id="b61ba-118">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b61ba-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="b61ba-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b61ba-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
