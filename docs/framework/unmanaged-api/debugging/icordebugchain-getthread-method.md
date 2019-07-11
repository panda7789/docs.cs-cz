---
title: ICorDebugChain::GetThread – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d05002ecdb903a1adfeea88930083ba472164324
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745635"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="b6ad1-102">ICorDebugChain::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="b6ad1-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="b6ad1-103">Získá fyzické vlákno, které tento řetěz volání je součástí.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ad1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6ad1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6ad1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6ad1-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="b6ad1-106">[out] Ukazatel na objekt, který představuje fyzické vlákno ICorDebugThread tento řetěz volání je součástí.</span><span class="sxs-lookup"><span data-stu-id="b6ad1-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6ad1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6ad1-107">Requirements</span></span>  
 <span data-ttu-id="b6ad1-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6ad1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6ad1-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6ad1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6ad1-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6ad1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6ad1-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6ad1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
