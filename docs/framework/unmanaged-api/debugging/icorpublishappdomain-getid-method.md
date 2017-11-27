---
title: "ICorPublishAppDomain::GetID – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishAppDomain.GetID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bfbde806f409f2639b2468e0ba962b1659d1ffc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="e70d4-102">ICorPublishAppDomain::GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="e70d4-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="e70d4-103">Získá jedinečný identifikátor pro tento [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e70d4-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e70d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e70d4-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e70d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e70d4-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="e70d4-106">[out] Ukazatel na identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e70d4-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e70d4-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e70d4-107">Remarks</span></span>  
 <span data-ttu-id="e70d4-108">Pouze v oboru obsahujícího procesu je jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="e70d4-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e70d4-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e70d4-109">Requirements</span></span>  
 <span data-ttu-id="e70d4-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e70d4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e70d4-111">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="e70d4-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e70d4-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e70d4-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e70d4-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e70d4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e70d4-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="e70d4-114">See Also</span></span>  
 [<span data-ttu-id="e70d4-115">ICorPublishAppDomain – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="e70d4-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
