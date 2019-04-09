---
title: ICorDebugProcessEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugProcessEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcessEnum
helpviewer_keywords:
- ICorDebugProcessEnum interface [.NET Framework debugging]
ms.assetid: b63a507a-ca97-4be0-8e4f-401cce2125f6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3651a4be94fa624d0dd6ab64b8c3f8169945de0d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175315"
---
# <a name="icordebugprocessenum-interface"></a><span data-ttu-id="b0cbe-102">ICorDebugProcessEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0cbe-102">ICorDebugProcessEnum Interface</span></span>
<span data-ttu-id="b0cbe-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugProcess.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-103">Implements ICorDebugEnum methods and enumerates ICorDebugProcess arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0cbe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b0cbe-104">Methods</span></span>  
  
|<span data-ttu-id="b0cbe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0cbe-105">Method</span></span>|<span data-ttu-id="b0cbe-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b0cbe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0cbe-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="b0cbe-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-next-method.md)|<span data-ttu-id="b0cbe-108">Získá zadaný počet `ICorDebugProcess` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-108">Gets the specified number of `ICorDebugProcess` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0cbe-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b0cbe-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0cbe-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="b0cbe-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0cbe-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0cbe-111">Requirements</span></span>  
 <span data-ttu-id="b0cbe-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0cbe-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0cbe-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0cbe-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0cbe-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0cbe-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b0cbe-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b0cbe-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b0cbe-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0cbe-116">See also</span></span>

- [<span data-ttu-id="b0cbe-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b0cbe-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
