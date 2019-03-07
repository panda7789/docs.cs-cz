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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eba0ff6e545a5da5d7733a157b73ddd66e717de9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57477111"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="9fe9f-102">ICorDebugRemote::DebugActiveProcessEx – metoda</span><span class="sxs-lookup"><span data-stu-id="9fe9f-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="9fe9f-103">Spustí nějaký proces ve vzdáleném počítači v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="9fe9f-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fe9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fe9f-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fe9f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9fe9f-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="9fe9f-106">[in] Ukazatel [icordebugremotetarget – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="9fe9f-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="9fe9f-107">Tento parametr slouží k určení počítače, na kterém je proces spuštěn.</span><span class="sxs-lookup"><span data-stu-id="9fe9f-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="9fe9f-108">[in] ID procesu, ke kterému je ladicí program připojit.</span><span class="sxs-lookup"><span data-stu-id="9fe9f-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="9fe9f-109">[in] `true` Pokud ladicí program by měl chovat jako ladicí program systému Win32 pro proces a odeslání nespravované zpětná volání; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="9fe9f-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="9fe9f-110">[out] Ukazatel na adresu "ICorDebugProcess" objekt, který představuje proces, ke kterému je připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="9fe9f-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fe9f-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="9fe9f-111">Return Value</span></span>  
 <span data-ttu-id="9fe9f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9fe9f-112">S_OK</span></span>  
 <span data-ttu-id="9fe9f-113">Úspěšně připojeno k procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="9fe9f-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="9fe9f-114">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="9fe9f-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="9fe9f-115">Nelze se připojit k procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="9fe9f-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9fe9f-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fe9f-116">Remarks</span></span>  
 <span data-ttu-id="9fe9f-117">Ladění ve smíšeném režimu není v Silverlightu podporovaný.</span><span class="sxs-lookup"><span data-stu-id="9fe9f-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fe9f-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9fe9f-118">Requirements</span></span>  
 <span data-ttu-id="9fe9f-119">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fe9f-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fe9f-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fe9f-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fe9f-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fe9f-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fe9f-122">**Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="9fe9f-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fe9f-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9fe9f-123">See also</span></span>
- [<span data-ttu-id="9fe9f-124">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fe9f-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [<span data-ttu-id="9fe9f-125">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9fe9f-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="9fe9f-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9fe9f-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
