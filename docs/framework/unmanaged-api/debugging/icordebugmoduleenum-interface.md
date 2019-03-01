---
title: ICorDebugModuleEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum
helpviewer_keywords:
- ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 2fb93cd6-6d47-4fdc-a9a0-047726fd03a1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bf3d72b2439250fd8fbdc1bf1dc9ca28352c9ad
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976834"
---
# <a name="icordebugmoduleenum-interface"></a><span data-ttu-id="75603-102">ICorDebugModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="75603-102">ICorDebugModuleEnum Interface</span></span>

<span data-ttu-id="75603-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugModule.</span><span class="sxs-lookup"><span data-stu-id="75603-103">Implements ICorDebugEnum methods, and enumerates ICorDebugModule arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75603-104">Metody</span><span class="sxs-lookup"><span data-stu-id="75603-104">Methods</span></span>  
  
|<span data-ttu-id="75603-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="75603-105">Method</span></span>|<span data-ttu-id="75603-106">Popis</span><span class="sxs-lookup"><span data-stu-id="75603-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75603-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="75603-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-next-method.md)|<span data-ttu-id="75603-108">Získá zadaný počet `ICorDebugModule` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="75603-108">Gets the specified number of `ICorDebugModule` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="75603-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75603-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75603-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="75603-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="75603-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75603-111">Requirements</span></span>  
 <span data-ttu-id="75603-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75603-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75603-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="75603-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75603-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75603-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75603-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75603-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75603-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75603-116">See also</span></span>
- [<span data-ttu-id="75603-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="75603-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
