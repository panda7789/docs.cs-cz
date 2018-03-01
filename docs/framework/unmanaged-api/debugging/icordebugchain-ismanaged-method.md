---
title: "ICorDebugChain::IsManaged – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugChain.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::IsManaged
helpviewer_keywords:
- ICorDebugChain::IsManaged method [.NET Framework debugging]
- IsManaged method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 17b389a0-1a4d-4e8a-8613-9bc1769930f9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9e9937222c215d22ef4ef572873385f279e7ba86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchainismanaged-method"></a><span data-ttu-id="f8939-102">ICorDebugChain::IsManaged – metoda</span><span class="sxs-lookup"><span data-stu-id="f8939-102">ICorDebugChain::IsManaged Method</span></span>
<span data-ttu-id="f8939-103">Získá hodnotu, která určuje, zda tento řetězec používá spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f8939-103">Gets a value that indicates whether this chain is running managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8939-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8939-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL               *pManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8939-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8939-105">Parameters</span></span>  
 `pManaged`  
 <span data-ttu-id="f8939-106">[out] `true` Pokud tento řetězec používá spravovaného kódu; jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="f8939-106">[out] `true` if this chain is running managed code; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8939-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f8939-107">Requirements</span></span>  
 <span data-ttu-id="f8939-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8939-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8939-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8939-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8939-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8939-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8939-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8939-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
