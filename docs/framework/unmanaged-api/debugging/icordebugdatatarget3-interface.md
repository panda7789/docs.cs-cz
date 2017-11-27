---
title: "Rozhraní ICorDebugDataTarget3"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a1ab94e792265916e29ed24239e25cb5d57d1313
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="934b0-102">Rozhraní ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="934b0-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="934b0-103">Logicky rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní k zadání informací o načíst moduly.</span><span class="sxs-lookup"><span data-stu-id="934b0-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="934b0-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="934b0-104">Method</span></span>  
  
|<span data-ttu-id="934b0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="934b0-105">Method</span></span>|<span data-ttu-id="934b0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="934b0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="934b0-107">Metoda GetLoadedModules</span><span class="sxs-lookup"><span data-stu-id="934b0-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="934b0-108">Získá seznam modulů, které byly načteny dosavadní práce.</span><span class="sxs-lookup"><span data-stu-id="934b0-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="934b0-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="934b0-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="934b0-110">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="934b0-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="934b0-111">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="934b0-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934b0-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="934b0-112">Requirements</span></span>  
 <span data-ttu-id="934b0-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934b0-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934b0-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="934b0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="934b0-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="934b0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="934b0-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="934b0-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934b0-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="934b0-117">See Also</span></span>  
 [<span data-ttu-id="934b0-118">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="934b0-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="934b0-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="934b0-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
