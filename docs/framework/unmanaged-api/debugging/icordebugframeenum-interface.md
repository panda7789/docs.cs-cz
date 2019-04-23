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
ms.openlocfilehash: cd24dfa6771ca450e79b4b932735968ecc51fc90
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59093816"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="7a3cd-102">ICorDebugFrameEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7a3cd-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="7a3cd-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="7a3cd-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7a3cd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7a3cd-104">Methods</span></span>  
  
|<span data-ttu-id="7a3cd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7a3cd-105">Method</span></span>|<span data-ttu-id="7a3cd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7a3cd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7a3cd-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7a3cd-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="7a3cd-108">Získá zadaný počet `ICorDebugFrame` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="7a3cd-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7a3cd-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7a3cd-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7a3cd-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="7a3cd-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a3cd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7a3cd-111">Requirements</span></span>  
 <span data-ttu-id="7a3cd-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a3cd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a3cd-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7a3cd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7a3cd-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a3cd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a3cd-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a3cd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a3cd-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7a3cd-116">See also</span></span>

- [<span data-ttu-id="7a3cd-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7a3cd-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
