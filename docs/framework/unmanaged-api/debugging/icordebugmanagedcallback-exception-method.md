---
title: ICorDebugManagedCallback::Exception – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Exception
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Exception
helpviewer_keywords:
- Exception method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::Exception method [.NET Framework debugging]
ms.assetid: ab18a509-dff3-4930-b585-bd15e0414176
topic_type:
- apiref
ms.openlocfilehash: af2dab65629093401219f1016538b912bee4d067
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130816"
---
# <a name="icordebugmanagedcallbackexception-method"></a><span data-ttu-id="e0136-102">ICorDebugManagedCallback::Exception – metoda</span><span class="sxs-lookup"><span data-stu-id="e0136-102">ICorDebugManagedCallback::Exception Method</span></span>
<span data-ttu-id="e0136-103">Oznamuje ladicímu programu, že byla vyvolána výjimka ze spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="e0136-103">Notifies the debugger that an exception has been thrown from managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0136-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0136-104">Syntax</span></span>  
  
```cpp  
HRESULT Exception (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] BOOL                unhandled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0136-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0136-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="e0136-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace, ve které byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e0136-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain in which the exception was thrown.</span></span>  
  
 `pThread`  
 <span data-ttu-id="e0136-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém byla vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="e0136-107">[in] A pointer to an ICorDebugThread object that represents the thread in which the exception was thrown.</span></span>  
  
 `unhandled`  
 <span data-ttu-id="e0136-108">pro Pokud je tato hodnota `false`, výjimka ještě nebyla zpracována aplikací; v opačném případě je výjimka neošetřená a ukončí proces.</span><span class="sxs-lookup"><span data-stu-id="e0136-108">[in] If this value is `false`, the exception has not yet been processed by the application; otherwise, the exception is unhandled and will terminate the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0136-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0136-109">Remarks</span></span>  
 <span data-ttu-id="e0136-110">Konkrétní výjimku lze načíst z objektu vlákna.</span><span class="sxs-lookup"><span data-stu-id="e0136-110">The specific exception can be retrieved from the thread object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0136-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e0136-111">Requirements</span></span>  
 <span data-ttu-id="e0136-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0136-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0136-113">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e0136-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0136-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e0136-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0136-115">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0136-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0136-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e0136-116">See also</span></span>

- [<span data-ttu-id="e0136-117">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e0136-117">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
