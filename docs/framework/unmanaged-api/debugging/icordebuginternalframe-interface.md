---
title: ICorDebugInternalFrame – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f16b4628215bee2410708edeb337b41fbdc0311
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59109821"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="e8552-102">ICorDebugInternalFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8552-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="e8552-103">Představuje modul runtime interní rámec v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e8552-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="e8552-104">Toto rozhraní je podtřídou třídy icordebugframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e8552-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8552-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e8552-105">Methods</span></span>  
  
|<span data-ttu-id="e8552-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e8552-106">Method</span></span>|<span data-ttu-id="e8552-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e8552-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8552-108">GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="e8552-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="e8552-109">Získá typ této vnitřní rámec.</span><span class="sxs-lookup"><span data-stu-id="e8552-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8552-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8552-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e8552-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="e8552-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8552-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8552-112">Requirements</span></span>  
 <span data-ttu-id="e8552-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8552-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8552-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8552-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8552-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8552-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8552-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8552-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8552-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8552-117">See also</span></span>

- [<span data-ttu-id="e8552-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e8552-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
