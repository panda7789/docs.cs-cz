---
title: "ICorPublishEnum::GetCount – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishEnum.GetCount
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 023965489530e70deb7dc9460418ef0d56654081
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="9e5ff-102">ICorPublishEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="9e5ff-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="9e5ff-103">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="9e5ff-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e5ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9e5ff-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9e5ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e5ff-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="9e5ff-106">[out] Ukazatel na počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="9e5ff-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e5ff-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9e5ff-107">Requirements</span></span>  
 <span data-ttu-id="9e5ff-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e5ff-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e5ff-109">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9e5ff-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9e5ff-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9e5ff-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e5ff-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e5ff-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e5ff-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e5ff-112">See Also</span></span>  
 [<span data-ttu-id="9e5ff-113">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9e5ff-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
