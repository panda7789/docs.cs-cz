---
title: "ICorDebugChain::GetThread – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetThread
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugChain interface [.NET Framework debugging]
- ICorDebugChain::GetThread method [.NET Framework debugging]
ms.assetid: b3390319-6366-418c-ba80-b552ac4dfc1e
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e8307134bc81041efe2a596131b5d309220a873
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetthread-method"></a><span data-ttu-id="9d6e6-102">ICorDebugChain::GetThread – metoda</span><span class="sxs-lookup"><span data-stu-id="9d6e6-102">ICorDebugChain::GetThread Method</span></span>
<span data-ttu-id="9d6e6-103">Získá fyzické vlákno, které je tento řetězec volání součástí.</span><span class="sxs-lookup"><span data-stu-id="9d6e6-103">Gets the physical thread this call chain is part of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d6e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d6e6-104">Syntax</span></span>  
  
```  
HRESULT GetThread (  
    [out] ICorDebugThread    **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d6e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d6e6-105">Parameters</span></span>  
 `ppThread`  
 <span data-ttu-id="9d6e6-106">[out] Ukazatel na ICorDebugThread objekt, který reprezentuje fyzický vlákno této řetěz volání je součástí.</span><span class="sxs-lookup"><span data-stu-id="9d6e6-106">[out] A pointer to an ICorDebugThread object that represents the physical thread this call chain is part of.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d6e6-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d6e6-107">Requirements</span></span>  
 <span data-ttu-id="9d6e6-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d6e6-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d6e6-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d6e6-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d6e6-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d6e6-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d6e6-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d6e6-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
