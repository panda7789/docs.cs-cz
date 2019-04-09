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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105128"
---
# <a name="icorpublishenumclone-method"></a><span data-ttu-id="f4604-102">ICorPublishEnum::Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="f4604-102">ICorPublishEnum::Clone Method</span></span>
<span data-ttu-id="f4604-103">Vytvoří kopii tohoto [icorpublishenum –](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="f4604-103">Creates a copy of this [ICorPublishEnum](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4604-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4604-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorPublishEnum   **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f4604-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f4604-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="f4604-106">[out] Ukazatel na adresu `ICorPublishEnum` objekt, který je kopií této `ICorPublishEnum` objektu.</span><span class="sxs-lookup"><span data-stu-id="f4604-106">[out] A pointer to the address of an `ICorPublishEnum` object that is a copy of this `ICorPublishEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4604-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4604-107">Requirements</span></span>  
 <span data-ttu-id="f4604-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4604-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4604-109">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f4604-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f4604-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f4604-110">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f4604-111">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f4604-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f4604-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4604-112">See also</span></span>

- [<span data-ttu-id="f4604-113">ICorPublishEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4604-113">ICorPublishEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)
