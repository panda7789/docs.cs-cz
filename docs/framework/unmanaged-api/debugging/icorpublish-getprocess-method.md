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
ms.openlocfilehash: a9d28243e9907fcc6320b2e09a49312bf35a70b4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121778"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="cfd39-102">ICorPublish::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="cfd39-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="cfd39-103">Získá instanci [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) , která představuje proces se zadaným identifikátorem.</span><span class="sxs-lookup"><span data-stu-id="cfd39-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfd39-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfd39-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfd39-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cfd39-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="cfd39-106">pro Identifikátor procesu</span><span class="sxs-lookup"><span data-stu-id="cfd39-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="cfd39-107">mimo Ukazatel na adresu `ICorPublishProcess` instance, která představuje proces.</span><span class="sxs-lookup"><span data-stu-id="cfd39-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfd39-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cfd39-108">Remarks</span></span>  
 <span data-ttu-id="cfd39-109">`GetProcess` dojde k chybě, pokud proces neexistuje nebo se nejedná o spravovaný proces, který může ladit aktuální uživatel.</span><span class="sxs-lookup"><span data-stu-id="cfd39-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfd39-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfd39-110">Requirements</span></span>  
 <span data-ttu-id="cfd39-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfd39-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfd39-112">**Hlavička:** CorPub. idl, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="cfd39-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="cfd39-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cfd39-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfd39-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfd39-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfd39-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfd39-115">See also</span></span>

- [<span data-ttu-id="cfd39-116">ICorPublish – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cfd39-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
