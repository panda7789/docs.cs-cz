---
title: ICorDebugRemote::DebugActiveProcessEx – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: 83cc4eadca7c337c06c5fbf9f0e74306c2b9cb99
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131278"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="74aef-102">ICorDebugRemote::DebugActiveProcessEx – metoda</span><span class="sxs-lookup"><span data-stu-id="74aef-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="74aef-103">Spustí proces na vzdáleném počítači v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="74aef-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74aef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74aef-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74aef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="74aef-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="74aef-106">pro Ukazatel na [rozhraní ICorDebugRemoteTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="74aef-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="74aef-107">Tento parametr slouží k určení počítače, na kterém je spuštěn proces.</span><span class="sxs-lookup"><span data-stu-id="74aef-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="74aef-108">pro ID procesu, ke kterému má být připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="74aef-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="74aef-109">[in] `true`, jestli se má ladicí program chovat jako ladicí program Win32 pro proces a odeslání nespravovaných zpětných volání; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="74aef-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="74aef-110">mimo Ukazatel na adresu objektu "ICorDebugProcess", který představuje proces, ke kterému byl připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="74aef-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74aef-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="74aef-111">Return Value</span></span>  
 <span data-ttu-id="74aef-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="74aef-112">S_OK</span></span>  
 <span data-ttu-id="74aef-113">Úspěšně připojeno k procesu na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="74aef-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="74aef-114">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="74aef-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="74aef-115">Nelze se připojit k procesu na vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="74aef-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74aef-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74aef-116">Remarks</span></span>  
 <span data-ttu-id="74aef-117">Ladění ve smíšeném režimu není v Silverlightu podporované.</span><span class="sxs-lookup"><span data-stu-id="74aef-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74aef-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74aef-118">Requirements</span></span>  
 <span data-ttu-id="74aef-119">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74aef-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74aef-120">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74aef-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74aef-121">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="74aef-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74aef-122">**Verze .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="74aef-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74aef-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74aef-123">See also</span></span>

- [<span data-ttu-id="74aef-124">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74aef-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="74aef-125">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74aef-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="74aef-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="74aef-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
