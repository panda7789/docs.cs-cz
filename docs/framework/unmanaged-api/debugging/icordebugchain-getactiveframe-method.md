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
ms.openlocfilehash: 2f67188539d5ad5523c255fbc663e990e1b8245f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894682"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="35330-102">ICorDebugChain::GetActiveFrame – metoda</span><span class="sxs-lookup"><span data-stu-id="35330-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="35330-103">Získá aktivní (tj. poslední) rámec v řetězu.</span><span class="sxs-lookup"><span data-stu-id="35330-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35330-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35330-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35330-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="35330-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="35330-106">mimo Ukazatel na adresu objektu ICorDebugFrame, který představuje aktivní (tj. poslední) rámec v řetězci.</span><span class="sxs-lookup"><span data-stu-id="35330-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35330-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="35330-107">Remarks</span></span>  
 <span data-ttu-id="35330-108">Pokud není k dispozici žádný spravovaný rámec `ppFrame` zásobníku, je nastaven na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="35330-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="35330-109">Pokud aktivní rámec není k dispozici, volání bude úspěšné a `ppFrame` bude mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="35330-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="35330-110">Aktivní rámce nebudou k dispozici pro řetězy iniciované v důsledku CHAIN_ENTER_UNMANAGED a pro některé řetězy iniciované z CHAIN_CLASS_INIT.</span><span class="sxs-lookup"><span data-stu-id="35330-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="35330-111">Podívejte se na výčet CorDebugChainReason –.</span><span class="sxs-lookup"><span data-stu-id="35330-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35330-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="35330-112">Requirements</span></span>  
 <span data-ttu-id="35330-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35330-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35330-114">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="35330-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35330-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="35330-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35330-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35330-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
