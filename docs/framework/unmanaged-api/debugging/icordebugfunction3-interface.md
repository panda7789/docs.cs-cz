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
ms.openlocfilehash: 4c29d631f84ce2dd7532e32951e71d6597218ebb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59088857"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="0ebd9-102">Rozhraní ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="0ebd9-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="0ebd9-103">[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="0ebd9-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="0ebd9-104">Logicky rozšiřuje rozhraní ICorDebugFunction pro žádost o ReJIT poskytují přístup ke kódu.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0ebd9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0ebd9-105">Methods</span></span>  
  
|<span data-ttu-id="0ebd9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="0ebd9-106">Method</span></span>|<span data-ttu-id="0ebd9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0ebd9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0ebd9-108">GetActiveReJitRequestILCode – metoda</span><span class="sxs-lookup"><span data-stu-id="0ebd9-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="0ebd9-109">Získá ukazatel rozhraní k [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) , který obsahuje IL z aktivního ReJIT požadavku.</span><span class="sxs-lookup"><span data-stu-id="0ebd9-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ebd9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ebd9-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ebd9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ebd9-111">Requirements</span></span>  
 <span data-ttu-id="0ebd9-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0ebd9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ebd9-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ebd9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ebd9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ebd9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ebd9-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ebd9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ebd9-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ebd9-116">See also</span></span>

- [<span data-ttu-id="0ebd9-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0ebd9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0ebd9-118">Ladění</span><span class="sxs-lookup"><span data-stu-id="0ebd9-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [<span data-ttu-id="0ebd9-119">ReJIT: Nepředstavuje Průvodce</span><span class="sxs-lookup"><span data-stu-id="0ebd9-119">ReJIT: A How-To Guide</span></span>](https://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
