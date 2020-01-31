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
ms.openlocfilehash: 9cb956c0262fdcdb5971d049ea7b057aa4d952c0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781907"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="7b507-102">ICorDebugManagedCallback::EditAndContinueRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="7b507-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="7b507-103">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="7b507-103">This method has been deprecated.</span></span> <span data-ttu-id="7b507-104">Oznamuje ladicímu programu, že byla do integrovaného vývojového prostředí (IDE) odeslána událost přemapování.</span><span class="sxs-lookup"><span data-stu-id="7b507-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b507-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b507-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="7b507-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b507-106">Remarks</span></span>  
 <span data-ttu-id="7b507-107">Metoda `EditAndContinueRemap` je volána, když došlo k pokusu o spuštění kódu ve staré verzi aktualizované funkce.</span><span class="sxs-lookup"><span data-stu-id="7b507-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="7b507-108">Modul CLR (Common Language Runtime) volá metodu `EditAndContinueRemap` k odeslání události přemapování na rozhraní IDE.</span><span class="sxs-lookup"><span data-stu-id="7b507-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b507-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7b507-109">Requirements</span></span>  
 <span data-ttu-id="7b507-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b507-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b507-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7b507-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b507-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7b507-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b507-113">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b507-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b507-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b507-114">See also</span></span>

- [<span data-ttu-id="7b507-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7b507-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
