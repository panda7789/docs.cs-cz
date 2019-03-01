---
title: ICorDebugChainEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum
helpviewer_keywords:
- ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6639335c-48e1-4e74-a4f3-70a6a0f54af1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57a36f1d15ad251781b4d9843086a966fa2d4585
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982125"
---
# <a name="icordebugchainenum-interface"></a><span data-ttu-id="c8bd5-102">ICorDebugChainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c8bd5-102">ICorDebugChainEnum Interface</span></span>

<span data-ttu-id="c8bd5-103">Implementuje metody ICorDebugEnum a vytváří výčet polí icordebugchain –.</span><span class="sxs-lookup"><span data-stu-id="c8bd5-103">Implements ICorDebugEnum methods, and enumerates ICorDebugChain arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c8bd5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c8bd5-104">Methods</span></span>  
  
|<span data-ttu-id="c8bd5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c8bd5-105">Method</span></span>|<span data-ttu-id="c8bd5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c8bd5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c8bd5-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="c8bd5-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-next-method.md)|<span data-ttu-id="c8bd5-108">Získá zadaný počet `ICorDebugChain` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="c8bd5-108">Gets the specified number of `ICorDebugChain` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8bd5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8bd5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c8bd5-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="c8bd5-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8bd5-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8bd5-111">Requirements</span></span>  
 <span data-ttu-id="c8bd5-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8bd5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8bd5-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c8bd5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8bd5-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8bd5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8bd5-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8bd5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8bd5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c8bd5-116">See also</span></span>
- [<span data-ttu-id="c8bd5-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="c8bd5-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
