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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109821"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="9d067-102">ICorDebugInternalFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d067-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="9d067-103">Představuje modul runtime interní rámec v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9d067-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="9d067-104">Toto rozhraní je podtřídou třídy icordebugframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9d067-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d067-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9d067-105">Methods</span></span>  
  
|<span data-ttu-id="9d067-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9d067-106">Method</span></span>|<span data-ttu-id="9d067-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9d067-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d067-108">GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="9d067-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="9d067-109">Získá typ této vnitřní rámec.</span><span class="sxs-lookup"><span data-stu-id="9d067-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d067-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d067-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d067-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="9d067-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d067-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d067-112">Requirements</span></span>  
 <span data-ttu-id="9d067-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d067-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d067-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d067-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d067-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d067-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="9d067-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9d067-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d067-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d067-117">See also</span></span>

- [<span data-ttu-id="9d067-118">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d067-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
