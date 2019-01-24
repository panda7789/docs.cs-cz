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
ms.openlocfilehash: 4db005e1de043e60ffe958de732a5280fcccbea7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529944"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="cfd96-102">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfd96-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="cfd96-103">Poskytuje metody pro načtení informací o související s obálka volatelná aplikacemi běhu (RCW).</span><span class="sxs-lookup"><span data-stu-id="cfd96-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="cfd96-104">Metody</span><span class="sxs-lookup"><span data-stu-id="cfd96-104">Methods</span></span>  
  
|<span data-ttu-id="cfd96-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="cfd96-105">Method</span></span>|<span data-ttu-id="cfd96-106">Popis</span><span class="sxs-lookup"><span data-stu-id="cfd96-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="cfd96-107">GetCachedInterfacePointers – metoda</span><span class="sxs-lookup"><span data-stu-id="cfd96-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="cfd96-108">Získá ukazatele raw rozhraní ukládat do mezipaměti na aktuální objekt RCW.</span><span class="sxs-lookup"><span data-stu-id="cfd96-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="cfd96-109">GetCachedInterfaceTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="cfd96-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="cfd96-110">Poskytuje enumerátor pro typy rozhraní, že byla malá a velká použita k nebo použít jako aktuální objekt.</span><span class="sxs-lookup"><span data-stu-id="cfd96-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cfd96-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfd96-111">Remarks</span></span>  
 <span data-ttu-id="cfd96-112">Pokud chcete zkontrolovat, zda instanci rozhraní "ICorDebugValue" představuje obálky RCW, ladicí program volá `QueryInterface` na "ICorDebugValue" s `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="cfd96-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfd96-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfd96-113">Requirements</span></span>  
 <span data-ttu-id="cfd96-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfd96-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfd96-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cfd96-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cfd96-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cfd96-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfd96-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfd96-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd96-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfd96-118">See also</span></span>
- [<span data-ttu-id="cfd96-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="cfd96-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="cfd96-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="cfd96-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
