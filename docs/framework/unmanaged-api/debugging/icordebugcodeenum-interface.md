---
title: ICorDebugCodeEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum
helpviewer_keywords:
- ICorDebugCodeEnum interface [.NET Framework debugging]
ms.assetid: b5589171-a4a0-4c00-bbdc-6e0a42233b75
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6f36ce2fbf57c72102550069989c94b5cc19e58c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61749797"
---
# <a name="icordebugcodeenum-interface"></a><span data-ttu-id="91eed-102">ICorDebugCodeEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="91eed-102">ICorDebugCodeEnum Interface</span></span>

<span data-ttu-id="91eed-103">Implementuje metody "ICorDebugEnum" a vytváří výčet polí "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="91eed-103">Implements "ICorDebugEnum" methods, and enumerates "ICorDebugCode" arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="91eed-104">Metody</span><span class="sxs-lookup"><span data-stu-id="91eed-104">Methods</span></span>  
  
|<span data-ttu-id="91eed-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="91eed-105">Method</span></span>|<span data-ttu-id="91eed-106">Popis</span><span class="sxs-lookup"><span data-stu-id="91eed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="91eed-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="91eed-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-next-method.md)|<span data-ttu-id="91eed-108">Získá zadaný počet `ICorDebugCode` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="91eed-108">Gets the specified number of `ICorDebugCode` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="91eed-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="91eed-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="91eed-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="91eed-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91eed-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91eed-111">Requirements</span></span>  
 <span data-ttu-id="91eed-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91eed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91eed-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91eed-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91eed-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91eed-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91eed-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91eed-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91eed-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="91eed-116">See also</span></span>

- [<span data-ttu-id="91eed-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="91eed-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
