---
title: Rozhraní ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6392d1040c9d76944f79dc3a39213ae6c2191bef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415565"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="1144e-102">Rozhraní ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="1144e-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="1144e-103">Logicky rozšiřuje [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) rozhraní k zadání informací o načíst moduly.</span><span class="sxs-lookup"><span data-stu-id="1144e-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="1144e-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="1144e-104">Method</span></span>  
  
|<span data-ttu-id="1144e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1144e-105">Method</span></span>|<span data-ttu-id="1144e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="1144e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1144e-107">GetLoadedModules – metoda</span><span class="sxs-lookup"><span data-stu-id="1144e-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="1144e-108">Získá seznam modulů, které byly načteny dosavadní práce.</span><span class="sxs-lookup"><span data-stu-id="1144e-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1144e-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1144e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1144e-110">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="1144e-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="1144e-111">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="1144e-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1144e-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1144e-112">Requirements</span></span>  
 <span data-ttu-id="1144e-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1144e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1144e-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1144e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1144e-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1144e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1144e-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1144e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1144e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="1144e-117">See Also</span></span>  
 [<span data-ttu-id="1144e-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="1144e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="1144e-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="1144e-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
