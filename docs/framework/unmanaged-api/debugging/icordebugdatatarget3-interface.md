---
title: Rozhraní ICorDebugDataTarget3
ms.date: 03/30/2017
ms.assetid: f477af85-994f-4df0-ae78-404ed252bf49
ms.openlocfilehash: 5f91db291396589a916933bdc7c2a2390dd61a5d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136671"
---
# <a name="icordebugdatatarget3-interface"></a><span data-ttu-id="49de6-102">Rozhraní ICorDebugDataTarget3</span><span class="sxs-lookup"><span data-stu-id="49de6-102">ICorDebugDataTarget3 Interface</span></span>
<span data-ttu-id="49de6-103">Logicky rozšiřuje rozhraní [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) , aby poskytovala informace o načtených modulech.</span><span class="sxs-lookup"><span data-stu-id="49de6-103">Logically extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to provide information about loaded modules.</span></span>  
  
## <a name="method"></a><span data-ttu-id="49de6-104">Metoda</span><span class="sxs-lookup"><span data-stu-id="49de6-104">Method</span></span>  
  
|<span data-ttu-id="49de6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="49de6-105">Method</span></span>|<span data-ttu-id="49de6-106">Popis</span><span class="sxs-lookup"><span data-stu-id="49de6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="49de6-107">GetLoadedModules – metoda</span><span class="sxs-lookup"><span data-stu-id="49de6-107">GetLoadedModules Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-getloadedmodules-method.md)|<span data-ttu-id="49de6-108">Načte seznam modulů, které byly doposud načteny.</span><span class="sxs-lookup"><span data-stu-id="49de6-108">Gets a list of the modules that have been loaded so far.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="49de6-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="49de6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49de6-110">Toto rozhraní je dostupné jenom pro .NET Native.</span><span class="sxs-lookup"><span data-stu-id="49de6-110">This interface is available with .NET Native only.</span></span> <span data-ttu-id="49de6-111">Pokud implementujete Toto rozhraní pro ICorDebug scénáře mimo .NET Native, modul CLR (Common Language Runtime) bude toto rozhraní ignorovat.</span><span class="sxs-lookup"><span data-stu-id="49de6-111">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49de6-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="49de6-112">Requirements</span></span>  
 <span data-ttu-id="49de6-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49de6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49de6-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="49de6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49de6-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="49de6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49de6-116">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49de6-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49de6-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49de6-117">See also</span></span>

- [<span data-ttu-id="49de6-118">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="49de6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="49de6-119">Ladění</span><span class="sxs-lookup"><span data-stu-id="49de6-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
