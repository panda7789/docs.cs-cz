---
title: "ICorDebugMemoryBuffer rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98703b07f6601307b5f26aa14b2faf67f8823be5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="bdfcf-102">ICorDebugMemoryBuffer rozhraní</span><span class="sxs-lookup"><span data-stu-id="bdfcf-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="bdfcf-103">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bdfcf-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bdfcf-104">Methods</span></span>  
  
|<span data-ttu-id="bdfcf-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bdfcf-105">Method</span></span>|<span data-ttu-id="bdfcf-106">Popis</span><span class="sxs-lookup"><span data-stu-id="bdfcf-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bdfcf-107">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="bdfcf-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="bdfcf-108">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="bdfcf-109">GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="bdfcf-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="bdfcf-110">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdfcf-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bdfcf-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bdfcf-112">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="bdfcf-113">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bdfcf-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdfcf-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bdfcf-114">Requirements</span></span>  
 <span data-ttu-id="bdfcf-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdfcf-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdfcf-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bdfcf-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdfcf-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdfcf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdfcf-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdfcf-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdfcf-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="bdfcf-119">See Also</span></span>  
 [<span data-ttu-id="bdfcf-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="bdfcf-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bdfcf-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="bdfcf-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
