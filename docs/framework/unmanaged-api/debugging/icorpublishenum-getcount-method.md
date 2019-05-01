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
ms.openlocfilehash: 0424d929f40da1faabd7456cdd85e39a59246d48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986606"
---
# <a name="icorpublishenumgetcount-method"></a><span data-ttu-id="f49a2-102">ICorPublishEnum::GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="f49a2-102">ICorPublishEnum::GetCount Method</span></span>
<span data-ttu-id="f49a2-103">Získá počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="f49a2-103">Gets the number of items in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f49a2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f49a2-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f49a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f49a2-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="f49a2-106">[out] Ukazatel na počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="f49a2-106">[out] A pointer to the number of items in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f49a2-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f49a2-107">Requirements</span></span>  
 <span data-ttu-id="f49a2-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f49a2-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f49a2-109">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f49a2-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f49a2-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f49a2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f49a2-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f49a2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49a2-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f49a2-112">See also</span></span>

- [<span data-ttu-id="f49a2-113">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f49a2-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
