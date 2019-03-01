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
ms.openlocfilehash: 6a1af92cbce84b674058ab2c8af2e15b0070dcd8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974754"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="fe6e9-102">ICorDebugInternalFrame – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fe6e9-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="fe6e9-103">Představuje modul runtime interní rámec v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="fe6e9-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="fe6e9-104">Toto rozhraní je podtřídou třídy icordebugframe – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fe6e9-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fe6e9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fe6e9-105">Methods</span></span>  
  
|<span data-ttu-id="fe6e9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="fe6e9-106">Method</span></span>|<span data-ttu-id="fe6e9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fe6e9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fe6e9-108">GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="fe6e9-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="fe6e9-109">Získá typ této vnitřní rámec.</span><span class="sxs-lookup"><span data-stu-id="fe6e9-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe6e9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe6e9-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fe6e9-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="fe6e9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fe6e9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fe6e9-112">Requirements</span></span>  
 <span data-ttu-id="fe6e9-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fe6e9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fe6e9-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fe6e9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fe6e9-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fe6e9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fe6e9-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fe6e9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe6e9-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe6e9-117">See also</span></span>
- [<span data-ttu-id="fe6e9-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="fe6e9-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
