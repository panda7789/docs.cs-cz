---
title: "ICorDebugManagedCallback::LoadClass – metoda"
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
- ICorDebugManagedCallback.LoadClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f3e732b418398e9c917085d22507c9304981b06a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="420d4-102">ICorDebugManagedCallback::LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="420d4-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="420d4-103">Načtení třídy upozorní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="420d4-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="420d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="420d4-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="420d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="420d4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="420d4-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, do kterého se načetl třídy.</span><span class="sxs-lookup"><span data-stu-id="420d4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="420d4-107">[v] Ukazatel na ICorDebugClass objekt, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="420d4-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="420d4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="420d4-108">Remarks</span></span>  
 <span data-ttu-id="420d4-109">Tato zpětného volání dojde pouze v případě, že třída načítání je povoleno modul, který obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="420d4-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="420d4-110">Načtení třídy je vždy povolena pro dynamické moduly.</span><span class="sxs-lookup"><span data-stu-id="420d4-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="420d4-111">`LoadClass` Zpětné volání poskytuje příslušnou dobu pro vazbu na nově vygenerované třídy v dynamických modulech zarážky.</span><span class="sxs-lookup"><span data-stu-id="420d4-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="420d4-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="420d4-112">Requirements</span></span>  
 <span data-ttu-id="420d4-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="420d4-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="420d4-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="420d4-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="420d4-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="420d4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="420d4-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="420d4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="420d4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="420d4-117">See Also</span></span>  
 [<span data-ttu-id="420d4-118">UnloadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="420d4-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [<span data-ttu-id="420d4-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="420d4-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
