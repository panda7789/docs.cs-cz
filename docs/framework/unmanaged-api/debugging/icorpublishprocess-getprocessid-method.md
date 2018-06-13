---
title: ICorPublishProcess::GetProcessID – metoda
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91e1697366bd3ee95fd040ee261d68417a8125e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423605"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="3832a-102">ICorPublishProcess::GetProcessID – metoda</span><span class="sxs-lookup"><span data-stu-id="3832a-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="3832a-103">Získá identifikátor tohoto procesu.</span><span class="sxs-lookup"><span data-stu-id="3832a-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3832a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3832a-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3832a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3832a-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="3832a-106">[out] Ukazatel na identifikátor procesu reprezentována to [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="3832a-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3832a-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3832a-107">Requirements</span></span>  
 <span data-ttu-id="3832a-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3832a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3832a-109">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="3832a-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="3832a-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3832a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3832a-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3832a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3832a-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="3832a-112">See Also</span></span>  
 [<span data-ttu-id="3832a-113">ICorPublishProcess – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3832a-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
