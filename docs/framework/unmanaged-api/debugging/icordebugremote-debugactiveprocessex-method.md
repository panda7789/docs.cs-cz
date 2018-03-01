---
title: "ICorDebugRemote::DebugActiveProcessEx – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 09bc98b477231eb1466300451585f4569aff222c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="a4d43-102">ICorDebugRemote::DebugActiveProcessEx – metoda</span><span class="sxs-lookup"><span data-stu-id="a4d43-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>
<span data-ttu-id="a4d43-103">Spustí proces ve vzdáleném počítači v rámci ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="a4d43-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d43-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4d43-104">Syntax</span></span>  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a4d43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a4d43-105">Parameters</span></span>  
 `pRemoteTarget`  
 <span data-ttu-id="a4d43-106">[v] Ukazatel na [ICorDebugRemoteTarget rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span><span class="sxs-lookup"><span data-stu-id="a4d43-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="a4d43-107">Tento parametr slouží k určení počítače, na kterém je spuštěn proces.</span><span class="sxs-lookup"><span data-stu-id="a4d43-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="a4d43-108">[v] ID procesu, ke kterému má být připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="a4d43-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="a4d43-109">[v] `true` Pokud ladicí program by měl chovat jako Win32 ladicí program pro proces a odesílání nespravované zpětná volání; jinak `false`.</span><span class="sxs-lookup"><span data-stu-id="a4d43-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a4d43-110">[out] Ukazatel na adresu "ICorDebugProcess" objekt, který představuje proces, který byl připojen ladicí program.</span><span class="sxs-lookup"><span data-stu-id="a4d43-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4d43-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a4d43-111">Return Value</span></span>  
 <span data-ttu-id="a4d43-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="a4d43-112">S_OK</span></span>  
 <span data-ttu-id="a4d43-113">Pro proces ve vzdáleném počítači se úspěšně připojil.</span><span class="sxs-lookup"><span data-stu-id="a4d43-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="a4d43-114">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="a4d43-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="a4d43-115">Nelze připojit k procesu ve vzdáleném počítači.</span><span class="sxs-lookup"><span data-stu-id="a4d43-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a4d43-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a4d43-116">Remarks</span></span>  
 <span data-ttu-id="a4d43-117">Ladění ve smíšeném režimu není podporována v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="a4d43-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4d43-118">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4d43-118">Requirements</span></span>  
 <span data-ttu-id="a4d43-119">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a4d43-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4d43-120">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4d43-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4d43-121">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4d43-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4d43-122">**Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="a4d43-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d43-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4d43-123">See Also</span></span>  
 [<span data-ttu-id="a4d43-124">ICorDebugRemote – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4d43-124">ICorDebugRemote Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 [<span data-ttu-id="a4d43-125">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a4d43-125">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="a4d43-126">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="a4d43-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
