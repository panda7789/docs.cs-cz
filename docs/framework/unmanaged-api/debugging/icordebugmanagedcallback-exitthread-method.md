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
ms.openlocfilehash: 3ba1280aa44a9445f6af7fe9a8769b7cdc7edb66
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205250"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="c9847-102">ICorDebugManagedCallback::ExitThread – metoda</span><span class="sxs-lookup"><span data-stu-id="c9847-102">ICorDebugManagedCallback::ExitThread Method</span></span>
<span data-ttu-id="c9847-103">Oznamuje ladicímu programu, že bylo ukončeno vlákno, které spustilo spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="c9847-103">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9847-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9847-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9847-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c9847-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="c9847-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="c9847-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="c9847-107">pro Ukazatel na objekt ICorDebugThread, který představuje spravované vlákno.</span><span class="sxs-lookup"><span data-stu-id="c9847-107">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9847-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9847-108">Remarks</span></span>  
 <span data-ttu-id="c9847-109">Po `ExitThread` vyvolání zpětného volání se vlákno již nebude zobrazovat v výčtech vláken.</span><span class="sxs-lookup"><span data-stu-id="c9847-109">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9847-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9847-110">Requirements</span></span>  
 <span data-ttu-id="c9847-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9847-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9847-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c9847-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9847-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c9847-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9847-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9847-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9847-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9847-115">See also</span></span>

- [<span data-ttu-id="c9847-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9847-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
