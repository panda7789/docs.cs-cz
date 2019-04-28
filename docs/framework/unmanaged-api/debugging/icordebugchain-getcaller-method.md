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
ms.openlocfilehash: fd65de77209f5a981c0a4c291f8573a61cf6335b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645276"
---
# <a name="icordebugchaingetcaller-method"></a><span data-ttu-id="110f1-102">ICorDebugChain::GetCaller – metoda</span><span class="sxs-lookup"><span data-stu-id="110f1-102">ICorDebugChain::GetCaller Method</span></span>
<span data-ttu-id="110f1-103">Získá řetězec, který volá tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="110f1-103">Gets the chain that called this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="110f1-104">Syntax</span></span>  
  
```  
HRESULT GetCaller (  
    [out] ICorDebugChain      **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="110f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="110f1-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="110f1-106">[out] Ukazatel na adresa icordebugchain – objekt, který představuje řetěz volání.</span><span class="sxs-lookup"><span data-stu-id="110f1-106">[out] A pointer to the address of an ICorDebugChain object that represents the calling chain.</span></span>  
  
 <span data-ttu-id="110f1-107">Pokud se tento řetězec byla volána samovolně (jako by tomu bylo-li tento řetězec nebo ladicí program inicializován zásobníku volání), `ppChain` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="110f1-107">If this chain was spontaneously called (as would be the case if this chain or the debugger initialized the call stack), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="110f1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="110f1-108">Remarks</span></span>  
 <span data-ttu-id="110f1-109">Volání řetězce může být v jiném vlákně, pokud bylo volání zařazen napříč vlákny.</span><span class="sxs-lookup"><span data-stu-id="110f1-109">The calling chain may be on a different thread, if the call was marshaled across threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="110f1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="110f1-110">Requirements</span></span>  
 <span data-ttu-id="110f1-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="110f1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="110f1-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="110f1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="110f1-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="110f1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="110f1-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="110f1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
