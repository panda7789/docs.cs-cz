---
title: ICorDebugThread2::InterceptCurrentException – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: c25a03ef5bbba18da31787c911f83a1348badd4b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791455"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a><span data-ttu-id="6f0b8-102">ICorDebugThread2::InterceptCurrentException – metoda</span><span class="sxs-lookup"><span data-stu-id="6f0b8-102">ICorDebugThread2::InterceptCurrentException Method</span></span>
<span data-ttu-id="6f0b8-103">Umožňuje ladicímu programu zachytit aktuální výjimku v tomto vlákně.</span><span class="sxs-lookup"><span data-stu-id="6f0b8-103">Allows a debugger to intercept the current exception on this thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f0b8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f0b8-104">Syntax</span></span>  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f0b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6f0b8-105">Parameters</span></span>  
 `pFrame`  
 <span data-ttu-id="6f0b8-106">pro Ukazatel na ICorDebugFrame, který představuje aktivní rámec zásobníku.</span><span class="sxs-lookup"><span data-stu-id="6f0b8-106">[in] A pointer to an ICorDebugFrame that represents the active stack frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f0b8-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6f0b8-107">Remarks</span></span>  
 <span data-ttu-id="6f0b8-108">Metodu `InterceptCurrentException` lze volat mezi zpětným voláním výjimky ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) nebo [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) a přidruženým voláním [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).</span><span class="sxs-lookup"><span data-stu-id="6f0b8-108">The `InterceptCurrentException` method can be called between an exception callback ([ICorDebugManagedCallback::Exception](icordebugmanagedcallback-exception-method.md) or [ICorDebugManagedCallback2::Exception](icordebugmanagedcallback2-exception-method.md)) and the associated call to [ICorDebugController::Continue](icordebugcontroller-continue-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f0b8-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6f0b8-109">Requirements</span></span>  
 <span data-ttu-id="6f0b8-110">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f0b8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f0b8-111">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6f0b8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f0b8-112">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6f0b8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f0b8-113">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f0b8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
