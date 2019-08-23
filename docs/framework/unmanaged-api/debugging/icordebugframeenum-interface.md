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
ms.openlocfilehash: b9ea398c32762be31f93002533b15bcf3851b870
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910235"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="a821a-102">ICorDebugFrameEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a821a-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="a821a-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="a821a-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a821a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a821a-104">Methods</span></span>  
  
|<span data-ttu-id="a821a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a821a-105">Method</span></span>|<span data-ttu-id="a821a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a821a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a821a-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="a821a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-next-method.md)|<span data-ttu-id="a821a-108">Získá zadaný počet `ICorDebugFrame` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="a821a-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a821a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a821a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a821a-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="a821a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a821a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a821a-111">Requirements</span></span>  
 <span data-ttu-id="a821a-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a821a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a821a-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a821a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a821a-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a821a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a821a-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a821a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a821a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a821a-116">See also</span></span>

- [<span data-ttu-id="a821a-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a821a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
