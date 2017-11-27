---
title: "ICorDebugComObjectValue – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugComObjectValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugComObjectValue
helpviewer_keywords: ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d339d3146a8a9214c3518eac6c31ed5222f9b31
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="73e37-102">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="73e37-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="73e37-103">Poskytuje metody k načtení informací, které jsou přidružené obálka volatelná na za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="73e37-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73e37-104">Metody</span><span class="sxs-lookup"><span data-stu-id="73e37-104">Methods</span></span>  
  
|<span data-ttu-id="73e37-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="73e37-105">Method</span></span>|<span data-ttu-id="73e37-106">Popis</span><span class="sxs-lookup"><span data-stu-id="73e37-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73e37-107">Getcachedinterfacepointers – metoda</span><span class="sxs-lookup"><span data-stu-id="73e37-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="73e37-108">Získá ukazatele nezpracovaná rozhraní v aktuální RCW mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="73e37-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="73e37-109">Getcachedinterfacetypes – metoda</span><span class="sxs-lookup"><span data-stu-id="73e37-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="73e37-110">Poskytuje enumerátor pro typy rozhraní, aby byla použita k nebo použít jako aktuální objekt.</span><span class="sxs-lookup"><span data-stu-id="73e37-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73e37-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73e37-111">Remarks</span></span>  
 <span data-ttu-id="73e37-112">Pokud chcete zkontrolovat, zda instanci rozhraní "ICorDebugValue" představuje RCW, ladicí program volá `QueryInterface` na "ICorDebugValue" s `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="73e37-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73e37-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73e37-113">Requirements</span></span>  
 <span data-ttu-id="73e37-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73e37-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73e37-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73e37-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73e37-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73e37-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73e37-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73e37-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73e37-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="73e37-118">See Also</span></span>  
 [<span data-ttu-id="73e37-119">Ladění v rozhraní</span><span class="sxs-lookup"><span data-stu-id="73e37-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="73e37-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="73e37-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
