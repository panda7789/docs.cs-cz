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
ms.openlocfilehash: 80002d064c48a90236a64a3d0a56fab5877cf411
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="4157d-102">ICorDebugMemoryBuffer rozhraní</span><span class="sxs-lookup"><span data-stu-id="4157d-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="4157d-103">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="4157d-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4157d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4157d-104">Methods</span></span>  
  
|<span data-ttu-id="4157d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4157d-105">Method</span></span>|<span data-ttu-id="4157d-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4157d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4157d-107">Getsize – metoda</span><span class="sxs-lookup"><span data-stu-id="4157d-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="4157d-108">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="4157d-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="4157d-109">GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="4157d-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="4157d-110">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4157d-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4157d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4157d-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4157d-112">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="4157d-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="4157d-113">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4157d-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4157d-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4157d-114">Requirements</span></span>  
 <span data-ttu-id="4157d-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4157d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4157d-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4157d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4157d-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4157d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4157d-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4157d-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4157d-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="4157d-119">See Also</span></span>  
 [<span data-ttu-id="4157d-120">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="4157d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4157d-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="4157d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
