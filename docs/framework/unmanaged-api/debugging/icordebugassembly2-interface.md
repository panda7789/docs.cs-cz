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
ms.openlocfilehash: a0482ff451b05ec50c199a75a3c3fabd68c28e21
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133996"
---
# <a name="icordebugassembly2-interface"></a><span data-ttu-id="dd4d0-102">ICorDebugAssembly2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd4d0-102">ICorDebugAssembly2 Interface</span></span>

<span data-ttu-id="dd4d0-103">Představuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="dd4d0-103">Represents an assembly.</span></span> <span data-ttu-id="dd4d0-104">Toto rozhraní je rozšířením rozhraní ICorDebugAssembly.</span><span class="sxs-lookup"><span data-stu-id="dd4d0-104">This interface is an extension of the ICorDebugAssembly interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dd4d0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dd4d0-105">Methods</span></span>  
  
|<span data-ttu-id="dd4d0-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="dd4d0-106">Method</span></span>|<span data-ttu-id="dd4d0-107">Popis</span><span class="sxs-lookup"><span data-stu-id="dd4d0-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dd4d0-108">IsFullyTrusted – metoda</span><span class="sxs-lookup"><span data-stu-id="dd4d0-108">IsFullyTrusted Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-isfullytrusted-method.md)|<span data-ttu-id="dd4d0-109">Získá hodnotu, která označuje, zda bylo sestavení uděleno úplnému vztahu důvěryhodnosti systémem zabezpečení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="dd4d0-109">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd4d0-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd4d0-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dd4d0-111">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="dd4d0-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd4d0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dd4d0-112">Requirements</span></span>  
 <span data-ttu-id="dd4d0-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd4d0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd4d0-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dd4d0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd4d0-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dd4d0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd4d0-116">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd4d0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd4d0-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd4d0-117">See also</span></span>

- [<span data-ttu-id="dd4d0-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="dd4d0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
