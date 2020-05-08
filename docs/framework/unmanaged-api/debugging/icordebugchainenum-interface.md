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
ms.openlocfilehash: 4556ebbd05e0660da14fb59d806c8feb0b45b9bb
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894220"
---
# <a name="icordebugchainenum-interface"></a><span data-ttu-id="4d987-102">ICorDebugChainEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d987-102">ICorDebugChainEnum Interface</span></span>

<span data-ttu-id="4d987-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugChain.</span><span class="sxs-lookup"><span data-stu-id="4d987-103">Implements ICorDebugEnum methods, and enumerates ICorDebugChain arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d987-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4d987-104">Methods</span></span>  
  
|<span data-ttu-id="4d987-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d987-105">Method</span></span>|<span data-ttu-id="4d987-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4d987-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d987-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="4d987-107">Next Method</span></span>](icordebugchainenum-next-method.md)|<span data-ttu-id="4d987-108">Získá zadaný počet `ICorDebugChain` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="4d987-108">Gets the specified number of `ICorDebugChain` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d987-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d987-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d987-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="4d987-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d987-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d987-111">Requirements</span></span>  
 <span data-ttu-id="4d987-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d987-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d987-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4d987-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d987-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4d987-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d987-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d987-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d987-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d987-116">See also</span></span>

- [<span data-ttu-id="4d987-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4d987-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
