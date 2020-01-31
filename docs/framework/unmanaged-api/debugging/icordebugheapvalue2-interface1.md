---
title: ICorDebugHeapValue2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue2
helpviewer_keywords:
- ICorDebugHeapValue2 interface [.NET Framework debugging]
ms.assetid: 87360a52-90b1-4ada-80c0-589a556116d8
topic_type:
- apiref
ms.openlocfilehash: d7126222bd23548ec7013ba234c3f3eebbc8e374
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788635"
---
# <a name="icordebugheapvalue2-interface"></a><span data-ttu-id="abb26-102">ICorDebugHeapValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abb26-102">ICorDebugHeapValue2 Interface</span></span>

<span data-ttu-id="abb26-103">Rozšíření ICorDebugHeapValue, které poskytuje podporu pro obslužné rutiny modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="abb26-103">An extension of ICorDebugHeapValue that provides support for common language runtime (CLR) handles.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="abb26-104">Metody</span><span class="sxs-lookup"><span data-stu-id="abb26-104">Methods</span></span>  
  
|<span data-ttu-id="abb26-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="abb26-105">Method</span></span>|<span data-ttu-id="abb26-106">Popis</span><span class="sxs-lookup"><span data-stu-id="abb26-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="abb26-107">CreateHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="abb26-107">CreateHandle Method</span></span>](icordebugheapvalue2-createhandle-method.md)|<span data-ttu-id="abb26-108">Vytvoří popisovač zadaného typu pro tento objekt `ICorDebugHeapValue2`.</span><span class="sxs-lookup"><span data-stu-id="abb26-108">Creates a handle of the specified type for this `ICorDebugHeapValue2` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abb26-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abb26-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="abb26-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="abb26-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abb26-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abb26-111">Requirements</span></span>  
 <span data-ttu-id="abb26-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abb26-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abb26-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="abb26-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abb26-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="abb26-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abb26-115">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abb26-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb26-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abb26-116">See also</span></span>

- [<span data-ttu-id="abb26-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="abb26-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
