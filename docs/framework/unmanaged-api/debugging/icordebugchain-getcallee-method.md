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
ms.openlocfilehash: ba9a4e32216fd6fad285397bfc48fbc54f602b88
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894653"
---
# <a name="icordebugchaingetcallee-method"></a><span data-ttu-id="36d9b-102">ICorDebugChain::GetCallee – metoda</span><span class="sxs-lookup"><span data-stu-id="36d9b-102">ICorDebugChain::GetCallee Method</span></span>
<span data-ttu-id="36d9b-103">Získá řetězec, který byl volán tímto řetězem.</span><span class="sxs-lookup"><span data-stu-id="36d9b-103">Gets the chain that was called by this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36d9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36d9b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36d9b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="36d9b-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="36d9b-106">mimo Ukazatel na adresu objektu ICorDebugChain, který představuje pojmenovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="36d9b-106">[out] A pointer to the address of an ICorDebugChain object that represents the called chain.</span></span> <span data-ttu-id="36d9b-107">Pokud tento řetěz aktuálně probíhá (tj. Pokud tento řetěz nečeká na návrat z volaného řetězce), `ppChain` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="36d9b-107">If this chain is currently executing (that is, if this chain is not waiting for a called chain to return), `ppChain` will be null.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36d9b-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36d9b-108">Remarks</span></span>  
 <span data-ttu-id="36d9b-109">Tento řetěz počká, než se volaný řetězec vrátí, než obnoví provádění.</span><span class="sxs-lookup"><span data-stu-id="36d9b-109">This chain will wait for the called chain to return before it resumes execution.</span></span> <span data-ttu-id="36d9b-110">Volaný řetěz může být v jiném vlákně v případě volání mezi vlákny zařazování.</span><span class="sxs-lookup"><span data-stu-id="36d9b-110">The called chain may be on another thread in the case of cross-thread marshaled calls.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36d9b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="36d9b-111">Requirements</span></span>  
 <span data-ttu-id="36d9b-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36d9b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36d9b-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="36d9b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36d9b-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="36d9b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36d9b-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36d9b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
