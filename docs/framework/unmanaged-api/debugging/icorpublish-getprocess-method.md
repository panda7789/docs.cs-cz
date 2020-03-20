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
ms.openlocfilehash: 46f047dbec7ff008873540806b76ffe7085086b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178425"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="019ab-102">ICorPublish::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="019ab-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="019ab-103">Získá [instanci ICorPublishProcess,](icorpublishprocess-interface.md) která představuje proces se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="019ab-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="019ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="019ab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="019ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="019ab-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="019ab-106">[v] Identifikátor procesu.</span><span class="sxs-lookup"><span data-stu-id="019ab-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="019ab-107">[out] Ukazatel na adresu `ICorPublishProcess` instance, která představuje proces.</span><span class="sxs-lookup"><span data-stu-id="019ab-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="019ab-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="019ab-108">Remarks</span></span>  
 <span data-ttu-id="019ab-109">`GetProcess`pokud proces neexistuje nebo se nejedná o spravovaný proces, který může být odladěn aktuálním uživatelem.</span><span class="sxs-lookup"><span data-stu-id="019ab-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="019ab-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="019ab-110">Requirements</span></span>  
 <span data-ttu-id="019ab-111">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="019ab-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="019ab-112">**Záhlaví:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="019ab-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="019ab-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="019ab-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="019ab-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="019ab-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="019ab-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="019ab-115">See also</span></span>

- [<span data-ttu-id="019ab-116">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="019ab-116">ICorPublish Interface</span></span>](icorpublish-interface.md)
