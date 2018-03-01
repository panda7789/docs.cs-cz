---
title: "ICorDebugModule::IsInMemory – metoda"
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
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 448458874c4de96503261bc0fe34fae160395c49
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="82e2a-102">ICorDebugModule::IsInMemory – metoda</span><span class="sxs-lookup"><span data-stu-id="82e2a-102">ICorDebugModule::IsInMemory Method</span></span>
<span data-ttu-id="82e2a-103">Získá hodnotu, která určuje, zda tento modul existuje pouze v paměti.</span><span class="sxs-lookup"><span data-stu-id="82e2a-103">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="82e2a-104">Syntax</span></span>  
  
```  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="82e2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="82e2a-105">Parameters</span></span>  
 `pInMemory`  
 <span data-ttu-id="82e2a-106">[out] `true` Pokud tento modul pouze v paměti; existuje, jinak hodnota `false`.</span><span class="sxs-lookup"><span data-stu-id="82e2a-106">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82e2a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="82e2a-107">Remarks</span></span>  
 <span data-ttu-id="82e2a-108">Modul CLR (CLR) podporuje načítání modulů z nezpracovaná datových proudů bajtů.</span><span class="sxs-lookup"><span data-stu-id="82e2a-108">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="82e2a-109">Tyto moduly se nazývají *moduly v paměti* a nejsou k dispozici na disku.</span><span class="sxs-lookup"><span data-stu-id="82e2a-109">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e2a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="82e2a-110">Requirements</span></span>  
 <span data-ttu-id="82e2a-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82e2a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82e2a-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82e2a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82e2a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82e2a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82e2a-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82e2a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e2a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="82e2a-115">See Also</span></span>  
    
 
