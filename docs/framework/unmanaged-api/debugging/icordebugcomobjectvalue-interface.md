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
ms.openlocfilehash: 4ff5c0d470e6eb84eb8b526f5e8f74e5e1a8118a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125491"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="e6b62-102">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e6b62-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="e6b62-103">Poskytuje metody pro načtení informací spojených s vydaným obálkou pro spuštění v modulu runtime (RCW).</span><span class="sxs-lookup"><span data-stu-id="e6b62-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e6b62-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e6b62-104">Methods</span></span>  
  
|<span data-ttu-id="e6b62-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e6b62-105">Method</span></span>|<span data-ttu-id="e6b62-106">Popis</span><span class="sxs-lookup"><span data-stu-id="e6b62-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6b62-107">GetCachedInterfacePointers – metoda</span><span class="sxs-lookup"><span data-stu-id="e6b62-107">GetCachedInterfacePointers Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="e6b62-108">Načte nezpracované ukazatele rozhraní v mezipaměti v aktuální RCW.</span><span class="sxs-lookup"><span data-stu-id="e6b62-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="e6b62-109">GetCachedInterfaceTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="e6b62-109">GetCachedInterfaceTypes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="e6b62-110">Poskytuje enumerátor pro typy rozhraní, pro které byl aktuální objekt použita nebo použit jako.</span><span class="sxs-lookup"><span data-stu-id="e6b62-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6b62-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e6b62-111">Remarks</span></span>  
 <span data-ttu-id="e6b62-112">Chcete-li ověřit, zda instance rozhraní "ICorDebugValue" představuje RCW, ladicí program volá `QueryInterface` v "ICorDebugValue" s `IID_ICorDebugComObjectValue`.</span><span class="sxs-lookup"><span data-stu-id="e6b62-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6b62-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e6b62-113">Requirements</span></span>  
 <span data-ttu-id="e6b62-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6b62-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6b62-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e6b62-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6b62-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e6b62-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e6b62-117">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e6b62-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6b62-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6b62-118">See also</span></span>

- [<span data-ttu-id="e6b62-119">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e6b62-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="e6b62-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="e6b62-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
