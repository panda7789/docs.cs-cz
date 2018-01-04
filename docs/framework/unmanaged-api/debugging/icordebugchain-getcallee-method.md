---
title: "ICorDebugChain::GetCallee – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetCallee
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3b584929d99e641e361de916c402a0d5723e53c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="98a42-102">ICorDebugChain::GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="98a42-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="98a42-103">Získá řetězec, který byl volány tento řetězec.</span><span class="sxs-lookup"><span data-stu-id="98a42-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a42-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98a42-104">Syntax</span></span>  
  
```  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="98a42-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98a42-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="98a42-106">[out] Ukazatel na adresu ICorDebugChain objekt, který reprezentuje řetězu názvem.</span><span class="sxs-lookup"><span data-stu-id="98a42-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="98a42-107">Pokud se tento řetězec je právě prováděných (tj. Pokud tento řetězec nečeká řetěz volané vrátit), `ppChain` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="98a42-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98a42-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98a42-108">Remarks</span></span>  
 <span data-ttu-id="98a42-109">Tento řetězec bude čekat řetězu volané vrátit před obnoví spuštění.</span><span class="sxs-lookup"><span data-stu-id="98a42-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="98a42-110">Řetězu názvem může být na jiné vlákno v případě Kódovaná volání mezi vlákny.</span><span class="sxs-lookup"><span data-stu-id="98a42-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98a42-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98a42-111">Requirements</span></span>  
 <span data-ttu-id="98a42-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98a42-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98a42-113">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98a42-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98a42-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98a42-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98a42-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98a42-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
