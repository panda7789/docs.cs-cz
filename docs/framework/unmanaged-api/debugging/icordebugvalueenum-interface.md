---
title: ICorDebugValueEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugValueEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueEnum
helpviewer_keywords:
- ICorDebugValueEnum interface [.NET Framework debugging]
ms.assetid: 88989482-a09f-4bd0-9adb-16f47b0291fd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ecbf1afb4443cd7c2b7a69028bc2baa42d1055ce
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975638"
---
# <a name="icordebugvalueenum-interface"></a><span data-ttu-id="52e5a-102">ICorDebugValueEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="52e5a-102">ICorDebugValueEnum Interface</span></span>
<span data-ttu-id="52e5a-103">Implementuje metody "ICorDebugEnum" a vytváří výčet polí "ICorDebugValue".</span><span class="sxs-lookup"><span data-stu-id="52e5a-103">Implements "ICorDebugEnum" methods and enumerates "ICorDebugValue" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="52e5a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="52e5a-104">Methods</span></span>  
  
|<span data-ttu-id="52e5a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="52e5a-105">Method</span></span>|<span data-ttu-id="52e5a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="52e5a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="52e5a-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="52e5a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalueenum-next-method.md)|<span data-ttu-id="52e5a-108">Získá zadaný počet `ICorDebugValue` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="52e5a-108">Gets the specified number of `ICorDebugValue` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="52e5a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="52e5a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="52e5a-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="52e5a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52e5a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52e5a-111">Requirements</span></span>  
 <span data-ttu-id="52e5a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52e5a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52e5a-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52e5a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52e5a-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52e5a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52e5a-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52e5a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52e5a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52e5a-116">See also</span></span>


- [<span data-ttu-id="52e5a-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="52e5a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
