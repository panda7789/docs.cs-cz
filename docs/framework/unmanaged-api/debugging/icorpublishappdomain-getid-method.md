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
ms.openlocfilehash: 33a72d9aea09f808d42d1a17a7ec5640d20d7c79
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140370"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="041b1-102">ICorPublishAppDomain::GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="041b1-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="041b1-103">Získá jedinečný identifikátor pro tento [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="041b1-103">Gets the unique identifier for this [ICorPublishAppDomain](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="041b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="041b1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="041b1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="041b1-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="041b1-106">mimo Ukazatel na identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="041b1-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="041b1-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="041b1-107">Remarks</span></span>  
 <span data-ttu-id="041b1-108">Identifikátor je jedinečný pouze v oboru obsahujícího proces.</span><span class="sxs-lookup"><span data-stu-id="041b1-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="041b1-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="041b1-109">Requirements</span></span>  
 <span data-ttu-id="041b1-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="041b1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="041b1-111">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="041b1-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="041b1-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="041b1-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="041b1-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="041b1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="041b1-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="041b1-114">See also</span></span>

- [<span data-ttu-id="041b1-115">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="041b1-115">ICorPublishAppDomain Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)
