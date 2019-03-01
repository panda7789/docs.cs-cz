---
title: ICorDebugFrameEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum
helpviewer_keywords:
- ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: ee3f85d3-044e-46b8-945c-93ebfa5d9e91
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb1c5bccf43e107cb976016c277c93b146498e1f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56978199"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="e2db9-102">ICorDebugFrameEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2db9-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="e2db9-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="e2db9-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e2db9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e2db9-104">Methods</span></span>  
  
|<span data-ttu-id="e2db9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2db9-105">Method</span></span>|<span data-ttu-id="e2db9-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e2db9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2db9-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="e2db9-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="e2db9-108">Získá zadaný počet `ICorDebugFrame` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="e2db9-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2db9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2db9-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e2db9-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="e2db9-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2db9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2db9-111">Requirements</span></span>  
 <span data-ttu-id="e2db9-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2db9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2db9-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e2db9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2db9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e2db9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2db9-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2db9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2db9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2db9-116">See also</span></span>
- [<span data-ttu-id="e2db9-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e2db9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
