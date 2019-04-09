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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 870de1d3db1e415792437e9763dc13bf8066913f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159637"
---
# <a name="icordebugheapvalue2-interface"></a><span data-ttu-id="3007e-102">ICorDebugHeapValue2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3007e-102">ICorDebugHeapValue2 Interface</span></span>

<span data-ttu-id="3007e-103">Rozšíření ICorDebugHeapValue, která poskytuje podporu pro zpracovává common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="3007e-103">An extension of ICorDebugHeapValue that provides support for common language runtime (CLR) handles.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3007e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3007e-104">Methods</span></span>  
  
|<span data-ttu-id="3007e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3007e-105">Method</span></span>|<span data-ttu-id="3007e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="3007e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3007e-107">CreateHandle – metoda</span><span class="sxs-lookup"><span data-stu-id="3007e-107">CreateHandle Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-createhandle-method.md)|<span data-ttu-id="3007e-108">Vytvoří popisovač zadaného typu pro tuto `ICorDebugHeapValue2` objektu.</span><span class="sxs-lookup"><span data-stu-id="3007e-108">Creates a handle of the specified type for this `ICorDebugHeapValue2` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3007e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3007e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3007e-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="3007e-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3007e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3007e-111">Requirements</span></span>  
 <span data-ttu-id="3007e-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3007e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3007e-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3007e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3007e-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3007e-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3007e-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3007e-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3007e-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3007e-116">See also</span></span>

- [<span data-ttu-id="3007e-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3007e-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
