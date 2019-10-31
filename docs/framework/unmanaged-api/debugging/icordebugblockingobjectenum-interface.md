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
ms.openlocfilehash: bfd61d985eac3ab56d8a5df9474b2b1a9f641f3e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122848"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="235f4-102">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="235f4-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="235f4-103">Poskytuje enumerátor pro seznam struktur [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="235f4-103">Provides an enumerator for a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="235f4-104">Toto rozhraní je podtřídou rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="235f4-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="235f4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="235f4-105">Methods</span></span>  
  
|<span data-ttu-id="235f4-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="235f4-106">Method</span></span>|<span data-ttu-id="235f4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="235f4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="235f4-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="235f4-108">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="235f4-109">Provede výčet ze seznamu [CorDebugBlockingObject –](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktur.</span><span class="sxs-lookup"><span data-stu-id="235f4-109">Enumerates through a list of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="235f4-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="235f4-110">Remarks</span></span>  
 <span data-ttu-id="235f4-111">Každá struktura `CorDebugBlockingObject` představuje objekt, který blokuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="235f4-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="235f4-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="235f4-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="235f4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="235f4-113">Requirements</span></span>  
 <span data-ttu-id="235f4-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="235f4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="235f4-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="235f4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="235f4-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="235f4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="235f4-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="235f4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="235f4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="235f4-118">See also</span></span>

- [<span data-ttu-id="235f4-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="235f4-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="235f4-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="235f4-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
