---
title: ICorDebugChain::GetActiveFrame – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c14b48a29993a65a0a0ab9fcb63bcb1e0d882042
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494064"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="56b06-102">ICorDebugChain::GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="56b06-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="56b06-103">Získá aktivní (to znamená nejnovější) rámce v řetězu.</span><span class="sxs-lookup"><span data-stu-id="56b06-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56b06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56b06-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56b06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56b06-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="56b06-106">[out] Ukazatel na adresu objektu ICorDebugFrame představující aktivní (to znamená nejnovější) rámce v řetězu.</span><span class="sxs-lookup"><span data-stu-id="56b06-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56b06-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="56b06-107">Remarks</span></span>  
 <span data-ttu-id="56b06-108">Pokud je k dispozici žádné spravované zásobníku `ppFrame` je nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="56b06-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="56b06-109">Pokud není k dispozici aktivní rámec, že volání bude úspěšné a `ppFrame` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="56b06-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="56b06-110">Aktivní snímků nebudou k dispozici pro řetězce iniciované z důvodu CHAIN_ENTER_UNMANAGED a pro některé řetězce iniciované z důvodu CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="56b06-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="56b06-111">Zobrazit cordebugchainreason – výčet.</span><span class="sxs-lookup"><span data-stu-id="56b06-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56b06-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56b06-112">Requirements</span></span>  
 <span data-ttu-id="56b06-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56b06-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56b06-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="56b06-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="56b06-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="56b06-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="56b06-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56b06-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
