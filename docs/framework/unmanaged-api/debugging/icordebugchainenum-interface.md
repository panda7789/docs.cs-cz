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
ms.openlocfilehash: e41cf2ebf0cc64ee7cf720643ae3229cdfbad1ad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969290"
---
# <a name="icordebugchainenum-interface"></a><span data-ttu-id="f7a5a-102">ICorDebugChainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7a5a-102">ICorDebugChainEnum Interface</span></span>

<span data-ttu-id="f7a5a-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugChain.</span><span class="sxs-lookup"><span data-stu-id="f7a5a-103">Implements ICorDebugEnum methods, and enumerates ICorDebugChain arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f7a5a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f7a5a-104">Methods</span></span>  
  
|<span data-ttu-id="f7a5a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f7a5a-105">Method</span></span>|<span data-ttu-id="f7a5a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="f7a5a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f7a5a-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="f7a5a-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-next-method.md)|<span data-ttu-id="f7a5a-108">Získá zadaný počet `ICorDebugChain` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="f7a5a-108">Gets the specified number of `ICorDebugChain` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7a5a-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7a5a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f7a5a-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="f7a5a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7a5a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7a5a-111">Requirements</span></span>  
 <span data-ttu-id="f7a5a-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7a5a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7a5a-113">**Hlaviček** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f7a5a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7a5a-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7a5a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7a5a-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7a5a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7a5a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7a5a-116">See also</span></span>

- [<span data-ttu-id="f7a5a-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="f7a5a-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
