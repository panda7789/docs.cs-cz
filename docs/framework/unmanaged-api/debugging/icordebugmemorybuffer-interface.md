---
title: ICorDebugMemoryBuffer Interface
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e12b50e964ec470b843ae35c960f20c5675fd572
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072906"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="a06ba-102">ICorDebugMemoryBuffer Interface</span><span class="sxs-lookup"><span data-stu-id="a06ba-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="a06ba-103">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="a06ba-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a06ba-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a06ba-104">Methods</span></span>  
  
|<span data-ttu-id="a06ba-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a06ba-105">Method</span></span>|<span data-ttu-id="a06ba-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a06ba-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a06ba-107">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="a06ba-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="a06ba-108">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="a06ba-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="a06ba-109">GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="a06ba-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="a06ba-110">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a06ba-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a06ba-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a06ba-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a06ba-112">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="a06ba-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="a06ba-113">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="a06ba-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a06ba-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a06ba-114">Requirements</span></span>  
 <span data-ttu-id="a06ba-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a06ba-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a06ba-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a06ba-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a06ba-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a06ba-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a06ba-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a06ba-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a06ba-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a06ba-119">See also</span></span>

- [<span data-ttu-id="a06ba-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a06ba-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="a06ba-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="a06ba-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
