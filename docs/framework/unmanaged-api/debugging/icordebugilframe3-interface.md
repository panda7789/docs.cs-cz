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
ms.openlocfilehash: b3094eb6e3006be49cf17c1ca2a220b8ec58b673
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139063"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="72541-102">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72541-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="72541-103">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="72541-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="72541-104">`ICorDebugILFrame3` je logické rozšíření rozhraní ICorDebugILFrame a ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="72541-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="72541-105">Metody</span><span class="sxs-lookup"><span data-stu-id="72541-105">Methods</span></span>  
  
|<span data-ttu-id="72541-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="72541-106">Method</span></span>|<span data-ttu-id="72541-107">Popis</span><span class="sxs-lookup"><span data-stu-id="72541-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="72541-108">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="72541-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="72541-109">Získá objekt ICorDebugValue, který zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="72541-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72541-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72541-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="72541-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="72541-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72541-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72541-112">Requirements</span></span>  
 <span data-ttu-id="72541-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72541-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72541-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72541-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72541-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="72541-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72541-116">**Verze .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72541-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72541-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="72541-117">See also</span></span>

- [<span data-ttu-id="72541-118">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="72541-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="72541-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="72541-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
