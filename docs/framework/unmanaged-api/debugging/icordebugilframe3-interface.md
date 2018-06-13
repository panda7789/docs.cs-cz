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
ms.openlocfilehash: be45022701f72e15e83b7ca28cd110ef58c809b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415594"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="c4017-102">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4017-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="c4017-103">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="c4017-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="c4017-104">`ICorDebugILFrame3` je logické rozšíření ICorDebugILFrame a ICorDebugILFrame2 rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c4017-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c4017-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c4017-105">Methods</span></span>  
  
|<span data-ttu-id="c4017-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="c4017-106">Method</span></span>|<span data-ttu-id="c4017-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c4017-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c4017-108">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="c4017-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="c4017-109">Získá objekt ICorDebugValue, který zapouzdří návratovou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="c4017-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4017-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4017-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c4017-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="c4017-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4017-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4017-112">Requirements</span></span>  
 <span data-ttu-id="c4017-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4017-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4017-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c4017-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c4017-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4017-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4017-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4017-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4017-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4017-117">See Also</span></span>  
 [<span data-ttu-id="c4017-118">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c4017-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="c4017-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c4017-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
