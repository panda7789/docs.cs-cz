---
title: "ICorDebug::CanLaunchOrAttach – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebug.CanLaunchOrAttach
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5bd657c73dfaf7643405b4b657edeffa6e33cd68
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="a6046-102">ICorDebug::CanLaunchOrAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="a6046-102">ICorDebug::CanLaunchOrAttach Method</span></span>
<span data-ttu-id="a6046-103">Vrátí hodnotu určující, zda je možné v rámci aktuální konfiguraci počítače a prostředí runtime spouštění nového procesu nebo připojení k zadané stávajícího procesu HRESULT.</span><span class="sxs-lookup"><span data-stu-id="a6046-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6046-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a6046-104">Syntax</span></span>  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6046-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6046-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="a6046-106">[v] ID existujícího procesu.</span><span class="sxs-lookup"><span data-stu-id="a6046-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="a6046-107">[v] Předejte `true` Pokud plánujete spouštět s povoleným laděním Win32, nebo se připojit s laděním Win32 povoleno; jinak hodnota předejte `false`.</span><span class="sxs-lookup"><span data-stu-id="a6046-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6046-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a6046-108">Return Value</span></span>  
 <span data-ttu-id="a6046-109">S_OK Pokud ladění služeb zjistit nový proces spouštění nebo připojení k dané proces je možné, zadané informace o aktuální konfiguraci počítače a prostředí runtime.</span><span class="sxs-lookup"><span data-stu-id="a6046-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="a6046-110">Možné hodnoty HRESULT jsou:</span><span class="sxs-lookup"><span data-stu-id="a6046-110">Possible HRESULT values are:</span></span>  
  
-   <span data-ttu-id="a6046-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a6046-111">S_OK</span></span>  
  
-   <span data-ttu-id="a6046-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="a6046-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
-   <span data-ttu-id="a6046-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="a6046-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
-   <span data-ttu-id="a6046-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="a6046-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6046-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a6046-115">Remarks</span></span>  
 <span data-ttu-id="a6046-116">Tato metoda je pouze informační.</span><span class="sxs-lookup"><span data-stu-id="a6046-116">This method is purely informational.</span></span> <span data-ttu-id="a6046-117">Rozhraní neukončí nezabráníte ve spouštění nebo připojení k procesu, bez ohledu na hodnotu vrácený `CanLaunchOrAttach`.</span><span class="sxs-lookup"><span data-stu-id="a6046-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="a6046-118">Pokud budete chtít spustit s povoleným laděním Win32 nebo připojení s povoleným laděním Win32, předat `true` pro `win32DebuggingEnabled`.</span><span class="sxs-lookup"><span data-stu-id="a6046-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="a6046-119">Hodnota HRESULT vrácený `CanLaunchOrAttach` může lišit, pokud použijete tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="a6046-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6046-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a6046-120">Requirements</span></span>  
 <span data-ttu-id="a6046-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6046-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6046-122">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6046-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6046-123">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6046-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6046-124">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6046-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6046-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="a6046-125">See Also</span></span>  
 [<span data-ttu-id="a6046-126">ICorDebug – rozhraní rozhraní</span><span class="sxs-lookup"><span data-stu-id="a6046-126">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
