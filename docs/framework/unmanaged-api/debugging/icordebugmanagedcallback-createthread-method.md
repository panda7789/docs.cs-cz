---
title: ICorDebugManagedCallback::CreateThread – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.CreateThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::CreateThread method
helpviewer_keywords:
- ICorDebugManagedCallback::CreateThread method [.NET Framework debugging]
- CreateThread method [.NET Framework debugging]
ms.assetid: 6b961728-21c4-4e8d-ae81-197458be62f4
topic_type:
- apiref
ms.openlocfilehash: 5fa3bafd35912a7729833896f7e6f0bb2ff9b121
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212383"
---
# <a name="icordebugmanagedcallbackcreatethread-method"></a><span data-ttu-id="f63d8-102">ICorDebugManagedCallback::CreateThread – metoda</span><span class="sxs-lookup"><span data-stu-id="f63d8-102">ICorDebugManagedCallback::CreateThread Method</span></span>
<span data-ttu-id="f63d8-103">Oznamuje ladicímu programu, že vlákno zahájilo provádění spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="f63d8-103">Notifies the debugger that a thread has started executing managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f63d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f63d8-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f63d8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f63d8-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="f63d8-106">pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno.</span><span class="sxs-lookup"><span data-stu-id="f63d8-106">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="f63d8-107">pro Ukazatel na objekt ICorDebugThread, který představuje vlákno.</span><span class="sxs-lookup"><span data-stu-id="f63d8-107">[in] A pointer to an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f63d8-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f63d8-108">Remarks</span></span>  
 <span data-ttu-id="f63d8-109">Vlákno bude umístěno v první instrukci spravovaného kódu, který má být proveden.</span><span class="sxs-lookup"><span data-stu-id="f63d8-109">The thread will be positioned at the first managed code instruction to be executed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f63d8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f63d8-110">Requirements</span></span>  
 <span data-ttu-id="f63d8-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f63d8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f63d8-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f63d8-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f63d8-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f63d8-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f63d8-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f63d8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f63d8-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="f63d8-115">See also</span></span>

- [<span data-ttu-id="f63d8-116">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f63d8-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
