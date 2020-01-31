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
ms.openlocfilehash: 6cc1ef5f778902efaa53156fbefe334046c82114
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794527"
---
# <a name="icordebugframeenum-interface"></a><span data-ttu-id="436b2-102">ICorDebugFrameEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="436b2-102">ICorDebugFrameEnum Interface</span></span>

<span data-ttu-id="436b2-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugFrame.</span><span class="sxs-lookup"><span data-stu-id="436b2-103">Implements ICorDebugEnum methods, and enumerates ICorDebugFrame arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="436b2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="436b2-104">Methods</span></span>  
  
|<span data-ttu-id="436b2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="436b2-105">Method</span></span>|<span data-ttu-id="436b2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="436b2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="436b2-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="436b2-107">Next Method</span></span>](icordebugframeenum-next-method.md)|<span data-ttu-id="436b2-108">Získá zadaný počet instancí `ICorDebugFrame` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="436b2-108">Gets the specified number of `ICorDebugFrame` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="436b2-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="436b2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="436b2-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="436b2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="436b2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="436b2-111">Requirements</span></span>  
 <span data-ttu-id="436b2-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="436b2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="436b2-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="436b2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="436b2-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="436b2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="436b2-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="436b2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="436b2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="436b2-116">See also</span></span>

- [<span data-ttu-id="436b2-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="436b2-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
