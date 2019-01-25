---
title: ICorDebugFrameEnum – rozhraní 1
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
ms.openlocfilehash: 91609d7afde9338d194dce96cdc852e3505f2a84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575525"
---
# <a name="icordebugframeenum-interface1"></a><span data-ttu-id="1e762-102">ICorDebugFrameEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="1e762-102">ICorDebugFrameEnum Interface1</span></span>
<span data-ttu-id="1e762-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="1e762-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1e762-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1e762-104">Methods</span></span>  
  
|<span data-ttu-id="1e762-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1e762-105">Method</span></span>|<span data-ttu-id="1e762-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1e762-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1e762-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="1e762-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="1e762-108">Získá zadaný počet `ICorDebugFrame` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="1e762-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e762-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1e762-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e762-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="1e762-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e762-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1e762-111">Requirements</span></span>  
 <span data-ttu-id="1e762-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e762-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e762-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e762-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e762-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e762-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e762-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e762-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e762-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1e762-116">See also</span></span>
- [<span data-ttu-id="1e762-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1e762-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
