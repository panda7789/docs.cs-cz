---
title: ICorPublishEnum::Clone – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishEnum::Clone
helpviewer_keywords:
- Clone method, ICorPublishEnum interface [.NET Framework debugging]
- ICorPublishEnum::Clone method [.NET Framework debugging]
ms.assetid: c9a26ea3-b8eb-4b8e-854f-9a2ca26b3b39
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e0ce1d8c0074f62d35e16465b368269e233a713b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993522"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="f7d4d-102">ICorPublishEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="f7d4d-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="f7d4d-103">Vytvoří kopii tohoto [icorpublishenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="f7d4d-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d4d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7d4d-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f7d4d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f7d4d-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="f7d4d-106">[out] Ukazatel na adresu `ICorPublishEnum` objekt, který je kopií této `ICorPublishEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="f7d4d-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f7d4d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f7d4d-107">Requirements</span></span>  
 <span data-ttu-id="f7d4d-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7d4d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7d4d-109">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f7d4d-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f7d4d-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7d4d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7d4d-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7d4d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7d4d-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7d4d-112">See also</span></span>

- [<span data-ttu-id="f7d4d-113">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f7d4d-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
