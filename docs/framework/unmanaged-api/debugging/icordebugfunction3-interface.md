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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1945e678dd62f81c698807714d0e71053d6b378
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414782"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="ba067-102">Rozhraní ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="ba067-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="ba067-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="ba067-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ba067-104">Logicky rozšiřuje rozhraní ICorDebugFunction k poskytování přístupu ke kódu z ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="ba067-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ba067-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ba067-105">Methods</span></span>  
  
|<span data-ttu-id="ba067-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ba067-106">Method</span></span>|<span data-ttu-id="ba067-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ba067-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba067-108">GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="ba067-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="ba067-109">Získá ukazatele rozhraní k [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) obsahující IL z active ReJIT žádosti.</span><span class="sxs-lookup"><span data-stu-id="ba067-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba067-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ba067-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba067-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba067-111">Requirements</span></span>  
 <span data-ttu-id="ba067-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba067-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba067-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba067-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba067-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba067-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba067-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba067-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba067-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba067-116">See Also</span></span>  
 [<span data-ttu-id="ba067-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="ba067-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="ba067-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="ba067-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="ba067-119">ReJIT: Postupy: Průvodce</span><span class="sxs-lookup"><span data-stu-id="ba067-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
