---
title: ICorDebugMemoryBuffer Interface
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e12b50e964ec470b843ae35c960f20c5675fd572
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59072906"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="d22d3-102">ICorDebugMemoryBuffer Interface</span><span class="sxs-lookup"><span data-stu-id="d22d3-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="d22d3-103">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="d22d3-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d22d3-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d22d3-104">Methods</span></span>  
  
|<span data-ttu-id="d22d3-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d22d3-105">Method</span></span>|<span data-ttu-id="d22d3-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d22d3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d22d3-107">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="d22d3-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="d22d3-108">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d22d3-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="d22d3-109">GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="d22d3-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="d22d3-110">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d22d3-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d22d3-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d22d3-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d22d3-112">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d22d3-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="d22d3-113">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d22d3-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d22d3-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d22d3-114">Requirements</span></span>  
 <span data-ttu-id="d22d3-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d22d3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d22d3-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d22d3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d22d3-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d22d3-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d22d3-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d22d3-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d22d3-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d22d3-119">See also</span></span>

- [<span data-ttu-id="d22d3-120">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d22d3-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d22d3-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="d22d3-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
