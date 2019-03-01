---
title: ICorDebugAssembly2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2
helpviewer_keywords:
- ICorDebugAssembly2 interface [.NET Framework debugging]
ms.assetid: c0766e29-e573-4f9a-a928-167d1de5aa7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6980b78dc416e03df578756b7a2ee45a48a4fd5a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967136"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="abd0e-102">ICorDebugAssembly2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="abd0e-102">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="abd0e-103">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="abd0e-103">Represents an assembly.</span></span> <span data-ttu-id="abd0e-104">Toto rozhraní je rozšířením icordebugassembly – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="abd0e-104">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="abd0e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="abd0e-105">Methods</span></span>  
  
|<span data-ttu-id="abd0e-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="abd0e-106">Method</span></span>|<span data-ttu-id="abd0e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="abd0e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="abd0e-108">IsFullyTrusted – metoda</span><span class="sxs-lookup"><span data-stu-id="abd0e-108">IsFullyTrusted Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="abd0e-109">Získá hodnotu určující, zda sestavení byla udělena úplná důvěryhodnost systém zabezpečení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="abd0e-109">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="abd0e-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="abd0e-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abd0e-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="abd0e-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abd0e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abd0e-112">Requirements</span></span>  
 <span data-ttu-id="abd0e-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abd0e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abd0e-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abd0e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="abd0e-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abd0e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="abd0e-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abd0e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd0e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abd0e-117">See also</span></span>
- [<span data-ttu-id="abd0e-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="abd0e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
