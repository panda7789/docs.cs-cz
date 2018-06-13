---
title: ICorDebugManagedCallback::EditAndContinueRemap – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EditAndContinueRemap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EditAndContinueRemap
helpviewer_keywords:
- EditAndContinueRemap method [.NET Framework debugging]
- ICorDebugManagedCallback::EditAndContinueRemap method [.NET Framework debugging]
ms.assetid: 24a8fcce-317e-48ff-aefc-d86123ada935
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e8aa71a79bee45d5a8e1f3448c781e6ba1ec605
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414135"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="af240-102">ICorDebugManagedCallback::EditAndContinueRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="af240-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="af240-103">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="af240-103">This method has been deprecated.</span></span> <span data-ttu-id="af240-104">Upozorní ladicího programu, přemapování událostí byl odeslán do integrované vývojové prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="af240-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af240-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af240-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="af240-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af240-106">Remarks</span></span>  
 <span data-ttu-id="af240-107">`EditAndContinueRemap` Metoda je volána, když má došlo k pokusu o spuštění kódu v původní verzi aktualizované funkce.</span><span class="sxs-lookup"><span data-stu-id="af240-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="af240-108">Běžné volání modulu runtime jazyka `EditAndContinueRemap` metodu pro odeslání události přemapování do prostředí IDE.</span><span class="sxs-lookup"><span data-stu-id="af240-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af240-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af240-109">Requirements</span></span>  
 <span data-ttu-id="af240-110">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af240-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af240-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="af240-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="af240-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af240-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af240-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af240-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af240-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="af240-114">See Also</span></span>  
 [<span data-ttu-id="af240-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="af240-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
