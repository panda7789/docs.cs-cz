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
ms.openlocfilehash: 7a49bd6626518179c9b5ef008fca28d304537cc8
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205266"
---
# <a name="icordebugmanagedcallbackexitprocess-method"></a><span data-ttu-id="720b3-102">ICorDebugManagedCallback::ExitProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="720b3-102">ICorDebugManagedCallback::ExitProcess Method</span></span>
<span data-ttu-id="720b3-103">Oznamuje ladicímu programu, že došlo k ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="720b3-103">Notifies the debugger that a process has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="720b3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="720b3-104">Syntax</span></span>  
  
```cpp  
HRESULT ExitProcess (  
    [in] ICorDebugProcess *pProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="720b3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="720b3-105">Parameters</span></span>  
 `pProcess`  
 <span data-ttu-id="720b3-106">pro Ukazatel na objekt ICorDebugProcess, který představuje proces.</span><span class="sxs-lookup"><span data-stu-id="720b3-106">[in] A pointer to an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="720b3-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="720b3-107">Remarks</span></span>  
 <span data-ttu-id="720b3-108">V události nemůžete pokračovat `ExitProcess` .</span><span class="sxs-lookup"><span data-stu-id="720b3-108">You cannot continue from an `ExitProcess` event.</span></span> <span data-ttu-id="720b3-109">Tato událost může být vyvolána asynchronně s ostatními událostmi, pokud se zdá, že se proces zastaví.</span><span class="sxs-lookup"><span data-stu-id="720b3-109">This event may fire asynchronously to other events while the process appears to be stopped.</span></span> <span data-ttu-id="720b3-110">Tato situace může nastat, pokud se proces ukončí během zastavení, obvykle kvůli nějakému externímu vynutitmu.</span><span class="sxs-lookup"><span data-stu-id="720b3-110">This can occur if the process terminates while stopped, usually due to some external force.</span></span>  
  
 <span data-ttu-id="720b3-111">Pokud již modul CLR (Common Language Runtime) odesílá spravované zpětné volání, bude tato událost zpožděna až po vrácení zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="720b3-111">If the common language runtime (CLR) is already dispatching a managed callback, this event will be delayed until after that callback has returned.</span></span>  
  
 <span data-ttu-id="720b3-112">`ExitProcess`Událost je jediná událost ukončení/uvolnění, která zaručuje, že se má volat při vypnutí.</span><span class="sxs-lookup"><span data-stu-id="720b3-112">The `ExitProcess` event is the only exit/unload event that is guaranteed to get called on shutdown.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="720b3-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="720b3-113">Requirements</span></span>  
 <span data-ttu-id="720b3-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="720b3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="720b3-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="720b3-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="720b3-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="720b3-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="720b3-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="720b3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="720b3-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="720b3-118">See also</span></span>

- [<span data-ttu-id="720b3-119">ICorDebugManagedCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="720b3-119">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
