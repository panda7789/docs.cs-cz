---
title: ICorPublish::GetProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c625aec5b4937ec232318e62a95a612b0e8a6cd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624402"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="6dd63-102">ICorPublish::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="6dd63-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="6dd63-103">Získá [icorpublishprocess –](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instanci, která představuje proces se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="6dd63-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd63-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6dd63-104">Syntax</span></span>  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6dd63-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6dd63-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="6dd63-106">[in] Identifikátor procesu.</span><span class="sxs-lookup"><span data-stu-id="6dd63-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="6dd63-107">[out] Ukazatel na adresu `ICorPublishProcess` instanci, která představuje proces.</span><span class="sxs-lookup"><span data-stu-id="6dd63-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6dd63-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6dd63-108">Remarks</span></span>  
 <span data-ttu-id="6dd63-109">`GetProcess` selže, pokud proces neexistuje nebo není spravovaný proces, který lze ladit aktuálním uživatelem.</span><span class="sxs-lookup"><span data-stu-id="6dd63-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd63-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6dd63-110">Requirements</span></span>  
 <span data-ttu-id="6dd63-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dd63-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dd63-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="6dd63-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6dd63-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dd63-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dd63-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dd63-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd63-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6dd63-115">See also</span></span>
- [<span data-ttu-id="6dd63-116">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6dd63-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
