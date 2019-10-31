---
title: Rozhraní ICorDebugFunction3
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: fc50fd7180aaf5c1cff2147268d34921eec39e8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137766"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="e5842-102">Rozhraní ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="e5842-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="e5842-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="e5842-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="e5842-104">Logicky rozšiřuje rozhraní ICorDebugFunction a poskytuje přístup k kódu z požadavku ReJIT.</span><span class="sxs-lookup"><span data-stu-id="e5842-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e5842-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e5842-105">Methods</span></span>  
  
|<span data-ttu-id="e5842-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e5842-106">Method</span></span>|<span data-ttu-id="e5842-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e5842-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e5842-108">GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="e5842-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="e5842-109">Získá ukazatel rozhraní na [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) , který obsahuje Il z aktivní žádosti ReJIT.</span><span class="sxs-lookup"><span data-stu-id="e5842-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5842-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e5842-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5842-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5842-111">Requirements</span></span>  
 <span data-ttu-id="e5842-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e5842-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e5842-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e5842-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e5842-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e5842-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e5842-115">**Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e5842-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5842-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5842-116">See also</span></span>

- [<span data-ttu-id="e5842-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e5842-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e5842-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="e5842-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="e5842-119">ReJIT: Průvodce</span><span class="sxs-lookup"><span data-stu-id="e5842-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
