---
title: ICorPublishEnum::Skip – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Skip
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Skip
helpviewer_keywords:
- ICorPublishEnum::Skip method [.NET Framework debugging]
- Skip method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 1680ec06-4ab0-447e-93ad-cdb8693fde5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4e7d4e449624f295c4011a4ccdad46226e742a8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681154"
---
# <a name="icorpublishenumskip-method"></a><span data-ttu-id="66369-102">ICorPublishEnum::Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="66369-102">ICorPublishEnum::Skip Method</span></span>
<span data-ttu-id="66369-103">Přesune kurzor vpřed o zadaný počet položek ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="66369-103">Moves the cursor forward in the enumeration by the specified number of items.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66369-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="66369-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="66369-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="66369-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="66369-106">[in] Počet položek, podle kterého se má přesunout kurzor vpřed.</span><span class="sxs-lookup"><span data-stu-id="66369-106">[in] The number of items by which to move the cursor forward.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66369-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="66369-107">Requirements</span></span>  
 <span data-ttu-id="66369-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66369-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66369-109">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="66369-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="66369-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66369-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66369-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66369-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66369-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66369-112">See also</span></span>
- [<span data-ttu-id="66369-113">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="66369-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
