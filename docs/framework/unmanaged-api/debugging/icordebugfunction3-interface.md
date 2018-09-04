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
ms.openlocfilehash: ff49d64b0b58d301d24e39bc626abf6520c031b9
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514217"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="3385b-102">Rozhraní ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="3385b-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="3385b-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="3385b-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="3385b-104">Logicky rozšiřuje rozhraní ICorDebugFunction pro žádost o ReJIT poskytují přístup ke kódu.</span><span class="sxs-lookup"><span data-stu-id="3385b-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3385b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3385b-105">Methods</span></span>  
  
|<span data-ttu-id="3385b-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3385b-106">Method</span></span>|<span data-ttu-id="3385b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3385b-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3385b-108">GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="3385b-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="3385b-109">Získá ukazatel rozhraní k [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) , který obsahuje IL z aktivního ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="3385b-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3385b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3385b-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3385b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3385b-111">Requirements</span></span>  
 <span data-ttu-id="3385b-112">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3385b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3385b-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3385b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3385b-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3385b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3385b-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3385b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3385b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3385b-116">See Also</span></span>  
 [<span data-ttu-id="3385b-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="3385b-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="3385b-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="3385b-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="3385b-119">ReJIT: Nepředstavuje Průvodce</span><span class="sxs-lookup"><span data-stu-id="3385b-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
