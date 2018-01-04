---
title: ICorDebugBreakpointEnum Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpointEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpointEnum
helpviewer_keywords: ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f09a9d3870e2b975dc9ed952eca33147a21fce6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugbreakpointenum-interface1"></a><span data-ttu-id="19313-102">ICorDebugBreakpointEnum Interface1</span><span class="sxs-lookup"><span data-stu-id="19313-102">ICorDebugBreakpointEnum Interface1</span></span>
<span data-ttu-id="19313-103">Implementuje metody ICorDebugEnum a vytvoří výčet ICorDebugBreakpoint pole.</span><span class="sxs-lookup"><span data-stu-id="19313-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="19313-104">Metody</span><span class="sxs-lookup"><span data-stu-id="19313-104">Methods</span></span>  
  
|<span data-ttu-id="19313-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="19313-105">Method</span></span>|<span data-ttu-id="19313-106">Popis</span><span class="sxs-lookup"><span data-stu-id="19313-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="19313-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="19313-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="19313-108">Získá zadaný počet `ICorDebugBreakpoint` instancí z výčtu, počínaje na aktuální pozici.</span><span class="sxs-lookup"><span data-stu-id="19313-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19313-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19313-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19313-110">Toto rozhraní nepodporuje volané vzdáleně, mezi počítači nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="19313-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19313-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19313-111">Requirements</span></span>  
 <span data-ttu-id="19313-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19313-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19313-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19313-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19313-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19313-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19313-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19313-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19313-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="19313-116">See Also</span></span>  
 [<span data-ttu-id="19313-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="19313-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
