---
title: ICorDebugEval::GetThread – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
ms.openlocfilehash: 6a7d9465a454175b58bb7b9566d31f3c65420610
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085060"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="f58d1-102">ICorDebugEval::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="f58d1-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="f58d1-103">Získá vlákno, ve kterém se toto vyhodnocení provádí nebo spustí.</span><span class="sxs-lookup"><span data-stu-id="f58d1-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f58d1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f58d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f58d1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f58d1-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="f58d1-106">mimo Ukazatel na adresu objektu ICorDebugThread, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="f58d1-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f58d1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f58d1-107">Requirements</span></span>  
 <span data-ttu-id="f58d1-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f58d1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f58d1-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f58d1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f58d1-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f58d1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f58d1-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f58d1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
