---
title: ICorDebugBreakpointEnum – rozhraní 1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 508cb9b4b2ff13a58f1313b958acd7b043741848
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54642932"
---
# <a name="icordebugbreakpointenum-interface1"></a><span data-ttu-id="dd8f1-102">ICorDebugBreakpointEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="dd8f1-102">ICorDebugBreakpointEnum Interface1</span></span>
<span data-ttu-id="dd8f1-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugBreakpoint.</span><span class="sxs-lookup"><span data-stu-id="dd8f1-103">Implements ICorDebugEnum methods, and enumerates ICorDebugBreakpoint arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd8f1-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dd8f1-104">Methods</span></span>  
  
|<span data-ttu-id="dd8f1-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dd8f1-105">Method</span></span>|<span data-ttu-id="dd8f1-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dd8f1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd8f1-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="dd8f1-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-next-method.md)|<span data-ttu-id="dd8f1-108">Získá zadaný počet `ICorDebugBreakpoint` instancí z výčtu od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="dd8f1-108">Gets the specified number of `ICorDebugBreakpoint` instances from the enumeration, starting at the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd8f1-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd8f1-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd8f1-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="dd8f1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd8f1-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd8f1-111">Requirements</span></span>  
 <span data-ttu-id="dd8f1-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd8f1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd8f1-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd8f1-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd8f1-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd8f1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd8f1-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd8f1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8f1-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd8f1-116">See also</span></span>
- [<span data-ttu-id="dd8f1-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dd8f1-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
