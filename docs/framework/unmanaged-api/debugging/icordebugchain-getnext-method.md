---
title: ICorDebugChain::GetNext – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetNext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetNext
helpviewer_keywords:
- GetNext method [.NET Framework debugging]
- ICorDebugChain::GetNext method [.NET Framework debugging]
ms.assetid: 8d9744a5-e08b-4ab2-9855-5c22711cc1e6
topic_type:
- apiref
ms.openlocfilehash: 47a90ed63ae217cb150f392ad9196f8d0d5764e3
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894646"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="7acc4-102">ICorDebugChain::GetNext – metoda</span><span class="sxs-lookup"><span data-stu-id="7acc4-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="7acc4-103">Získá další řetězec snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="7acc4-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7acc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7acc4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7acc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7acc4-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="7acc4-106">mimo Ukazatel na adresu objektu ICorDebugChain, který představuje další řetězec snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="7acc4-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="7acc4-107">Pokud je tento řetěz poslední řetěz, `ppChain` má hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="7acc4-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7acc4-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7acc4-108">Requirements</span></span>  
 <span data-ttu-id="7acc4-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7acc4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7acc4-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7acc4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7acc4-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7acc4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7acc4-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7acc4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
