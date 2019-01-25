---
title: ICorDebugStaticFieldSymbol Interface
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0415e622ebba76d0af7d58fc3b59c4bdb47e0043
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619886"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="37858-102">ICorDebugStaticFieldSymbol Interface</span><span class="sxs-lookup"><span data-stu-id="37858-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="37858-103">Představuje informací symbolů ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="37858-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37858-104">Metody</span><span class="sxs-lookup"><span data-stu-id="37858-104">Methods</span></span>  
  
|<span data-ttu-id="37858-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="37858-105">Method</span></span>|<span data-ttu-id="37858-106">Popis</span><span class="sxs-lookup"><span data-stu-id="37858-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37858-107">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="37858-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="37858-108">Získá adresu statické pole.</span><span class="sxs-lookup"><span data-stu-id="37858-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="37858-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="37858-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="37858-110">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="37858-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="37858-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="37858-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="37858-112">Získá velikost v bajtech statické pole.</span><span class="sxs-lookup"><span data-stu-id="37858-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37858-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="37858-113">Remarks</span></span>  
 <span data-ttu-id="37858-114">`ICorDebugStaticFieldSymbol` Rozhraní se používá k načtení informací symbolů ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="37858-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="37858-115">Toto rozhraní je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="37858-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="37858-116">Pokud se rozhodnete implementovat toto rozhraní ICorDebug scénářích mimo .NET Native, modul common language runtime bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="37858-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37858-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37858-117">Requirements</span></span>  
 <span data-ttu-id="37858-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37858-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37858-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37858-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37858-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37858-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37858-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37858-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37858-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37858-122">See also</span></span>
- [<span data-ttu-id="37858-123">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="37858-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="37858-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="37858-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="37858-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="37858-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
