---
title: "ICorDebugManagedCallback::LoadClass – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.LoadClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::LoadClass
helpviewer_keywords:
- ICorDebugManagedCallback::LoadClass method [.NET Framework debugging]
- LoadClass method [.NET Framework debugging]
ms.assetid: e58dac7b-85c3-41ca-b9aa-3a7fc9ae6680
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3518a20567cdac8ed6587aa3dc06408ae6bf7b06
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmanagedcallbackloadclass-method"></a><span data-ttu-id="953e8-102">ICorDebugManagedCallback::LoadClass – metoda</span><span class="sxs-lookup"><span data-stu-id="953e8-102">ICorDebugManagedCallback::LoadClass Method</span></span>
<span data-ttu-id="953e8-103">Načtení třídy upozorní ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="953e8-103">Notifies the debugger that a class has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="953e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="953e8-104">Syntax</span></span>  
  
```  
HRESULT LoadClass (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugClass     *c  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="953e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="953e8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="953e8-106">[v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace, do kterého se načetl třídy.</span><span class="sxs-lookup"><span data-stu-id="953e8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the class has been loaded.</span></span>  
  
 `c`  
 <span data-ttu-id="953e8-107">[v] Ukazatel na ICorDebugClass objekt, který představuje třídu.</span><span class="sxs-lookup"><span data-stu-id="953e8-107">[in] A pointer to an ICorDebugClass object that represents the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="953e8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="953e8-108">Remarks</span></span>  
 <span data-ttu-id="953e8-109">Tato zpětného volání dojde pouze v případě, že třída načítání je povoleno modul, který obsahuje třídu.</span><span class="sxs-lookup"><span data-stu-id="953e8-109">This callback occurs only if class loading has been enabled for the module that contains the class.</span></span> <span data-ttu-id="953e8-110">Načtení třídy je vždy povolena pro dynamické moduly.</span><span class="sxs-lookup"><span data-stu-id="953e8-110">Class loading is always enabled for dynamic modules.</span></span>  
  
 <span data-ttu-id="953e8-111">`LoadClass` Zpětné volání poskytuje příslušnou dobu pro vazbu na nově vygenerované třídy v dynamických modulech zarážky.</span><span class="sxs-lookup"><span data-stu-id="953e8-111">The `LoadClass` callback provides an appropriate time to bind breakpoints to newly generated classes in dynamic modules.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="953e8-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="953e8-112">Requirements</span></span>  
 <span data-ttu-id="953e8-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="953e8-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="953e8-114">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="953e8-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="953e8-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="953e8-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="953e8-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="953e8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="953e8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="953e8-117">See Also</span></span>  
 [<span data-ttu-id="953e8-118">Unloadclass – metoda</span><span class="sxs-lookup"><span data-stu-id="953e8-118">UnloadClass Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadclass-method.md)  
 [<span data-ttu-id="953e8-119">ICorDebugManagedCallback – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="953e8-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
