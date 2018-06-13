---
title: ICorDebugChain::GetCaller – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCaller
helpviewer_keywords:
- ICorDebugChain::GetCaller method [.NET Framework debugging]
- GetCaller method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: d0b8ab4b-d7d2-4fa0-945f-3d2b87e7e991
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a0b5d702e9718ce6ac537beae67fc190b152b9f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405140"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="19247-102">ICorDebugChain::GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="19247-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="19247-103">Získá řetězec, který volá tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="19247-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19247-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19247-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19247-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19247-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="19247-106">[out] Ukazatel na adresu ICorDebugChain objekt, který reprezentuje řetězu volání.</span><span class="sxs-lookup"><span data-stu-id="19247-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="19247-107">Pokud se tento řetězec samovolně volala (protože by byl tento případ, pokud se tento řetězec nebo ladicího programu inicializovat zásobníku volání), `ppChain` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="19247-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19247-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19247-108">Remarks</span></span>  
 <span data-ttu-id="19247-109">Řetězu volání může být v jiném podprocesu, pokud bylo volání zařazené napříč vlákny.</span><span class="sxs-lookup"><span data-stu-id="19247-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19247-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19247-110">Requirements</span></span>  
 <span data-ttu-id="19247-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19247-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19247-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19247-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19247-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19247-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19247-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19247-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
