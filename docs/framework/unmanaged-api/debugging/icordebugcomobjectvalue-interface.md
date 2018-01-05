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
ms.workload: dotnet
ms.openlocfilehash: 9adeec14e102ef575f24566980477a285f87ba40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="71268-102">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="71268-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="71268-103">Poskytuje metody k načtení informací, které jsou přidružené obálka volatelná na za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="71268-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71268-104">Metody</span><span class="sxs-lookup"><span data-stu-id="71268-104">Methods</span></span>  
  
|<span data-ttu-id="71268-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="71268-105">Method</span></span>|<span data-ttu-id="71268-106">Popis</span><span class="sxs-lookup"><span data-stu-id="71268-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71268-107">GetCachedInterfacePointers – metoda</span><span class="sxs-lookup"><span data-stu-id="71268-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="71268-108">Získá ukazatele nezpracovaná rozhraní v aktuální RCW mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="71268-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="71268-109">GetCachedInterfaceTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="71268-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="71268-110">Poskytuje enumerátor pro typy rozhraní, aby byla použita k nebo použít jako aktuální objekt.</span><span class="sxs-lookup"><span data-stu-id="71268-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71268-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71268-111">Remarks</span></span>  
 <span data-ttu-id="71268-112">Pokud chcete zkontrolovat, zda instanci rozhraní "ICorDebugValue" představuje RCW, ladicí program volá `QueryInterface` na "ICorDebugValue" s `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="71268-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71268-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="71268-113">Requirements</span></span>  
 <span data-ttu-id="71268-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71268-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71268-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="71268-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71268-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="71268-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71268-117">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71268-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71268-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="71268-118">See Also</span></span>  
 [<span data-ttu-id="71268-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="71268-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="71268-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="71268-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
