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
ms.openlocfilehash: 528db447df4d71d67441b05ad29e6a900c59afbb
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892826"
---
# <a name="icordebugcomobjectvalue-interface"></a><span data-ttu-id="5044a-102">ICorDebugComObjectValue – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5044a-102">ICorDebugComObjectValue Interface</span></span>
<span data-ttu-id="5044a-103">Poskytuje metody pro načtení informací spojených s vydaným obálkou pro spuštění v modulu runtime (RCW).</span><span class="sxs-lookup"><span data-stu-id="5044a-103">Provides methods to retrieve information associated with a runtime callable wrapper (RCW).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5044a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5044a-104">Methods</span></span>  
  
|<span data-ttu-id="5044a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5044a-105">Method</span></span>|<span data-ttu-id="5044a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="5044a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5044a-107">GetCachedInterfacePointers – metoda</span><span class="sxs-lookup"><span data-stu-id="5044a-107">GetCachedInterfacePointers Method</span></span>](icordebugcomobjectvalue-getcachedinterfacepointers-method.md)|<span data-ttu-id="5044a-108">Načte nezpracované ukazatele rozhraní v mezipaměti v aktuální RCW.</span><span class="sxs-lookup"><span data-stu-id="5044a-108">Gets the raw interface pointers cached on the current RCW.</span></span>|  
|[<span data-ttu-id="5044a-109">GetCachedInterfaceTypes – metoda</span><span class="sxs-lookup"><span data-stu-id="5044a-109">GetCachedInterfaceTypes Method</span></span>](icordebugcomobjectvalue-getcachedinterfacetypes-method.md)|<span data-ttu-id="5044a-110">Poskytuje enumerátor pro typy rozhraní, pro které byl aktuální objekt použita nebo použit jako.</span><span class="sxs-lookup"><span data-stu-id="5044a-110">Provides an enumerator for the interface types that the current object has been cased to or used as.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5044a-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5044a-111">Remarks</span></span>  
 <span data-ttu-id="5044a-112">Chcete-li ověřit, zda instance rozhraní "ICorDebugValue" představuje RCW, ladicí program volá `QueryInterface` "ICorDebugValue" s. `IID_ICorDebugComObjectValue`</span><span class="sxs-lookup"><span data-stu-id="5044a-112">To check whether an instance of an "ICorDebugValue" interface represents an RCW, a debugger calls `QueryInterface` on "ICorDebugValue" with `IID_ICorDebugComObjectValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5044a-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5044a-113">Requirements</span></span>  
 <span data-ttu-id="5044a-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5044a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5044a-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5044a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5044a-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5044a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5044a-117">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5044a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5044a-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5044a-118">See also</span></span>

- [<span data-ttu-id="5044a-119">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5044a-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5044a-120">Ladění</span><span class="sxs-lookup"><span data-stu-id="5044a-120">Debugging</span></span>](index.md)
