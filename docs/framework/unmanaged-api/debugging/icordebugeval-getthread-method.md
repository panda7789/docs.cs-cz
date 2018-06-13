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
ms.openlocfilehash: e64bc173717c3121d6c2b101f734ee325a0ced53
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413758"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="b7dcb-102">ICorDebugEval::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="b7dcb-102">ICorDebugEval::GetThread Method</span></span>
<span data-ttu-id="b7dcb-103">Získá vlákno, ve kterém toto testování provádí nebo spustí.</span><span class="sxs-lookup"><span data-stu-id="b7dcb-103">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7dcb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b7dcb-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b7dcb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b7dcb-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="b7dcb-106">[out] Ukazatel na adresu ICorDebugThread objekt, který reprezentuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="b7dcb-106">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7dcb-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b7dcb-107">Requirements</span></span>  
 <span data-ttu-id="b7dcb-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7dcb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7dcb-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7dcb-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7dcb-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7dcb-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7dcb-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7dcb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
