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
ms.openlocfilehash: a03b06143c0bd92425c7bfc13af6e374dc629f10
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140486"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="e2144-102">ICorPublishEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="e2144-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="e2144-103">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="e2144-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2144-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2144-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2144-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e2144-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="e2144-106">mimo Ukazatel na počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="e2144-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2144-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2144-107">Requirements</span></span>  
 <span data-ttu-id="e2144-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2144-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2144-109">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="e2144-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="e2144-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e2144-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2144-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2144-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2144-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2144-112">See also</span></span>

- [<span data-ttu-id="e2144-113">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2144-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
