---
title: "Icordebuginternalframe – Interface1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugInternalFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugInternalFrame
helpviewer_keywords: ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e950847764e695f705aeded0e3804db4b872827
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuginternalframe-interface1"></a><span data-ttu-id="9d534-102">Icordebuginternalframe – Interface1</span><span class="sxs-lookup"><span data-stu-id="9d534-102">ICorDebugInternalFrame Interface1</span></span>
<span data-ttu-id="9d534-103">Představuje modul runtime interní rámce v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9d534-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="9d534-104">Toto rozhraní je podtřídou třídy rozhraní ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="9d534-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d534-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9d534-105">Methods</span></span>  
  
|<span data-ttu-id="9d534-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="9d534-106">Method</span></span>|<span data-ttu-id="9d534-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9d534-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d534-108">GetFrameType – metoda</span><span class="sxs-lookup"><span data-stu-id="9d534-108">GetFrameType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="9d534-109">Získá typ této interní rámce.</span><span class="sxs-lookup"><span data-stu-id="9d534-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d534-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d534-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d534-111">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="9d534-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d534-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d534-112">Requirements</span></span>  
 <span data-ttu-id="9d534-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d534-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d534-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d534-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d534-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d534-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d534-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d534-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d534-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d534-117">See Also</span></span>  
 [<span data-ttu-id="9d534-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9d534-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
