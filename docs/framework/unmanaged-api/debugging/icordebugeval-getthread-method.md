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
ms.openlocfilehash: b985ada09e0e1914c5e60da61a45398fc6098b33
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976275"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="4a35f-102">ICorDebugEval::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="4a35f-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="4a35f-103">Získá vlákno, ve kterém se toto vyhodnocení provádí nebo spustí.</span><span class="sxs-lookup"><span data-stu-id="4a35f-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a35f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4a35f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a35f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a35f-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="4a35f-106">mimo Ukazatel na adresu objektu ICorDebugThread, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="4a35f-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a35f-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4a35f-107">Requirements</span></span>  
 <span data-ttu-id="4a35f-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a35f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a35f-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4a35f-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a35f-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4a35f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a35f-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a35f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
