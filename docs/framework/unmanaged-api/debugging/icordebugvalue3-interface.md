---
title: "ICorDebugValue3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6a470113dc54876937850294f6d99fc15a2cf98e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="b29db-102">ICorDebugValue3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b29db-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="b29db-103">Rozšiřuje rozhraní "ICorDebugValue" a "Icordebugvalue2 –" poskytovat podporu pro pole, které jsou větší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="b29db-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b29db-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b29db-104">Methods</span></span>  
  
|<span data-ttu-id="b29db-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b29db-105">Method</span></span>|<span data-ttu-id="b29db-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b29db-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b29db-107">GetSize64 – metoda</span><span class="sxs-lookup"><span data-stu-id="b29db-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="b29db-108">Získá velikost v bajtech to `ICorDebugValue3` objektu.</span><span class="sxs-lookup"><span data-stu-id="b29db-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b29db-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b29db-109">Remarks</span></span>  
 <span data-ttu-id="b29db-110">[Icordebugvalue::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) metoda vrátí velikost objektu, který rozsahy od 0 do 2 147 483 647 bajtů.</span><span class="sxs-lookup"><span data-stu-id="b29db-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="b29db-111">V [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], velikost pole může být vyšší než 2 GB.</span><span class="sxs-lookup"><span data-stu-id="b29db-111">In the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="b29db-112">`ICorDebugValue3` Rozhraní umožňuje určit velikost těchto polí.</span><span class="sxs-lookup"><span data-stu-id="b29db-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b29db-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b29db-113">Requirements</span></span>  
 <span data-ttu-id="b29db-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b29db-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b29db-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b29db-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b29db-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b29db-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b29db-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b29db-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b29db-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b29db-118">See Also</span></span>  
    
    
 [<span data-ttu-id="b29db-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b29db-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b29db-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="b29db-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
