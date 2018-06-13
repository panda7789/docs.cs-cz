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
ms.openlocfilehash: 291c8129a790c235ee6e7f163c49c4e1e726cce5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402709"
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="2b125-102">ICorDebugChain::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="2b125-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="2b125-103">Získá fyzické vlákno, které je tento řetězec volání součástí.</span><span class="sxs-lookup"><span data-stu-id="2b125-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b125-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b125-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b125-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b125-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="2b125-106">[out] Ukazatel na ICorDebugThread objekt, který reprezentuje fyzický vlákno této řetěz volání je součástí.</span><span class="sxs-lookup"><span data-stu-id="2b125-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b125-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b125-107">Requirements</span></span>  
 <span data-ttu-id="2b125-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b125-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b125-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b125-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b125-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b125-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b125-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b125-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
