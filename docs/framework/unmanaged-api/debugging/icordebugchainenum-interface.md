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
ms.openlocfilehash: 2d8a64b7dcaf4758cba217be06fa7d09f6c76920
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989245"
---
# <a name="icordebugchainenum-interface"></a><span data-ttu-id="22e7b-102">ICorDebugChainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22e7b-102">ICorDebugChainEnum Interface</span></span>

<span data-ttu-id="22e7b-103">Implementuje metody ICorDebugEnum a vytváří výčet polí icordebugchain –.</span><span class="sxs-lookup"><span data-stu-id="22e7b-103">Implements ICorDebugEnum methods, and enumerates ICorDebugChain arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="22e7b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="22e7b-104">Methods</span></span>  
  
|<span data-ttu-id="22e7b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="22e7b-105">Method</span></span>|<span data-ttu-id="22e7b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="22e7b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="22e7b-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="22e7b-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-next-method.md)|<span data-ttu-id="22e7b-108">Získá zadaný počet `ICorDebugChain` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="22e7b-108">Gets the specified number of `ICorDebugChain` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="22e7b-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22e7b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22e7b-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="22e7b-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22e7b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22e7b-111">Requirements</span></span>  
 <span data-ttu-id="22e7b-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22e7b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22e7b-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="22e7b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22e7b-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="22e7b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22e7b-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22e7b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22e7b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22e7b-116">See also</span></span>

- [<span data-ttu-id="22e7b-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="22e7b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
