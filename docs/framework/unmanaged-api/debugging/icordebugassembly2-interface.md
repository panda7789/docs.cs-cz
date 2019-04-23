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
ms.openlocfilehash: 70eac63855f16205c3d5dbcb28305481b986484c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201166"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="374fb-102">ICorDebugAssembly2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="374fb-102">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="374fb-103">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="374fb-103">Represents an assembly.</span></span> <span data-ttu-id="374fb-104">Toto rozhraní je rozšířením icordebugassembly – rozhraní.</span><span class="sxs-lookup"><span data-stu-id="374fb-104">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="374fb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="374fb-105">Methods</span></span>  
  
|<span data-ttu-id="374fb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="374fb-106">Method</span></span>|<span data-ttu-id="374fb-107">Popis</span><span class="sxs-lookup"><span data-stu-id="374fb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="374fb-108">IsFullyTrusted – metoda</span><span class="sxs-lookup"><span data-stu-id="374fb-108">IsFullyTrusted Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="374fb-109">Získá hodnotu určující, zda sestavení byla udělena úplná důvěryhodnost systém zabezpečení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="374fb-109">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="374fb-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="374fb-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="374fb-111">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="374fb-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="374fb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="374fb-112">Requirements</span></span>  
 <span data-ttu-id="374fb-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="374fb-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="374fb-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="374fb-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="374fb-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="374fb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="374fb-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="374fb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="374fb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="374fb-117">See also</span></span>

- [<span data-ttu-id="374fb-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="374fb-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
