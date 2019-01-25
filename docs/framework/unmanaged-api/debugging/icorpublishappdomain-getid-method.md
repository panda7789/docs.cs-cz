---
title: ICorPublishAppDomain::GetID – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishAppDomain.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishAppDomain::GetID
helpviewer_keywords:
- GetID method, ICorPublishAppDomain interface [.NET Framework debugging]
- ICorPublishAppDomain::GetID method [.NET Framework debugging]
ms.assetid: 229437e3-1465-4bd8-8846-9804b2488133
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a18e079f84d8adf2cc6f9bd22b35eb1445eaaf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585013"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="44937-102">ICorPublishAppDomain::GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="44937-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="44937-103">Získá jedinečný identifikátor pro tento [icorpublishappdomain –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="44937-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44937-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44937-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="44937-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44937-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="44937-106">[out] Ukazatel na identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="44937-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="44937-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44937-107">Remarks</span></span>  
 <span data-ttu-id="44937-108">Pouze v rámci nadřazeného procesu je jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="44937-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44937-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="44937-109">Requirements</span></span>  
 <span data-ttu-id="44937-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44937-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44937-111">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="44937-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="44937-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44937-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44937-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44937-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44937-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="44937-114">See also</span></span>
- [<span data-ttu-id="44937-115">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="44937-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
