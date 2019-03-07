---
title: ICorPublishEnum::GetCount – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::GetCount
helpviewer_keywords:
- GetCount method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::GetCount method [.NET Framework debugging]
ms.assetid: d228f684-2be3-4029-93ae-31fe02213c1f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c353edf9db0a7bc7ec0a25f712527dc3c9d8cc28
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484651"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="c9e7b-102">ICorPublishEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="c9e7b-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="c9e7b-103">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="c9e7b-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9e7b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9e7b-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9e7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9e7b-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="c9e7b-106">[out] Ukazatel na počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="c9e7b-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9e7b-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9e7b-107">Requirements</span></span>  
 <span data-ttu-id="c9e7b-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9e7b-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9e7b-109">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="c9e7b-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="c9e7b-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9e7b-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9e7b-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9e7b-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9e7b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9e7b-112">See also</span></span>
- [<span data-ttu-id="c9e7b-113">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9e7b-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
