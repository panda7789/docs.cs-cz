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
ms.openlocfilehash: e1e97b8df2ad81f91cd7250afbe4c5cc544ca6be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702246"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="3d1dd-102">ICorDebugManagedCallback::EditAndContinueRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="3d1dd-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="3d1dd-103">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-103">This method has been deprecated.</span></span> <span data-ttu-id="3d1dd-104">Upozorní ladicího programu, že přemapování události odeslala do integrovaného vývojového prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="3d1dd-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d1dd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d1dd-105">Syntax</span></span>  
  
```  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="3d1dd-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d1dd-106">Remarks</span></span>  
 <span data-ttu-id="3d1dd-107">`EditAndContinueRemap` Metoda se volá, když byl pokus o spuštění kódu v původní verzi aktualizované funkce.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="3d1dd-108">Common language runtime zavolá `EditAndContinueRemap` metodu pro odeslání události přemapování do integrovaného vývojového prostředí.</span><span class="sxs-lookup"><span data-stu-id="3d1dd-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d1dd-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d1dd-109">Requirements</span></span>  
 <span data-ttu-id="3d1dd-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d1dd-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d1dd-111">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d1dd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d1dd-112">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d1dd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d1dd-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d1dd-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d1dd-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d1dd-114">See also</span></span>
- [<span data-ttu-id="3d1dd-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d1dd-115">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
