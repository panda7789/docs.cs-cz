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
ms.openlocfilehash: 03cb1556ee971124ed4c591f38d9f892fc7df7b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192143"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="c8994-102">ICorDebugChain::GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="c8994-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="c8994-103">Získá aktivní (tj. poslední) rámec v řetězu.</span><span class="sxs-lookup"><span data-stu-id="c8994-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8994-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8994-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8994-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8994-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="c8994-106">mimo Ukazatel na adresu objektu ICorDebugFrame, který představuje aktivní (tj. poslední) rámec v řetězci.</span><span class="sxs-lookup"><span data-stu-id="c8994-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8994-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8994-107">Remarks</span></span>  
 <span data-ttu-id="c8994-108">Pokud není k dispozici žádný spravovaný rámec zásobníku, je `ppFrame` nastavena na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c8994-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="c8994-109">Pokud aktivní rámec není k dispozici, bude volání úspěšné a `ppFrame` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c8994-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="c8994-110">Aktivní rámce nebudou k dispozici pro řetězy iniciované v důsledku CHAIN_ENTER_UNMANAGED a pro některé řetězy iniciované z CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="c8994-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="c8994-111">Podívejte se na výčet CorDebugChainReason –.</span><span class="sxs-lookup"><span data-stu-id="c8994-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8994-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c8994-112">Requirements</span></span>  
 <span data-ttu-id="c8994-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8994-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8994-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c8994-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8994-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c8994-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8994-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8994-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
