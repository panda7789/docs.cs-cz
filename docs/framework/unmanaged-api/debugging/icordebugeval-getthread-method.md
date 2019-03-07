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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 64cc5b6e7c6fe44080b35dc07f029ad311b88ca7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57489381"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="9dece-102">ICorDebugEval::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="9dece-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="9dece-103">Získá vláken, ve kterém toto testování je provádění nebo se spustí.</span><span class="sxs-lookup"><span data-stu-id="9dece-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dece-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9dece-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dece-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9dece-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="9dece-106">[out] Ukazatel na adresu icordebugthread – objekt, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="9dece-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dece-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9dece-107">Requirements</span></span>  
 <span data-ttu-id="9dece-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dece-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dece-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9dece-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dece-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dece-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dece-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dece-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
