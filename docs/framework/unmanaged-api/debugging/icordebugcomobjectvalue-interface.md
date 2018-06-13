---
title: ICorDebugComObjectValue – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugComObjectValue
helpviewer_keywords:
- ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 505a7f6c-d92b-42b4-b539-433f5102ea9b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11afee9c2a84999ccad2cdc12e2a14a4dc17d542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412513"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="643de-102">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="643de-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="643de-103">Poskytuje metody k načtení informací, které jsou přidružené obálka volatelná na za běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="643de-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="643de-104">Metody</span><span class="sxs-lookup"><span data-stu-id="643de-104">Methods</span></span>  
  
|<span data-ttu-id="643de-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="643de-105">Method</span></span>|<span data-ttu-id="643de-106">Popis</span><span class="sxs-lookup"><span data-stu-id="643de-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="643de-107">GetCachedInterfacePointers – metoda</span><span class="sxs-lookup"><span data-stu-id="643de-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="643de-108">Získá ukazatele nezpracovaná rozhraní v aktuální RCW mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="643de-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="643de-109">GetCachedInterfaceTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="643de-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="643de-110">Poskytuje enumerátor pro typy rozhraní, aby byla použita k nebo použít jako aktuální objekt.</span><span class="sxs-lookup"><span data-stu-id="643de-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="643de-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="643de-111">Remarks</span></span>  
 <span data-ttu-id="643de-112">Pokud chcete zkontrolovat, zda instanci rozhraní "ICorDebugValue" představuje RCW, ladicí program volá `QueryInterface` na "ICorDebugValue" s `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="643de-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="643de-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="643de-113">Requirements</span></span>  
 <span data-ttu-id="643de-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="643de-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="643de-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="643de-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="643de-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="643de-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="643de-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="643de-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="643de-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="643de-118">See Also</span></span>  
 [<span data-ttu-id="643de-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="643de-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="643de-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="643de-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
