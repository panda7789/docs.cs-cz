---
title: ICorDebugBlockingObjectEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum
helpviewer_keywords:
- ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
ms.assetid: 208e5c2d-3f3f-404e-8b3c-7cccc14ddb16
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a23d21d0ed8c6a6a226d5e58eafb7bde65a4896
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59161450"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="ddb0b-102">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddb0b-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="ddb0b-103">Poskytuje enumerátor pro seznam [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="ddb0b-104">Toto rozhraní je podtřídou třídy icordebugenum – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ddb0b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ddb0b-105">Methods</span></span>  
  
|<span data-ttu-id="ddb0b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ddb0b-106">Method</span></span>|<span data-ttu-id="ddb0b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ddb0b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ddb0b-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="ddb0b-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="ddb0b-109">Vytvoří výčet prostřednictvím seznamu [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ddb0b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ddb0b-110">Remarks</span></span>  
 <span data-ttu-id="ddb0b-111">Každý `CorDebugBlockingObject` struktura představuje objekt, který blokuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddb0b-112">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="ddb0b-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ddb0b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ddb0b-113">Requirements</span></span>  
 <span data-ttu-id="ddb0b-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ddb0b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ddb0b-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ddb0b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ddb0b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ddb0b-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ddb0b-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ddb0b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ddb0b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ddb0b-118">See also</span></span>

- [<span data-ttu-id="ddb0b-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ddb0b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="ddb0b-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="ddb0b-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
