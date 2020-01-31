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
ms.openlocfilehash: be1e1cd0d38ad71de43478af5565bb1ac98a8c0d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778005"
---
# <a name="icordebugblockingobjectenum-interface"></a><span data-ttu-id="4dfef-102">ICorDebugBlockingObjectEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4dfef-102">ICorDebugBlockingObjectEnum Interface</span></span>
<span data-ttu-id="4dfef-103">Poskytuje enumerátor pro seznam struktur [CorDebugBlockingObject –](cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="4dfef-103">Provides an enumerator for a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span> <span data-ttu-id="4dfef-104">Toto rozhraní je podtřídou rozhraní ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="4dfef-104">This interface is a subclass of the ICorDebugEnum interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4dfef-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4dfef-105">Methods</span></span>  
  
|<span data-ttu-id="4dfef-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4dfef-106">Method</span></span>|<span data-ttu-id="4dfef-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4dfef-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4dfef-108">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="4dfef-108">Next Method</span></span>](icordebugblockingobjectenum-next-method.md)|<span data-ttu-id="4dfef-109">Provede výčet ze seznamu [CorDebugBlockingObject –](cordebugblockingobject-structure.md) struktur.</span><span class="sxs-lookup"><span data-stu-id="4dfef-109">Enumerates through a list of [CorDebugBlockingObject](cordebugblockingobject-structure.md) structures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dfef-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4dfef-110">Remarks</span></span>  
 <span data-ttu-id="4dfef-111">Každá struktura `CorDebugBlockingObject` představuje objekt, který blokuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="4dfef-111">Each `CorDebugBlockingObject` structure represents an object that is blocking a thread.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4dfef-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4dfef-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dfef-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4dfef-113">Requirements</span></span>  
 <span data-ttu-id="4dfef-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dfef-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dfef-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4dfef-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dfef-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4dfef-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dfef-117">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dfef-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dfef-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4dfef-118">See also</span></span>

- [<span data-ttu-id="4dfef-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="4dfef-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4dfef-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="4dfef-120">Debugging</span></span>](index.md)
