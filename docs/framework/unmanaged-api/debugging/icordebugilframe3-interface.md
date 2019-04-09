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
ms.openlocfilehash: b46c74ec0bfc1fc44bcaca07439c472b0fd8393f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113760"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="5d687-102">ICorDebugILFrame3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d687-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="5d687-103">Poskytuje metodu, která zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="5d687-103">Provides a method that encapsulates the return value of a function.</span></span> `ICorDebugILFrame3` <span data-ttu-id="5d687-104">je logickým rozšířením rozhraní ICorDebugILFrame a ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="5d687-104">is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5d687-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5d687-105">Methods</span></span>  
  
|<span data-ttu-id="5d687-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="5d687-106">Method</span></span>|<span data-ttu-id="5d687-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5d687-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5d687-108">GetReturnValueForILOffset – metoda</span><span class="sxs-lookup"><span data-stu-id="5d687-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="5d687-109">Získá ICorDebugValue objekt, který zapouzdřuje vrácenou hodnotu funkce.</span><span class="sxs-lookup"><span data-stu-id="5d687-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5d687-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5d687-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5d687-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="5d687-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d687-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5d687-112">Requirements</span></span>  
 <span data-ttu-id="5d687-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d687-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d687-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5d687-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5d687-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d687-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="5d687-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="5d687-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5d687-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d687-117">See also</span></span>

- [<span data-ttu-id="5d687-118">ICorDebugCode3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d687-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="5d687-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5d687-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
