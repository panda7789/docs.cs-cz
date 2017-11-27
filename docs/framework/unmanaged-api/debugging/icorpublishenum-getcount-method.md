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
ms.openlocfilehash: 7b91c11482a1314bc86b464715dcba68f2a67724
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="ccb22-102">ICorPublishEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="ccb22-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="ccb22-103">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="ccb22-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccb22-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccb22-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccb22-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccb22-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="ccb22-106">[out] Ukazatel na počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="ccb22-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccb22-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccb22-107">Requirements</span></span>  
 <span data-ttu-id="ccb22-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccb22-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccb22-109">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="ccb22-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ccb22-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccb22-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccb22-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccb22-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccb22-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccb22-112">See Also</span></span>  
 [<span data-ttu-id="ccb22-113">ICorPublishEnum – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccb22-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
