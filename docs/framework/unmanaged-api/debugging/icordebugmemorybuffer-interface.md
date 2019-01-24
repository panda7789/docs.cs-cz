---
title: ICorDebugMemoryBuffer Interface
ms.date: 03/30/2017
ms.assetid: 85dc2d65-3657-4b93-9f23-9feaa95d37ff
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 019fc3db0f09dc9e5cb22ba3cf012605bf865d6b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574856"
---
# <a name="icordebugmemorybuffer-interface"></a><span data-ttu-id="0e354-102">ICorDebugMemoryBuffer Interface</span><span class="sxs-lookup"><span data-stu-id="0e354-102">ICorDebugMemoryBuffer Interface</span></span>
<span data-ttu-id="0e354-103">Představuje vyrovnávací paměť v paměti.</span><span class="sxs-lookup"><span data-stu-id="0e354-103">Represents an in-memory buffer.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0e354-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0e354-104">Methods</span></span>  
  
|<span data-ttu-id="0e354-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0e354-105">Method</span></span>|<span data-ttu-id="0e354-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0e354-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0e354-107">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="0e354-107">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getsize-method.md)|<span data-ttu-id="0e354-108">Získá velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="0e354-108">Gets the size of the memory buffer in bytes.</span></span>|  
|[<span data-ttu-id="0e354-109">GetStartAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="0e354-109">GetStartAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-getstartaddress-method.md)|<span data-ttu-id="0e354-110">Získá počáteční adresa vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="0e354-110">Gets the starting address of the memory buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e354-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e354-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e354-112">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0e354-112">This interface is available with .NET Native only.</span></span> <span data-ttu-id="0e354-113">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0e354-113">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e354-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0e354-114">Requirements</span></span>  
 <span data-ttu-id="0e354-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e354-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e354-116">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e354-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0e354-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e354-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0e354-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e354-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e354-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0e354-119">See also</span></span>
- [<span data-ttu-id="0e354-120">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="0e354-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="0e354-121">Ladění</span><span class="sxs-lookup"><span data-stu-id="0e354-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
