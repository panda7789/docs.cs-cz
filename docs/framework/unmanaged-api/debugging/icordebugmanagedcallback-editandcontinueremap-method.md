---
title: "ICorDebugManagedCallback::EditAndContinueRemap – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback.EditAndContinueRemap
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 90c22b697677ec493b8093117af0a9d1a86268ea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="b793f-102">ICorDebugManagedCallback::EditAndContinueRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="b793f-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="b793f-103">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b793f-103">This method has been deprecated.</span></span> <span data-ttu-id="b793f-104">Upozorní ladicího programu, přemapování událostí byl odeslán do integrované vývojové prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="b793f-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b793f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b793f-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="b793f-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b793f-106">Remarks</span></span>  
 <span data-ttu-id="b793f-107">`EditAndContinueRemap` Metoda je volána, když má došlo k pokusu o spuštění kódu v původní verzi aktualizované funkce.</span><span class="sxs-lookup"><span data-stu-id="b793f-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="b793f-108">Běžné volání modulu runtime jazyka `EditAndContinueRemap` metodu pro odeslání události přemapování do prostředí IDE.</span><span class="sxs-lookup"><span data-stu-id="b793f-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b793f-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b793f-109">Requirements</span></span>  
 <span data-ttu-id="b793f-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b793f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b793f-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b793f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b793f-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b793f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b793f-113">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b793f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b793f-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b793f-114">See Also</span></span>  
 [<span data-ttu-id="b793f-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b793f-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
