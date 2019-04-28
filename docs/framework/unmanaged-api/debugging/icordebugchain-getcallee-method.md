---
title: ICorDebugChain::GetCallee – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed5a7657affde335acf79952d77bbdb7ac42c7a0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645292"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="60f9f-102">ICorDebugChain::GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="60f9f-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="60f9f-103">Získá řetězec, který byl volán tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="60f9f-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60f9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="60f9f-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="60f9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="60f9f-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="60f9f-106">[out] Ukazatel na adresa icordebugchain – objekt, který představuje jen řetězce.</span><span class="sxs-lookup"><span data-stu-id="60f9f-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="60f9f-107">Pokud se tento řetězec aktuálně spouští (to znamená, pokud se tento řetězec není čeká řetěz volané vrátit), `ppChain` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="60f9f-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60f9f-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="60f9f-108">Remarks</span></span>  
 <span data-ttu-id="60f9f-109">Tento řetězec bude čekat volané řetězu vrátit předtím, než ji pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="60f9f-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="60f9f-110">Volané řetězci může být v jiném vlákně, v případě zařazené volání mezi vlákny.</span><span class="sxs-lookup"><span data-stu-id="60f9f-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60f9f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="60f9f-111">Requirements</span></span>  
 <span data-ttu-id="60f9f-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60f9f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60f9f-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60f9f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="60f9f-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60f9f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60f9f-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60f9f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
