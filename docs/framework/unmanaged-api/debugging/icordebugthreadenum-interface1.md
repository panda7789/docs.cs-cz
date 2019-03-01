---
title: ICorDebugThreadEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugThreadEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThreadEnum
helpviewer_keywords:
- ICorDebugThreadEnum interface [.NET Framework debugging]
ms.assetid: 796de687-7dd4-4b7b-a10b-8bf22dc7779f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b620357967d5d22148f64a3258fbb8dc52361d86
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56981722"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="d7aa2-102">ICorDebugThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d7aa2-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="d7aa2-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="d7aa2-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7aa2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d7aa2-104">Methods</span></span>  
  
|<span data-ttu-id="d7aa2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d7aa2-105">Method</span></span>|<span data-ttu-id="d7aa2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d7aa2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7aa2-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="d7aa2-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="d7aa2-108">Získá zadaný počet `ICorDebugThread` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="d7aa2-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7aa2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7aa2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7aa2-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="d7aa2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7aa2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7aa2-111">Requirements</span></span>  
 <span data-ttu-id="d7aa2-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7aa2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7aa2-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7aa2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7aa2-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7aa2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7aa2-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7aa2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7aa2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7aa2-116">See also</span></span>
- [<span data-ttu-id="d7aa2-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="d7aa2-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
