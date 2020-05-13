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
ms.openlocfilehash: 78b87b5c566b0d760a205757430123665fb2fcd3
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213709"
---
# <a name="icordebugmanagedcallbackeditandcontinueremap-method"></a><span data-ttu-id="0cb10-102">ICorDebugManagedCallback::EditAndContinueRemap – metoda</span><span class="sxs-lookup"><span data-stu-id="0cb10-102">ICorDebugManagedCallback::EditAndContinueRemap Method</span></span>
<span data-ttu-id="0cb10-103">Tato metoda je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="0cb10-103">This method has been deprecated.</span></span> <span data-ttu-id="0cb10-104">Oznamuje ladicímu programu, že byla do integrovaného vývojového prostředí (IDE) odeslána událost přemapování.</span><span class="sxs-lookup"><span data-stu-id="0cb10-104">It notifies the debugger that a remap event has been sent to the integrated development environment (IDE).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0cb10-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0cb10-105">Syntax</span></span>  
  
```cpp  
HRESULT EditAndContinueRemap (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread *pThread,  
    [in] ICorDebugFunction *pFunction,  
    [in] BOOL fAccurate  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="0cb10-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0cb10-106">Remarks</span></span>  
 <span data-ttu-id="0cb10-107">`EditAndContinueRemap`Metoda je volána, když došlo k pokusu o spuštění kódu ve staré verzi aktualizované funkce.</span><span class="sxs-lookup"><span data-stu-id="0cb10-107">The `EditAndContinueRemap` method is called when the execution of the code in an old version of an updated function has been attempted.</span></span> <span data-ttu-id="0cb10-108">Modul CLR (Common Language Runtime) volá `EditAndContinueRemap` metodu pro odeslání události přemapování na rozhraní IDE.</span><span class="sxs-lookup"><span data-stu-id="0cb10-108">The common language runtime calls the `EditAndContinueRemap` method to send a remap event to the IDE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0cb10-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0cb10-109">Requirements</span></span>  
 <span data-ttu-id="0cb10-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0cb10-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0cb10-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0cb10-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0cb10-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0cb10-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0cb10-113">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0cb10-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cb10-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="0cb10-114">See also</span></span>

- [<span data-ttu-id="0cb10-115">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cb10-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
