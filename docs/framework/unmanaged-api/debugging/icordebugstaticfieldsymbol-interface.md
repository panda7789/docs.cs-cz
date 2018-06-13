---
title: ICorDebugStaticFieldSymbol rozhraní
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cde5f60764772ece8528eb67a82836c0ae9e651b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422455"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="228c0-102">ICorDebugStaticFieldSymbol rozhraní</span><span class="sxs-lookup"><span data-stu-id="228c0-102">ICorDebugStaticFieldSymbol Interface</span></span>
<span data-ttu-id="228c0-103">Představuje informace o ladění symbol pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="228c0-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="228c0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="228c0-104">Methods</span></span>  
  
|<span data-ttu-id="228c0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="228c0-105">Method</span></span>|<span data-ttu-id="228c0-106">Popis</span><span class="sxs-lookup"><span data-stu-id="228c0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="228c0-107">GetAddress – metoda</span><span class="sxs-lookup"><span data-stu-id="228c0-107">GetAddress Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="228c0-108">Získá adresu statického pole.</span><span class="sxs-lookup"><span data-stu-id="228c0-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="228c0-109">GetName – metoda</span><span class="sxs-lookup"><span data-stu-id="228c0-109">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="228c0-110">Získá název statického pole.</span><span class="sxs-lookup"><span data-stu-id="228c0-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="228c0-111">GetSize – metoda</span><span class="sxs-lookup"><span data-stu-id="228c0-111">GetSize Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="228c0-112">Získá velikost v bajtech statického pole.</span><span class="sxs-lookup"><span data-stu-id="228c0-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="228c0-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="228c0-113">Remarks</span></span>  
 <span data-ttu-id="228c0-114">`ICorDebugStaticFieldSymbol` Rozhraní se používá k načtení informací o symbolu ladění pro statické pole.</span><span class="sxs-lookup"><span data-stu-id="228c0-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="228c0-115">Toto rozhraní je k dispozici s .NET Native jenom.</span><span class="sxs-lookup"><span data-stu-id="228c0-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="228c0-116">Pokud budete implementovat toto rozhraní pro scénáře ICorDebug mimo .NET Native, modul CLR bude ignorovat toto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="228c0-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="228c0-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="228c0-117">Requirements</span></span>  
 <span data-ttu-id="228c0-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="228c0-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="228c0-119">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="228c0-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="228c0-120">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="228c0-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="228c0-121">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="228c0-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="228c0-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="228c0-122">See Also</span></span>  
 [<span data-ttu-id="228c0-123">ICorDebugInstanceFieldSymbol – rozhraní</span><span class="sxs-lookup"><span data-stu-id="228c0-123">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 [<span data-ttu-id="228c0-124">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="228c0-124">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="228c0-125">Ladění</span><span class="sxs-lookup"><span data-stu-id="228c0-125">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
