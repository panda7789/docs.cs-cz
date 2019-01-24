---
title: ICorDebugThreadEnum – rozhraní 1
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
ms.openlocfilehash: 100dc6c83c7c1d45ddb2ea0396c5115c4d79a7f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560357"
---
# <a name="icordebugthreadenum-interface1"></a><span data-ttu-id="498af-102">ICorDebugThreadEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="498af-102">ICorDebugThreadEnum Interface1</span></span>
<span data-ttu-id="498af-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="498af-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="498af-104">Metody</span><span class="sxs-lookup"><span data-stu-id="498af-104">Methods</span></span>  
  
|<span data-ttu-id="498af-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="498af-105">Method</span></span>|<span data-ttu-id="498af-106">Popis</span><span class="sxs-lookup"><span data-stu-id="498af-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="498af-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="498af-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="498af-108">Získá zadaný počet `ICorDebugThread` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="498af-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="498af-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="498af-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="498af-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="498af-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="498af-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="498af-111">Requirements</span></span>  
 <span data-ttu-id="498af-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="498af-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="498af-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="498af-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="498af-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="498af-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="498af-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="498af-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="498af-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="498af-116">See also</span></span>
- [<span data-ttu-id="498af-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="498af-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
