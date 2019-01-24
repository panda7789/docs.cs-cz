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
ms.openlocfilehash: 354de38e106ea16eef10bd9a9cebf2b27ca44d25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548125"
---
# <a name="icordebugmanagedcallbackunloadclass-method"></a><span data-ttu-id="785dc-102">ICorDebugManagedCallback::UnloadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="785dc-102">ICorDebugManagedCallback::UnloadClass Method</span></span>
<span data-ttu-id="785dc-103">Upozorní ladicího programu, že třída uvolňován.</span><span class="sxs-lookup"><span data-stu-id="785dc-103">Notifies the debugger that a class is being unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="785dc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="785dc-104">Syntax</span></span>  
  
```  
HRESULT UnloadClass (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugClass      *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="785dc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="785dc-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="785dc-106">[in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující třídu.</span><span class="sxs-lookup"><span data-stu-id="785dc-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the class.</span></span>  
  
 `c`  
 <span data-ttu-id="785dc-107">[in] Ukazatel na objekt ICorDebugClass, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="785dc-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="785dc-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="785dc-108">Remarks</span></span>  
 <span data-ttu-id="785dc-109">Třídy neměly by být odkazovány po tomto volání.</span><span class="sxs-lookup"><span data-stu-id="785dc-109">The class should not be referenced after this call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="785dc-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="785dc-110">Requirements</span></span>  
 <span data-ttu-id="785dc-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="785dc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="785dc-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="785dc-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="785dc-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="785dc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="785dc-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="785dc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="785dc-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="785dc-115">See also</span></span>
- [<span data-ttu-id="785dc-116">LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="785dc-116">LoadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadclass-method.md)
- [<span data-ttu-id="785dc-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="785dc-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
