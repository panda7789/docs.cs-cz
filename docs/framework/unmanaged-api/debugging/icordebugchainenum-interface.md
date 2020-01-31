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
ms.openlocfilehash: 1f94e2e1f6b376a1998ba4fbcc940147eb16272a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784211"
---
# <a name="icordebugchainenum-interface"></a><span data-ttu-id="de624-102">ICorDebugChainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="de624-102">ICorDebugChainEnum Interface</span></span>

<span data-ttu-id="de624-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugChain.</span><span class="sxs-lookup"><span data-stu-id="de624-103">Implements ICorDebugEnum methods, and enumerates ICorDebugChain arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="de624-104">Metody</span><span class="sxs-lookup"><span data-stu-id="de624-104">Methods</span></span>  
  
|<span data-ttu-id="de624-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="de624-105">Method</span></span>|<span data-ttu-id="de624-106">Popis</span><span class="sxs-lookup"><span data-stu-id="de624-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="de624-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="de624-107">Next Method</span></span>](icordebugchainenum-next-method.md)|<span data-ttu-id="de624-108">Získá zadaný počet instancí `ICorDebugChain` z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="de624-108">Gets the specified number of `ICorDebugChain` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de624-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="de624-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="de624-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="de624-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de624-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="de624-111">Requirements</span></span>  
 <span data-ttu-id="de624-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de624-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de624-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="de624-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de624-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="de624-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de624-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de624-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de624-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de624-116">See also</span></span>

- [<span data-ttu-id="de624-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="de624-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
