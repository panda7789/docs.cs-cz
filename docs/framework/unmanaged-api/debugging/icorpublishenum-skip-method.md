---
title: "ICorPublishEnum::Skip – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.Skip
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6f75681237ff00b61cf584fb99c7ee6bbda6df48
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="e12f1-102">ICorPublishEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="e12f1-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="e12f1-103">Přesune kurzor dál o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="e12f1-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e12f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e12f1-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e12f1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e12f1-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e12f1-106">[v] Počet položek, kterým se mají předat přesunutí kurzoru.</span><span class="sxs-lookup"><span data-stu-id="e12f1-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e12f1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e12f1-107">Requirements</span></span>  
 <span data-ttu-id="e12f1-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e12f1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e12f1-109">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e12f1-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e12f1-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e12f1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e12f1-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e12f1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e12f1-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e12f1-112">See Also</span></span>  
 [<span data-ttu-id="e12f1-113">ICorPublishEnum – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="e12f1-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
