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
ms.openlocfilehash: 44a2038af5d6ef46ad7cc661603e99b2f3dd67a9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59215921"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="9a389-102">ICorPublishAppDomain::GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="9a389-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="9a389-103">Získá jedinečný identifikátor pro tento [icorpublishappdomain –](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9a389-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a389-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9a389-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9a389-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9a389-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="9a389-106">[out] Ukazatel na identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="9a389-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a389-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9a389-107">Remarks</span></span>  
 <span data-ttu-id="9a389-108">Pouze v rámci nadřazeného procesu je jedinečný identifikátor.</span><span class="sxs-lookup"><span data-stu-id="9a389-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a389-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9a389-109">Requirements</span></span>  
 <span data-ttu-id="9a389-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a389-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a389-111">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9a389-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9a389-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9a389-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9a389-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a389-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a389-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a389-114">See also</span></span>

- [<span data-ttu-id="9a389-115">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9a389-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
