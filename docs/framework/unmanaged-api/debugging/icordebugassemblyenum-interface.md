---
title: ICorDebugAssemblyEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAssemblyEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssemblyEnum
helpviewer_keywords:
- ICorDebugAssemblyEnum interface [.NET Framework debugging]
ms.assetid: 891ceb43-5161-421e-a0bf-299962fd7efd
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b259ceb8af61785bc77536d2718bdfbb3683c066
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979889"
---
# <a name="icordebugassemblyenum-interface"></a><span data-ttu-id="7b6fb-102">ICorDebugAssemblyEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b6fb-102">ICorDebugAssemblyEnum Interface</span></span>

<span data-ttu-id="7b6fb-103">Implementuje metody ICorDebugEnum a vytváří výčet polí ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="7b6fb-103">Implements ICorDebugEnum methods and enumerates ICorDebugAssembly arrays.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7b6fb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7b6fb-104">Methods</span></span>  
  
|<span data-ttu-id="7b6fb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7b6fb-105">Method</span></span>|<span data-ttu-id="7b6fb-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7b6fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7b6fb-107">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7b6fb-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-next-method.md)|<span data-ttu-id="7b6fb-108">Získá zadaný počet `ICorDebugAssembly` instancí ve výčtu, od aktuální pozice.</span><span class="sxs-lookup"><span data-stu-id="7b6fb-108">Gets the specified number of `ICorDebugAssembly` instances in the enumeration, starting from the current position.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b6fb-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b6fb-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7b6fb-110">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="7b6fb-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b6fb-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b6fb-111">Requirements</span></span>  
 <span data-ttu-id="7b6fb-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b6fb-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b6fb-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b6fb-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b6fb-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b6fb-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b6fb-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b6fb-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b6fb-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b6fb-116">See also</span></span>
- [<span data-ttu-id="7b6fb-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="7b6fb-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
