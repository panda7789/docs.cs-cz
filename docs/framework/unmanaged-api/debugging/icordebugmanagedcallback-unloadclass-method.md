---
title: ICorDebugManagedCallback::UnloadClass – metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 020774778b21cf0f6029a666e0022fe83845c4ed
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472444"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="fd23a-102">ICorDebugManagedCallback::UnloadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="fd23a-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="fd23a-103">Upozorní ladicího programu, že třída uvolňován.</span><span class="sxs-lookup"><span data-stu-id="fd23a-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd23a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd23a-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd23a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fd23a-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="fd23a-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující třídu.</span><span class="sxs-lookup"><span data-stu-id="fd23a-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="fd23a-107">[in] Ukazatel na objekt ICorDebugClass, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="fd23a-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd23a-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd23a-108">Remarks</span></span>  
 <span data-ttu-id="fd23a-109">Třídy neměly by být odkazovány po tomto volání.</span><span class="sxs-lookup"><span data-stu-id="fd23a-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd23a-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd23a-110">Requirements</span></span>  
 <span data-ttu-id="fd23a-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd23a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd23a-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fd23a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fd23a-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fd23a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd23a-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd23a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd23a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fd23a-115">See also</span></span>
- [<span data-ttu-id="fd23a-116">LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="fd23a-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="fd23a-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="fd23a-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
