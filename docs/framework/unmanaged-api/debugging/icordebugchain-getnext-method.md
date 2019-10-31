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
ms.openlocfilehash: 132734dfb6ba9d70836638ab67564fc215e9bc40
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192127"
---
# <a name="icordebugchaingetnext-method"></a><span data-ttu-id="61237-102">ICorDebugChain::GetNext – metoda</span><span class="sxs-lookup"><span data-stu-id="61237-102">ICorDebugChain::GetNext Method</span></span>
<span data-ttu-id="61237-103">Získá další řetězec snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="61237-103">Gets the next chain of frames for the thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="61237-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNext (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61237-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61237-105">Parameters</span></span>  
 `ppChain`  
 <span data-ttu-id="61237-106">mimo Ukazatel na adresu objektu ICorDebugChain, který představuje další řetězec snímků pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="61237-106">[out] A pointer to the address of an ICorDebugChain object that represents the next chain of frames for the thread.</span></span> <span data-ttu-id="61237-107">Pokud je tento řetězec posledním řetězcem, `ppChain` je null.</span><span class="sxs-lookup"><span data-stu-id="61237-107">If this chain is the last chain, `ppChain` is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61237-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61237-108">Requirements</span></span>  
 <span data-ttu-id="61237-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61237-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61237-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="61237-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61237-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="61237-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61237-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61237-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
