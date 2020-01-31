---
title: ICorDebugManagedCallback::ExitThread – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: fa649fd1983a76c71d400ad3e6965ac0794da6ed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76781599"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="22bc4-102">ICorDebugManagedCallback::ExitThread – metoda</span><span class="sxs-lookup"><span data-stu-id="22bc4-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="22bc4-103">Oznamuje ladicímu programu, že bylo ukončeno vlákno, které spustilo spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="22bc4-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22bc4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22bc4-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="22bc4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="22bc4-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="22bc4-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="22bc4-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="22bc4-107">pro Ukazatel na objekt ICorDebugThread, který představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="22bc4-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22bc4-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22bc4-108">Remarks</span></span>  
 <span data-ttu-id="22bc4-109">Po vyvolání zpětného volání `ExitThread` se vlákno již nebude zobrazovat v výčtech vláken.</span><span class="sxs-lookup"><span data-stu-id="22bc4-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="22bc4-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="22bc4-110">Requirements</span></span>  
 <span data-ttu-id="22bc4-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="22bc4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="22bc4-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="22bc4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="22bc4-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="22bc4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="22bc4-114">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="22bc4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22bc4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22bc4-115">See also</span></span>

- [<span data-ttu-id="22bc4-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="22bc4-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
