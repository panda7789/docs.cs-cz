---
title: ICorDebugBreakpointEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpointEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpointEnum
helpviewer_keywords:
- ICorDebugBreakpointEnum interface [.NET Framework debugging]
ms.assetid: 4c6f4f6e-52cc-402e-881b-7b8526544c90
topic_type:
- apiref
ms.openlocfilehash: e391a02571481d75ce88ae3f3b2b6421705d661c
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894706"
---
# <a name="icordebugbreakpointenum-interface"></a><span data-ttu-id="0aaf6-102">ICorDebugBreakpointEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0aaf6-102">ICorDebugBreakpointEnum Interface</span></span>

<span data-ttu-id="0aaf6-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="0aaf6-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0aaf6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0aaf6-104">Methods</span></span>  
  
|<span data-ttu-id="0aaf6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0aaf6-105">Method</span></span>|<span data-ttu-id="0aaf6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0aaf6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0aaf6-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="0aaf6-107">Next Method</span></span>](icordebugbreakpointenum-next-method.md)|<span data-ttu-id="0aaf6-108">Získá zadaný počet `ICorDebugBreakpoint` instancí z výčtu počínaje aktuální pozicí.</span><span class="sxs-lookup"><span data-stu-id="0aaf6-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0aaf6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0aaf6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0aaf6-110">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="0aaf6-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aaf6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0aaf6-111">Requirements</span></span>  
 <span data-ttu-id="0aaf6-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aaf6-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aaf6-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0aaf6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0aaf6-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0aaf6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0aaf6-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aaf6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aaf6-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="0aaf6-116">See also</span></span>

- [<span data-ttu-id="0aaf6-117">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0aaf6-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
