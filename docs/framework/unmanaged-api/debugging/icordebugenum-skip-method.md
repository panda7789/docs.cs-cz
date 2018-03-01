---
title: "ICorDebugEnum::Skip – metoda"
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
- ICorDebugEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Skip
helpviewer_keywords:
- ICorDebugEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: e925d88a-67a5-4f76-88b8-09cedeed0232
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0c2e0065b8dd16e32ed624dd073276e7885c1a52
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugenumskip-method"></a><span data-ttu-id="0a3a4-102">ICorDebugEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="0a3a4-102">ICorDebugEnum::Skip Method</span></span>
<span data-ttu-id="0a3a4-103">Přesune kurzor dál o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="0a3a4-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a3a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a3a4-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0a3a4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0a3a4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0a3a4-106">[v] Počet položek, kterým se mají předat přesunutí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="0a3a4-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a3a4-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a3a4-107">Requirements</span></span>  
 <span data-ttu-id="0a3a4-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0a3a4-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a3a4-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a3a4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a3a4-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a3a4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a3a4-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a3a4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a3a4-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a3a4-112">See Also</span></span>  
 [<span data-ttu-id="0a3a4-113">ICorDebugEnum – rozhraní 1</span><span class="sxs-lookup"><span data-stu-id="0a3a4-113">ICorDebugEnum Interface1</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)
