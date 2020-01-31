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
ms.openlocfilehash: 8d6e130981693268ae5c2cd615036b84ca8ed2d8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790702"
---
# <a name="icorpublishappdomaingetid-method"></a><span data-ttu-id="e8c4b-102">ICorPublishAppDomain::GetID – metoda</span><span class="sxs-lookup"><span data-stu-id="e8c4b-102">ICorPublishAppDomain::GetID Method</span></span>
<span data-ttu-id="e8c4b-103">Získá jedinečný identifikátor pro tento [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span><span class="sxs-lookup"><span data-stu-id="e8c4b-103">Gets the unique identifier for this [ICorPublishAppDomain](icorpublishappdomain-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8c4b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8c4b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *puId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8c4b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e8c4b-105">Parameters</span></span>  
 `puId`  
 <span data-ttu-id="e8c4b-106">mimo Ukazatel na identifikátor domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="e8c4b-106">[out] A pointer to the identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8c4b-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8c4b-107">Remarks</span></span>  
 <span data-ttu-id="e8c4b-108">Identifikátor je jedinečný pouze v oboru obsahujícího proces.</span><span class="sxs-lookup"><span data-stu-id="e8c4b-108">The identifier is unique only in the scope of the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8c4b-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e8c4b-109">Requirements</span></span>  
 <span data-ttu-id="e8c4b-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8c4b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8c4b-111">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="e8c4b-111">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e8c4b-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e8c4b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8c4b-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8c4b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c4b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8c4b-114">See also</span></span>

- [<span data-ttu-id="e8c4b-115">ICorPublishAppDomain – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8c4b-115">ICorPublishAppDomain Interface</span></span>](icorpublishappdomain-interface.md)
