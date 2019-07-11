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
ms.openlocfilehash: d11693473dc4ed4438bbcad7f95c1b20adc1062b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744968"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="ad68f-102">ICorDebugChain::GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="ad68f-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="ad68f-103">Získá řetězec, který volá tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="ad68f-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad68f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad68f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad68f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad68f-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="ad68f-106">[out] Ukazatel na adresa icordebugchain – objekt, který představuje řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="ad68f-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="ad68f-107">Pokud se tento řetězec byla volána samovolně (jako by tomu bylo-li tento řetězec nebo ladicí program inicializován zásobníku volání), `ppChain` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ad68f-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad68f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad68f-108">Remarks</span></span>  
 <span data-ttu-id="ad68f-109">Volání řetězce může být v jiném vlákně, pokud bylo volání zařazen napříč vlákny.</span><span class="sxs-lookup"><span data-stu-id="ad68f-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad68f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad68f-110">Requirements</span></span>  
 <span data-ttu-id="ad68f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad68f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad68f-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad68f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad68f-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad68f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad68f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad68f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
