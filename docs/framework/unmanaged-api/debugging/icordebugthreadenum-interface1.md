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
ms.openlocfilehash: 7edf103e397c6e3e1577b5ed4bc8fc0df264b843
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137992"
---
# <a name="icordebugthreadenum-interface"></a><span data-ttu-id="a9a59-102">ICorDebugThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a9a59-102">ICorDebugThreadEnum Interface</span></span>
<span data-ttu-id="a9a59-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="a9a59-103">Implements ICorDebugEnum methods and enumerates ICorDebugThread arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a9a59-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a9a59-104">Methods</span></span>  
  
|<span data-ttu-id="a9a59-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a9a59-105">Method</span></span>|<span data-ttu-id="a9a59-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a9a59-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a9a59-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a9a59-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-next-method.md)|<span data-ttu-id="a9a59-108">Získá zadaný počet `ICorDebugThread` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="a9a59-108">Gets the specified number of `ICorDebugThread` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a9a59-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a9a59-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9a59-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="a9a59-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9a59-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a9a59-111">Requirements</span></span>  
 <span data-ttu-id="a9a59-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9a59-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9a59-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a9a59-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9a59-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a9a59-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9a59-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9a59-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9a59-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a9a59-116">See also</span></span>

- [<span data-ttu-id="a9a59-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a9a59-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
