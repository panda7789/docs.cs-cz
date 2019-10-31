---
title: ICorDebugChain::GetPrevious – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetPrevious
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetPrevious
helpviewer_keywords:
- ICorDebugChain::GetPrevious method [.NET Framework debugging]
- GetPrevious method [.NET Framework debugging]
ms.assetid: 58eed4c8-d80c-4c6a-a875-967a90dd926c
topic_type:
- apiref
ms.openlocfilehash: c7598a9d93631ca93187886fd8929ba10726dad7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124726"
---
# <a name="icordebugchaingetprevious-method"></a><span data-ttu-id="66c6a-102">ICorDebugChain::GetPrevious – metoda</span><span class="sxs-lookup"><span data-stu-id="66c6a-102">ICorDebugChain::GetPrevious Method</span></span>
<span data-ttu-id="66c6a-103">Načte předchozí řetězec snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="66c6a-103">Gets the previous chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c6a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66c6a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPrevious (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66c6a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66c6a-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="66c6a-106">mimo Ukazatel na adresu objektu ICorDebugChain, který představuje předchozí řetězec snímků pro toto vlákno.</span><span class="sxs-lookup"><span data-stu-id="66c6a-106">[out] A pointer to the address of an ICorDebugChain object that represents the previous chain of frames for this thread.</span></span> <span data-ttu-id="66c6a-107">Pokud je tento řetěz prvním řetězcem, `ppChain` je null.</span><span class="sxs-lookup"><span data-stu-id="66c6a-107">If this chain is the first chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c6a-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66c6a-108">Requirements</span></span>  
 <span data-ttu-id="66c6a-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66c6a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66c6a-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="66c6a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66c6a-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="66c6a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66c6a-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66c6a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
