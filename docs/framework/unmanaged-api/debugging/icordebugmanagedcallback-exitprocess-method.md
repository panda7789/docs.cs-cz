---
title: ICorDebugManagedCallback::ExitProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitProcess
helpviewer_keywords:
- ExitProcess method, ICorDebugManagedCallback interface [.NET Framework debugging]
- ICorDebugManagedCallback::ExitProcess method [.NET Framework debugging]
ms.assetid: 63a7d47a-0d54-4e29-9767-9f09feaa38b7
topic_type:
- apiref
ms.openlocfilehash: 4518637eb47acf416a02c045f8ca6f8a90167277
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130779"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="d825d-102">ICorDebugManagedCallback::ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="d825d-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="d825d-103">Oznamuje ladicímu programu, že došlo k ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="d825d-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d825d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d825d-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d825d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d825d-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="d825d-106">pro Ukazatel na objekt ICorDebugProcess, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="d825d-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d825d-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d825d-107">Remarks</span></span>  
 <span data-ttu-id="d825d-108">Nemůžete pokračovat z `ExitProcess` události.</span><span class="sxs-lookup"><span data-stu-id="d825d-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="d825d-109">Tato událost může být vyvolána asynchronně s ostatními událostmi, pokud se zdá, že se proces zastaví.</span><span class="sxs-lookup"><span data-stu-id="d825d-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="d825d-110">Tato situace může nastat, pokud se proces ukončí během zastavení, obvykle kvůli nějakému externímu vynutitmu.</span><span class="sxs-lookup"><span data-stu-id="d825d-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="d825d-111">Pokud již modul CLR (Common Language Runtime) odesílá spravované zpětné volání, bude tato událost zpožděna až po vrácení zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d825d-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="d825d-112">Událost `ExitProcess` je jediná událost ukončení/uvolnění, která zaručuje, že se má volat při vypnutí.</span><span class="sxs-lookup"><span data-stu-id="d825d-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d825d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d825d-113">Requirements</span></span>  
 <span data-ttu-id="d825d-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d825d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d825d-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d825d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d825d-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d825d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d825d-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d825d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d825d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d825d-118">See also</span></span>

- [<span data-ttu-id="d825d-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d825d-119">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
