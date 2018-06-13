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
ms.openlocfilehash: f22d9d86e2b943a8825e1ec271a401b03f73fb6c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407011"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="a4b20-102">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4b20-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="a4b20-103">Poskytuje enumerátor pro seznam [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="a4b20-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="a4b20-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="a4b20-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4b20-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a4b20-105">Methods</span></span>  
  
|<span data-ttu-id="a4b20-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a4b20-106">Method</span></span>|<span data-ttu-id="a4b20-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a4b20-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4b20-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a4b20-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="a4b20-109">Vytvoří výčet prostřednictvím seznam [cordebugblockingobject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="a4b20-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4b20-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4b20-110">Remarks</span></span>  
 <span data-ttu-id="a4b20-111">Každý `CorDebugBlockingObject` struktura představuje objekt, který je blokování vlákna.</span><span class="sxs-lookup"><span data-stu-id="a4b20-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a4b20-112">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a4b20-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4b20-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4b20-113">Requirements</span></span>  
 <span data-ttu-id="a4b20-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4b20-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4b20-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4b20-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4b20-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4b20-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4b20-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4b20-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4b20-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4b20-118">See Also</span></span>  
 [<span data-ttu-id="a4b20-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a4b20-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="a4b20-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="a4b20-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
