---
title: "ICorDebugManagedCallback::UnloadClass – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugManagedCallback.UnloadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadClass
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadClass method [.NET Framework debugging]
- UnloadClass method [.NET Framework debugging]
ms.assetid: 66a59b18-ce9a-41f4-b23b-4dd6753d6d36
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: bc3e5b9eeae63e77f2dc8cc35b4bcef575711916
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="fafe1-102">ICorDebugManagedCallback::UnloadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="fafe1-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="fafe1-103">Odpojení třídy upozorní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="fafe1-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fafe1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fafe1-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fafe1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fafe1-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="fafe1-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující třídy.</span><span class="sxs-lookup"><span data-stu-id="fafe1-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="fafe1-107">[v] Ukazatel na ICorDebugClass objekt, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="fafe1-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fafe1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fafe1-108">Remarks</span></span>  
 <span data-ttu-id="fafe1-109">Třída nesmí odkazovat po toto volání.</span><span class="sxs-lookup"><span data-stu-id="fafe1-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fafe1-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fafe1-110">Requirements</span></span>  
 <span data-ttu-id="fafe1-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fafe1-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fafe1-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fafe1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fafe1-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fafe1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fafe1-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fafe1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fafe1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="fafe1-115">See Also</span></span>  
 [<span data-ttu-id="fafe1-116">LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="fafe1-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)  
 [<span data-ttu-id="fafe1-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fafe1-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
